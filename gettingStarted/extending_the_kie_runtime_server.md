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

![](/action05.png)On the second kie-server

![](/action06.png)

## Testing the container

In the example we are using, we build a plugin for the kie-server. 

The source code is [here](https://github.com/chtiJBUG/drools-onboarding/tree/master/drools-framework-kie-server-parent). There are two maven project, one for our kie-server that is a maven assembly project using the defautl kie-server from the community project and the second one is our own service.

We then built a service for the swimming pool that will use our drools service. The source code is [here](https://github.com/chtiJBUG/drools-onboarding/tree/master/drools-framework-examples/swimming-pool-kie-server).





