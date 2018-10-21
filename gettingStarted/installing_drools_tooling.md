# Installing Drools Tooling

To be able to work with drools, we need :  
1\) Java Virtual machine version 8  
2\) Eclipse IDE  
3\) download drools runtime and tools

## Install Java Virtual Machine

Drools works with either Oracle Java machine or OpenJDK. With the drools version we have, we can have Java version 7 or 8.

## Install Eclipse IDE

After installing Java, we can install [eclipse](http://www.eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/mars2).

## Download drools tooling

To be able to use drools in eclipse, we need to download the [Drools and jbpm Tools](http://download.jboss.org/drools/release/6.5.0.Final/droolsjbpm-integration-distribution-6.5.0.Final.zip).

You have to unzip the file. In the directory droolsjbpm-tools-distribution-6.5.0.Final/binaries/org.drools.updatesite/ is the update site from where you have to install new Software.

## Create your first project

Go to File/New/Other  
![](../overview/images/CreateProject_New.jpeg)  
then push on next.  
![](drools/CreateProject_SelectContent.jpeg)  
Select the middle button and push next.  
![](drools/CreateProject_enterName.jpeg)  
Enter "FirstProject" as a project name and keep only the "Add a sample Helloworld rule file to this project". The generated project should look like this:

![](drools/CreateNewProject_treeview.jpeg)

If you click with the right mouse button on DroolsTest class and run as "Java Program", the following should be displayed on the console view

![](drools/CreateProject_ConsoleOutput.jpeg)  
All is well installed.

