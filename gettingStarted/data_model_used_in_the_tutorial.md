# Data Model used in the tutorial
We are first going to write java code that we are going to use through all the drooks tutorial.
Here is the model we are going to use (taken from presentation done during conferences by Drools members)
We are in a bank that handles account (2) and on each account there can be movements (2). The purpose is to calculate the account balance between an accounting period (3) of all accounts given the movements it has.
We will run all examples in junit Tests.
![](drools/dataModel_fig1.jpeg)

We have to create an AccountProject of type drools as previously describes.
Then we shall create a java package that we can name droolscours package in src/main/java (to respect maven definition) by doing on src/main/java right click and new Package, gibe him a name and push the finish button.


![](drools/dataModel_fig2.jpeg)


and we are going to create 3 java classes : Account, AccountingPeriod and CashFlow by right-clicking on the new package just created and new Class

![](drools/dataModel_fig3.jpeg)


![](drools/dataModel_fig4.png)

And the Account class, add two attributes accountno and balance.
Right click source/generate getter/setter and the Account class will have getter/setter.

![](drools/dataModel_fig5.png)
Do the same for accounting period 
![](drools/dataModel_fig6.png)


and for CashFlow

![](drools/dataModel_fig7.png)

To be able to use junit, we have to add the junit library.
Select the project, right click and select BuildPath/Configure BuildPath

![](drools/dataModel_fig8.png)


Click on the Libraries tab and select the "Add library" button.
![](drools/dataModel_fig9.png)
Select the Junit library and push the next button


![](drools/dataModel_fig10.png)
On the next screen, push the Finish Button
![](drools/dataModel_fig11.png)
and the the Ok button
