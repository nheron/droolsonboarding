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

the source code of this project is [here](https://github.com/chtiJBUG/drools-onboarding).



