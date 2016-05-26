# Organizing rule execution for bigger projects

## Why do we need a Ruleflow ?
When capturing business requirements, most users express the rules by dividing the problem to resolve in steps. As this, it is very convenient to be able to implement it the same way. 
In the drools/jbpm technology, we are going to use a jbpm process by using rule steps, it is then called a rule flow. But in reality, we can mix jbpm/drools together.


## Configure project to become a jbpm project

select the project, right click with the mouse configure/convert to jbpm project

![](drools/lesson4_fig1.png)

## Create your first rule flow

in the src/test/rules create a package lesson4. Right click and create new File and call it ruleflow1.bpmn2 and click the OK button. An error messages appear to say the file is empty but the plugin will create a start event.

![](drools/lesson4_fig3.png)


put two Rule tasks and one End Event.

![](drools/lesson4_fig4.png)






