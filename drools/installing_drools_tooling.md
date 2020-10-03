# Installing Drools Tooling

To be able to work with drools, we need :  
1\) Java Virtual machine version 11  
2\) Eclipse IDE  
3\) download drools runtime and tools

## Install Java Virtual Machine

Drools is working with either Oracle Java machine or OpenJDK. With the drools version we have, we can have java version 11.

## Install Eclipse IDE

After installing java, we can install eclipse for [java developer ](https://www.eclipse.org/downloads/packages/release/2020-09/r/eclipse-ide-java-developers)or for [enterprise java developer](https://www.eclipse.org/downloads/packages/release/2020-09/r/eclipse-ide-enterprise-java-developers) 

## Download drools tooling

To be able to use drools in eclipse, we need to download the [Drools and jbpm Tools](http://download.jboss.org/drools/release/6.5.0.Final/droolsjbpm-integration-distribution-6.5.0.Final.zip).

The update site for eclipse is located [here](https://download.jboss.org/drools/release/7.43.1.Final/org.drools.updatesite/).

## Create you first project

Go to File/New/Other  
![](../.gitbook/assets/CreateProject_New.jpeg)  
then push on next  
![](../.gitbook/assets/CreateProject_SelectContent.jpeg)  
Select the middle button and push next  
![](../.gitbook/assets/CreateProject_enterName.jpeg)  
Enter "FirstProject" as a project name and keep only the "Add a sample Helloworld rule file to this project". the generated project should look like that:

![](../.gitbook/assets/CreateNewProject_treeview.jpeg)

If you do with the right mouse on DroolsTest class and run as "java Program", the following should be displayed on the console view

![](../.gitbook/assets/CreateProject_ConsoleOutput.jpeg)  
All is well installed.

