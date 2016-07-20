# Extending the kie runtime server

The 6.4 version offers a kie-server that can be connected to the kie-wb controler that will in return connect to the kie-server.

From within the  kie-wb, it is possible to create a container in the kie-server for an maven workbench artifact.

## Creating the container

Here we have an example when two kie-servers are connected

![](/action01.png)

We first have to create a container for the swimming pool project we created in the tutorial.

![](/action02.png)

After clicking finish the new container will appear![](/action03.png)After the container are created, we have to start it by clicking the "start" button. They will them appear once there are created.

![](/action04.png)

On the first kie-server

ser![](/action05.png)On the second kie-server

![](/action06.png)

## Testing the container

In the example we are using, we build a plugin for the kie-server.

The source code is [here](https://github.com/chtiJBUG/drools-onboarding/tree/master/drools-framework-kie-server-parent). There are two maven project, one for our kie-server that is a maven assembly project using the defautl kie-server from the community project and the second one is our own service.

We then built a service for the swimming pool that will use our drools service. The source code is [here](https://github.com/chtiJBUG/drools-onboarding/tree/master/drools-framework-examples/swimming-pool-kie-server).

### Creating a drools plugin for the kie-server

To create a kie-server plugin, you need to implement an interface kieServerExtentsion and to create a fiile called org.kie.server.services.api.KieServerExtension in the META-INF\/services directory and in this file you should put the complete class name of you implementation.

Here is the file META-INF\/services\/org.kie.server.services.api.KieServerExtension

```
org.chtijbug.kieserver.services.drools.DroolsFrameworkKieServerExtension
```

And the class you have to write must implemetns the following interface :

```
public interface KieServerExtension {
    boolean isActive();
    void init(KieServerImpl kieServer, KieServerRegistry registry);
    void destroy(KieServerImpl kieServer, KieServerRegistry registry);
    void createContainer(String id, KieContainerInstance kieContainerInstance, Map<String, Object> parameters);
    void disposeContainer(String id, KieContainerInstance kieContainerInstance, Map<String, Object> parameters);
    List<Object> getAppComponents(SupportedTransports type);
    <T> T getAppComponents(Class<T> serviceType);
    String getImplementedCapability();
    List<Object> getServices();
    String getExtensionName();
    Integer getStartOrder();
}
```

This methods will be called by the kie-server.

```
public class DroolsFrameworkKieServerExtension implements KieServerExtension {
    public static final String EXTENSION_NAME = "DroolsFramework";
    private static final Logger logger = LoggerFactory.getLogger(DroolsFrameworkKieServerExtension.class);
    private static final Boolean disabled = Boolean.parseBoolean(System.getProperty(KieServerConstants.KIE_DROOLS_SERVER_EXT_DISABLED, "false"));
    private static final Boolean filterRemoteable = Boolean.parseBoolean(System.getProperty(KieServerConstants.KIE_DROOLS_FILTER_REMOTEABLE_CLASSES, "false"));
    private DroolsFrameworkRulesExecutionService rulesExecutionService;
    private KieServerRegistry registry;
    private List<Object> services = new ArrayList<Object>();
    @Override
    public boolean isActive() {
        return disabled == false;
    }
    @Override
    public void init(KieServerImpl kieServer, KieServerRegistry registry) {
        this.rulesExecutionService = new DroolsFrameworkRulesExecutionService(registry);
        this.registry = registry;
        services.add(rulesExecutionService);
    }
    @Override
    public void destroy(KieServerImpl kieServer, KieServerRegistry registry) {
        // no-op?
    }
    @Override
    public void createContainer(String id, KieContainerInstance kieContainerInstance, Map<String, Object> parameters) {
        // do any other bootstrapping rule service requires
        Set<Class<?>> extraClasses = new HashSet<Class<?>>();
        // create kbases so declared types can be created
        Collection<String> kbases = kieContainerInstance.getKieContainer().getKieBaseNames();
        for (String kbase : kbases) {
            kieContainerInstance.getKieContainer().getKieBase(kbase);
        }
        KieModuleMetaData metaData = (KieModuleMetaData) parameters.get(KieServerConstants.KIE_SERVER_PARAM_MODULE_METADATA);
        Collection<String> packages = metaData.getPackages();
        for (String p : packages) {
            Collection<String> classes = metaData.getClasses(p);
            for (String c : classes) {
                String type = p + "." + c;
                try {
                    logger.debug("Adding {} type into extra jaxb classes set", type);
                    Class<?> clazz = Class.forName(type, true, kieContainerInstance.getKieContainer().getClassLoader());
                    addExtraClass(extraClasses, clazz, filterRemoteable);
                    logger.debug("Added {} type into extra jaxb classes set", type);
                } catch (ClassNotFoundException e) {
                    logger.warn("Unable to create instance of type {} due to {}", type, e.getMessage());
                    logger.debug("Complete stack trace for exception while creating type {}", type, e);
                } catch (Throwable e) {
                    logger.warn("Unexpected error while create instance of type {} due to {}", type, e.getMessage());
                    logger.debug("Complete stack trace for unknown error while creating type {}", type, e);
                }
            }
        }
        kieContainerInstance.addJaxbClasses(extraClasses);
    }
    @Override
    public void disposeContainer(String id, KieContainerInstance kieContainerInstance, Map<String, Object> parameters) {
    }
    @Override
    public List<Object> getAppComponents(SupportedTransports type) {
        ServiceLoader<KieServerApplicationComponentsService> appComponentsServices
                = ServiceLoader.load(KieServerApplicationComponentsService.class);
        List<Object> appComponentsList = new ArrayList<Object>();
        Object[] services = {
                rulesExecutionService,
                registry
        };
        for (KieServerApplicationComponentsService appComponentsService : appComponentsServices) {
            appComponentsList.addAll(appComponentsService.getAppComponents(EXTENSION_NAME, type, services));
        }
        return appComponentsList;
    }
    @Override
    public <T> T getAppComponents(Class<T> serviceType) {
        if (serviceType.isAssignableFrom(rulesExecutionService.getClass())) {
            return (T) rulesExecutionService;
        }
        return null;
    }
    @Override
    public String getImplementedCapability() {
        return KieServerConstants.CAPABILITY_BRM;
    }
    @Override
    public List<Object> getServices() {
        return services;
    }
    @Override
    public String getExtensionName() {
        return EXTENSION_NAME;
    }
    @Override
    public Integer getStartOrder() {
        return 0;
    }
    @Override
    public String toString() {
        return EXTENSION_NAME + " KIE Server extension";
    }
    protected void addExtraClass(Set<Class<?>> extraClasses, Class classToAdd, boolean filtered) {
        if (classToAdd.isInterface()
                || classToAdd.isAnnotation()
                || classToAdd.isLocalClass()
                || classToAdd.isMemberClass()) {
            return;
        }
        if (filtered) {
            boolean jaxbClass = false;
            boolean remoteableClass = false;
            // @XmlRootElement and @XmlType may be used with inheritance
            for (Annotation anno : classToAdd.getAnnotations()) {
                if (XmlRootElement.class.equals(anno.annotationType())) {
                    jaxbClass = true;
                    break;
                }
                if (XmlType.class.equals(anno.annotationType())) {
                    jaxbClass = true;
                    break;
                }
            }
            // @Remotable is not inheritable, and may not be used as such
            for (Annotation anno : classToAdd.getDeclaredAnnotations()) {
                if (Remotable.class.equals(anno.annotationType())) {
                    remoteableClass = true;
                    break;
                }
            }
            if (jaxbClass || remoteableClass) {
                extraClasses.add(classToAdd);
            }
        } else {
            extraClasses.add(classToAdd);
        }
    }
}
```

### Creating a service that uses our plugin

To build a new service in kie-server that will use a plugin we have to implement an interface

```
public interface KieServerApplicationComponentsService {
    Collection<Object> getAppComponents( String extension, SupportedTransports type, Object... services );
}
```

Our implementation looks like this :

```
public class LoyaltyKieServerApplicationComponentsService implements KieServerApplicationComponentsService {
    private static final String OWNER_EXTENSION = "DroolsFramework";
    public Collection<Object> getAppComponents(String extension, SupportedTransports type, Object... services) {
        // skip calls from other than owning extension
        if (!OWNER_EXTENSION.equals(extension)) {
            return Collections.emptyList();
        }
        DroolsFrameworkRulesExecutionService rulesExecutionService = null;
        KieServerRegistry context = null;
        for (Object object : services) {
            if (DroolsFrameworkRulesExecutionService.class.isAssignableFrom(object.getClass())) {
                DroolsFrameworkRulesExecutionService droolsFrameworkRulesExecutionService = (DroolsFrameworkRulesExecutionService) object; 
               context = droolsFrameworkRulesExecutionService.getContext();
                rulesExecutionService = droolsFrameworkRulesExecutionService;
                continue;
            }
        }
        List<Object> components = new ArrayList<Object>(1);
        if (SupportedTransports.REST.equals(type)) {
            components.add(new swimmingpoolResource(rulesExecutionService, context));
        }
        return components;
    }
}
```

ezez

ezez

