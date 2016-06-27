# Implementing the initial step


![](BRMS/step3-2-Implementation/action01.png)

![](BRMS/step3-2-Implementation/action02.png)
![](BRMS/step3-2-Implementation/action03.png)


![](BRMS/step3-2-Implementation/action04.png)


![](BRMS/step3-2-Implementation/action06.png)


![](BRMS/step3-2-Implementation/action07.png)

![](BRMS/step3-2-Implementation/action08.png)

![](BRMS/step3-2-Implementation/action09.png)

![](BRMS/step3-2-Implementation/action10.png)

![](BRMS/step3-2-Implementation/action11.png)

![](BRMS/step3-2-Implementation/action12.png)

![](BRMS/step3-2-Implementation/action13.png)

![](BRMS/step3-2-Implementation/action14.png)

![](BRMS/step3-2-Implementation/action15.png)

![](BRMS/step3-2-Implementation/action16.png)

![](BRMS/step3-2-Implementation/action17.png)

Then you shall obtain the rule as follows. Notice that the stringValue of the calculatedAttribute as a formula. So you should select the formula not a litteral. And also that we had to create a binding varialble "bd" for attribute birthdate of call Person.

![](BRMS/step3-2-Implementation/action18.png)
Notice that we test there is not already a calculated attribute for that person with the same key

Notice that we have to add to the list of calculated attribute of the person and then tell the rule engine the list was updated.




# Test the initial step

The workbench allows to test the rule we do.
Create a new item of type "Test scenario"  like follows : 

![](BRMS/step3-3-implementation/action02.png)


![](BRMS/step3-3-implementation/action01.png)



![](BRMS/step3-3-implementation/action03.png)


Click on the "Given" Cross  and add a new fact as follows : 

![](BRMS/step3-3-implementation/action04.png)

Then click on the "Add Field" text.

![](BRMS/step3-3-implementation/action05.png)
Select the field "quoteDate" : 

![](BRMS/step3-3-implementation/action06.png)

Click on the "Literal value" button

![](BRMS/step3-3-implementation/action07.png)

As the attribute is of type date, you can select a date with the date picker.

![](BRMS/step3-3-implementation/action08.png)

Select a date and then add another instance of type Person

 ![](BRMS/step3-3-implementation/action10.png)
and add a field and select birthdate.
 ![](BRMS/step3-3-implementation/action11.png)
 Select literal value.

 ![](BRMS/step3-3-implementation/action12.png)

And select a date as for the quote date but on same day (here June 30th?
 ![](BRMS/step3-3-implementation/action13.png)
then add a expectatation by clicking on the Cross near Expect
 ![](BRMS/step3-3-implementation/action14.png)
 
Add a fact of type CalculatedAttribute

![](BRMS/step3-3-implementation/action16bis.png)

and Click on the "A fact of type... "
Then chose the StringValue field

 ![](BRMS/step3-3-implementation/action15.png)
 
 And then enter the value true
 
 ![](BRMS/step3-3-implementation/action16ter.png)
 
 And as the rule we want to test is in ruleflow group init. Click on the cross near the "Given"  cross and enter "init" in the activate rule flow group part.

 ![](BRMS/step3-3-implementation/action16.png)


The test scenario should then look like this : 

 ![](BRMS/step3-3-implementation/action17.png)
 Then click the "Run scenario" button twice and you should see the screeen as follows
 ![](BRMS/step3-3-implementation/action18.png)



# Calculate person age

We shall calculate the person age based on his birthday and the curDay attribute of the quote.
At the same time, we shall initialize the price attribute with a BigDecimal.
in the function.drl, add the "import java.math.BigDecimal"

![](BRMS/step3-3bis-Implementation/action03.png)
First add the two classes on which we shall apply the rule.
![](BRMS/step3-3bis-Implementation/action01.png)
Then we should create the rule like that.


![](BRMS/step3-3bis-Implementation/action04.png)

We added two options : the ruleflow group.

Then we can create a test scenario to verify our rule.

![](BRMS/step3-3bis-Implementation/action05.png)

