# Extending the workbench

In the Guvnor 5.x, a rest interface exists that offered CRUD services on rule asset : creation, update, lists, etc..
In the 6.x version, this APi does not exist anymore  as it is replaced by accessing the git repository where you can do the same.
Now imagine that you have a user interface of an application that proposes to the end user to create a business rule. But in reality behind it creates many different drools rules : guided rules, templates etc.. 
There are two approaches to continue to run the same service to the end user : 
1\) We create the same rest services on the workbench. This will have no impact for the end user
2\) We create a new addon the implements a new user interface in the workbench.

The second approach looks very nice and I can voices telling this is the solution.
Unfortunately, end user do not like to change their habits !

So as a first approach, we shall write a plugin that implements new rest interface very near to the Guvnor 5.x API.

the source code of this project is [here](https://github.com/chtiJBUG/drools-onboarding/tree/master/drools-framework-kie-wb-parent).

## Testing the rest interface

Let us first look how the rest interface is working.

Before explaining how to build such a component, here are a few tests to explain how it works. We are using the firefox extension[ rest client](https://addons.mozilla.org/en-US/firefox/addon/restclient/).

Here to get the list of project\(package\) in a repository and a organizational unit : here "demo" and "onboarding-nautic-project" repossitory.

![](/assets/action02.png)

Here to get the list of assets of a project :

![](/assets/action03.png)

Here to have the content of a rule asset \(BirthdayReduction\)

the url is :

http:\/\/localhost:8080\/kie-wb\/rest\/packages\/demo\/onboarding-nautic-project\/swimmingpool\/assets\/BirthdayReduction.rdrl\/source

## Implementing the plugin

on the github repository of the project, the structure of the maven project is like this :

| Maven project | Content |
| :--- | :--- |
| kie-drools-framework-wb-webapp | IThis is a copy od the drools-wb and customized. All names were changed. In the dependency file pom.xml we added the new plugin we are building |
| drools-framework-kie-wb-wars |
|  |  |

