# Implementing the Child over 3 years old is free promotion step

## Creating the rule

Create a new Guided Rule that you call YougestUnder3yearsOldFree

then Add a new Constraint

![](../.gitbook/assets/action01%20%283%29.png)

![](../.gitbook/assets/action02%20%283%29.png)

Select the List class. Click on the "There is a list.." and the click on the Expression Builder button

![](../.gitbook/assets/action03%20%282%29.png)

on the first "Choose" select the size\(\) function and on the second "greater than"

![](../.gitbook/assets/action04%20%283%29.png)

Then click on the pencil ![](../.gitbook/assets/action05%20%283%29.png) Click on the "From Collect" link and then chose the person fact type

![](../.gitbook/assets/action06%20%283%29.png)

![](../.gitbook/assets/action07%20%283%29.png)

Then click on the "All Person with" link and select the age attribute and add the following constraint.

![](../.gitbook/assets/action08%20%283%29.png)

Then Add a new constraint of type Accumulate

![](../.gitbook/assets/action09%20%282%29.png)

And select the Number type from the add a pattern link.

![](../.gitbook/assets/action11%20%282%29.png)

Then make the rule look like this

![](../.gitbook/assets/action13%20%282%29.png)

## Creating rule to insert a period

![](../.gitbook/assets/action04%20%288%29.png)

Create a drl file with the following content

![](../.gitbook/assets/action05%20%286%29.png)

## Creating rule to start a process

To be able to start a process from a test scenario, we want to insert an object and set a attribute that would be the process id we want to start. So we first create a new Item of type Data Obkect that we shall call StartProcess. And we should add a field called procesId of type String

![](../.gitbook/assets/action01%20%289%29.png)

Then we shall create a guided rule called StartProcessRule as follows. In the Then add free form drl ![](../.gitbook/assets/action03%20%288%29.png)

![](../.gitbook/assets/action02%20%288%29.png)

## Testing the rule

Create the test scenario by inserting Objects like follows.

![](../.gitbook/assets/action06%20%286%29.png)

