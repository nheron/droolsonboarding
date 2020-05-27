# Implementing the initial step

## Implementing the initial step

![](../.gitbook/assets/action01%20%286%29.png)

![](../.gitbook/assets/action02%20%286%29.png) ![](../.gitbook/assets/action03%20%285%29.png)

![](../.gitbook/assets/action04%20%285%29.png)

![](../.gitbook/assets/action06%20%284%29.png)

![](../.gitbook/assets/action07%20%284%29.png)

![](../.gitbook/assets/action08%20%284%29.png)

![](../.gitbook/assets/action09%20%283%29.png)

![](../.gitbook/assets/action10%20%282%29.png)

![](../.gitbook/assets/action11%20%283%29.png)

![](../.gitbook/assets/action12%20%282%29.png)

![](../.gitbook/assets/action13%20%283%29.png)

![](../.gitbook/assets/action14%20%281%29.png)

![](../.gitbook/assets/action15%20%281%29.png)

![](../.gitbook/assets/action16%20%281%29.png)

![](../.gitbook/assets/action17%20%281%29.png)

Then you shall obtain the rule as follows. Notice that the stringValue of the calculatedAttribute as a formula. So you should select the formula not a litteral. And also that we had to create a binding varialble "bd" for attribute birthdate of call Person.

![](../.gitbook/assets/action18%20%281%29.png) Notice that we test there is not already a calculated attribute for that person with the same key

Notice that we have to add to the list of calculated attribute of the person and then tell the rule engine the list was updated.

## Test the initial step

The workbench allows to test the rule we do. Create a new item of type "Test scenario" like follows :

![](../.gitbook/assets/action02%20%287%29.png)

![](../.gitbook/assets/action01%20%287%29.png)

![](../.gitbook/assets/action03%20%286%29.png)

Click on the "Given" Cross and add a new fact as follows :

![](../.gitbook/assets/action04%20%286%29.png)

Then click on the "Add Field" text.

![](../.gitbook/assets/action05%20%284%29.png) Select the field "quoteDate" :

![](../.gitbook/assets/action06%20%285%29.png)

Click on the "Literal value" button

![](../.gitbook/assets/action07%20%285%29.png)

As the attribute is of type date, you can select a date with the date picker.

![](../.gitbook/assets/action08%20%285%29.png)

Select a date and then add another instance of type Person

![](../.gitbook/assets/action10%20%283%29.png) and add a field and select birthdate. ![](../.gitbook/assets/action11%20%284%29.png) Select literal value.

![](../.gitbook/assets/action12%20%283%29.png)

And select a date as for the quote date but on same day \(here June 30th? ![](../.gitbook/assets/action13%20%284%29.png) then add a expectatation by clicking on the Cross near Expect ![](../.gitbook/assets/action14%20%282%29.png)

Add a fact of type CalculatedAttribute

![](../.gitbook/assets/action16bis.png)

and Click on the "A fact of type... " Then chose the StringValue field

![](../.gitbook/assets/action15%20%282%29.png)

And then enter the value true

![](../.gitbook/assets/action16ter.png)

And as the rule we want to test is in ruleflow group init. Click on the cross near the "Given" cross and enter "init" in the activate rule flow group part.

![](../.gitbook/assets/action16%20%282%29.png)

The test scenario should then look like this :

![](../.gitbook/assets/action17%20%282%29.png) Then click the "Run scenario" button twice and you should see the screeen as follows ![](../.gitbook/assets/action18%20%282%29.png)

## Calculate person age

We shall calculate the person age based on his birthday and the curDay attribute of the quote. At the same time, we shall initialize the price attribute with a BigDecimal. in the function.drl, add the "import java.math.BigDecimal"

![](../.gitbook/assets/action03%20%287%29.png) First add the two classes on which we shall apply the rule. ![](../.gitbook/assets/action01%20%288%29.png) Then we should create the rule like that.

![](../.gitbook/assets/action04%20%287%29.png)

We added two options : the ruleflow group.

Then we can create a test scenario to verify our rule.

![](../.gitbook/assets/action05%20%285%29.png)

