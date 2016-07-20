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

