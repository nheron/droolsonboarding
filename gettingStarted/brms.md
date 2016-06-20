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

The drools part itself now implements a new algorithm : PHREAK algorith (see [5.4 part of documentation](http://docs.jboss.org/drools/release/6.3.0.Final/drools-docs/html/ch05.html#PHREAK)). 










## How version 5.x BRMS was working 



## How version 6 fits in modern java development process


### Maven versus Manuel Dependency handling


### Git versus subversion (Apache jackrabbit)



## Version 6 tooling 

### Rule design pattern : decision tables,decision tree, guided rules


### Plugin Architecture to build patterns


### Execution server : kie server and Plugin architecture








