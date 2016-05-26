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


Then select each of the Rule set and set the properties as follows : 



![](drools/lesson4_fig5.png)

![](drools/lesson4_fig6.png)
The workflow should look like that : 
![](drools/lesson4_fig7.png)

Select the workflow in the rear, and in the properties file, change as follows : 

![](drools/lesson4_fig8.png)

Create a new rule file called demo-ruleflow1.drl

```
package cours

import droolscours.Account;
import droolscours.AccountingPeriod;
import droolscours.CashFlow;
import util.OutputDisplay;

global OutputDisplay showResult;

rule "Account group1"
	ruleflow-group "Group1"
	when
		Account(  )
	then 
		showResult.showText("Account in Group1");
end
rule "Account group2"
	ruleflow-group "Group2"
	when
		Account(  )
	then 
		showResult.showText("Account in Group2");
end

```
Look at the keyword "ruleflow-group". Here the first rule we give it the name "Group1" and the second "Group2". they have the same name as the Rule-flow items we defined in the process definition above. Therefor, the first rule can only be fired when the rule-flow group "Group1" is activated and the same for the second rule and rule-flow group "Group2".















