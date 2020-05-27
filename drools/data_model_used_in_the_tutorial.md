# Data Model used in the tutorial

## Data Model used in the tutorial

We are first going to write java code that we are going to use through all the drooks tutorial.  
Here is the model we are going to use \(taken from presentation done during conferences by drools members\)  
We are in a bank that handles accounts \(2\) and on each account there can be movements \(1\). The purpose is to calculate the account balance between an accounting period \(3\) of all accounts given the movements it has.  
We will run all examples in junit Tests.  
This data model is the same as you can find in the reference model in the drools documentation.  
![](../.gitbook/assets/dataModel_fig1.jpeg)

### Implement the pojo model

We have to create an AccountProject of type drools as previously describes.  
Then we shall create a java package that we can name droolscours package in src/main/java \(to respect maven definition\) by doing on src/main/java right click and new Package, gibe him a name and push the finish button.

![](../.gitbook/assets/dataModel_fig2.jpeg)

and we are going to create 3 java classes : Account, AccountingPeriod and CashFlow by right-clicking on the new package just created and new Class

![](../.gitbook/assets/dataModel_fig3.jpeg)

![](../.gitbook/assets/dataModel_fig4.png)

And the Account class, add two attributes accountno and balance.  
Right click source/generate getter/setter and the Account class will have getter/setter.

![](../.gitbook/assets/dataModel_fig5.png)  
Do the same for accounting period  
![](../.gitbook/assets/dataModel_fig6.png)

and for CashFlow

![](../.gitbook/assets/dataModel_fig7.png)

## Add JUnit library

To be able to use junit, we have to add the junit library.  
Select the project, right click and select BuildPath/Configure BuildPath

![](../.gitbook/assets/dataModel_fig8.png)

Click on the Libraries tab and select the "Add library" button.  
![](../.gitbook/assets/dataModel_fig9.png)  
Select the Junit library and push the next button

![](../.gitbook/assets/dataModel_fig10.png)  
On the next screen, push the Finish Button  
![](../.gitbook/assets/dataModel_fig11.png)  
and the the Ok button

![](../.gitbook/assets/dataModel_fig12.png)  
The Junit libray is now part of the project  
![](../.gitbook/assets/dataModel_fig13.png)

We now have to create some directory.  
Select the src directory and right click button new Directory.

![](../.gitbook/assets/dataModel_fig14.png)  
Enter test/java in the folder name and press finish.  
Do the same but test/rules.  
The folder part should look like that :  
![](../.gitbook/assets/dataModel_fig15.png)

now Select src/test/java and right click buildpath/use as source folder

![](../.gitbook/assets/dataModel_fig16.png)

Do the same with src/test/rules  
now the project should look like this :

![](../.gitbook/assets/dataModel_fig17.png)

## Create a Helper Class

To simplify the writing of tests, we shall write a helper class.  
To do, we first create a package called util and in there create a class that we shall all KnowledgeSessionHelper

![](../.gitbook/assets/dataModel_fig18.png)

![](../.gitbook/assets/dataModel_fig20.png)  
Then create a new class called KnowledgeSessionHelper

![](../.gitbook/assets/dataModel_fig21.png)

![](../.gitbook/assets/dataModel_fig22.png)  
In the Class, the content should look like here  
![](../.gitbook/assets/dataModel_fig23.png)

## Create the first test case

Select the src/test/java package and Right click Other and type junit. Select Junit Test case

![](../.gitbook/assets/dataModel_fig24.png)

Push the next Button.  
In the next screen, enter droolscours as package name and FirstTry as Name

![](../.gitbook/assets/dataModel_fig25.png)

And push the Finish Button

the code should be entered like this :

![](../.gitbook/assets/dataModel_fig26.png)  
Select the open class, Right click and run as JUnit Test :

![](../.gitbook/assets/dataModel_fig27.png)  
And the Junit Window should appear as above. \(of course no rules were fired\).

We are now ready to start the lessons.

