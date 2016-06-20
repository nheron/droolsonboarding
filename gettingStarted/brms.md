# BRMS Tutorial

In the previous part, we learned the basic of drools concepts. We did that by using a java developer tooling eclipse. 
We can not expect a Business User to use eclipse as a User interface to implement rules.
Since version 5 of drools, there is a dedicated User interface for that was called Guvnor in all versions 5.X, called kie Workbench in versions 6.x till 6.3 and is is now called Business central starting with version 6.4.
Historically, Guvnor is a BRMS=Business Rule Management System. It allowed to handle all lifecyle of a rule : 
* CRUD on a rule artifact,
* Advanced Rule Pattern like decision tables,
* RuleFlow/jbpm process definition,
* definition of deployment rules packages, etc..

All was stored in a CMS (Content Management System) Component from the apache fundation called Jackrabbit. The application Guvnor itself was a monolithic application which features was only extensible by calling its rest API.
The user interface was developed using the Google Web Toolkit (GWT) from google to develop the application in java and generate the javascript to run as a native javascript application on the browser.
All jbpm components were separated application like jbpm-console.


## What is Business central ?

In version 6, the guvnor part was completely redesigned  : 

* A new framework based on GWT but with features that helps to build a Modern business application on HTML5 : [Errai](http://erraiframework.org/) 
* a new framework was defined to define plugins to add new features : [Uberfire](http://www.uberfireframework.org/)
* Use of standard build system widely used in the java ecosystem : [Apache Maven](https://maven.apache.org/)
* Use of a file base repository versus the CMS used before : [git](https://git-scm.com/)
We will explain all this in next part.

There are now two flavors of business central : the BRMS (Business Rule Management System)  and the BPMS (Business Process Management System). 

The BPMS  contains the BRMS with all jbpm specific components : 
* Form Modeler to develop specific Human task User Interfaces
* Process instance and task management : to run the processes from within the workbench and act on human tasks.
We will see during this tutorial the BRMS part.

The drools core part itself now implements a new algorithm : PHREAK algorith (see [5.4 part of documentation](http://docs.jboss.org/drools/release/6.3.0.Final/drools-docs/html/ch05.html#PHREAK)). 

Before starting the tutorial, we shall go through a few concepts that will help to understand how to use and integrate the BRMS in a real project.


## How version 5.x BRMS was working and used in a project.


As shown in the next picture, the steps when using version 5 were the following : 
* The java developer produces the pojo model (working with the business analyst)
* The java archive (jar) shall be uploaded to the Guvnor (BRMS) application. On this pojo mode, the business analyst can write rules.
* The java developer produces the final application that contains the drools runtime and deploys it with the pojo model inside.



![](BRMS/Guvnor5Architecture.jpg)

Now the application and Guvnor must have a synchronized version of the pojo model. 
There a few other points that should be taken care :  
* when upgrading a pojo model version, the two parts must be synchronized. 
* It is not possible to work in parallel. There are workarounds like duplicating the package in guvnor, etc..
* As modern java development is using a maven approach in dependency and configuration management, using Guvnor 5.x that forces to have it speacial build and deploy approach.


Guvnor is a nice tool very useful where most user interface about writing rules was kept in the Business Central (enhanced of course) but all the wrapping was redesigned. 



## How version 6 fits in modern java development process


### Maven versus Manuel Dependency handling




### Git versus subversion (Apache jackrabbit)



## Version 6 tooling 

### Rule design pattern : decision tables,decision tree, guided rules


### Plugin Architecture to build patterns


### Execution server : kie server and Plugin architecture








