# Implementing the Child over 3 years old is free promotion step

## Creating the rule

Create a new Guided Rule that you call YougestUnder3yearsOldFree

then Add a new Constraint

![](<../.gitbook/assets/action01 (8).png>)

![](<../.gitbook/assets/action02 (7).png>)

Select the List class. Click on the "There is a list.." and the click on the Expression Builder button

![](<../.gitbook/assets/action03 (6).png>)

on the first "Choose" select the size() function and on the second "greater than"

![](<../.gitbook/assets/action04 (7).png>)

Then click on the pencil ![](<../.gitbook/assets/action05 (5).png>) Click on the "From Collect" link and then chose the person fact type

![](<../.gitbook/assets/action06 (5).png>)

![](<../.gitbook/assets/action07 (5).png>)

Then click on the "All Person with" link and select the age attribute and add the following constraint.

![](<../.gitbook/assets/action08 (5).png>)

Then Add a new constraint of type Accumulate

![](<../.gitbook/assets/action09 (2).png>)

And select the Number type from the add a pattern link.

![](<../.gitbook/assets/action11 (4).png>)

Then make the rule look like this

![](<../.gitbook/assets/action13 (4).png>)

## Creating rule to insert a period

![](<../.gitbook/assets/action04 (8).png>)

Create a drl file with the following content

![](<../.gitbook/assets/action05 (6).png>)

## Creating rule to start a process

To be able to start a process from a test scenario, we want to insert an object and set a attribute that would be the process id we want to start. So we first create a new Item of type Data Obkect that we shall call StartProcess. And we should add a field called procesId of type String

![](<../.gitbook/assets/action01 (9).png>)

Then we shall create a guided rule called StartProcessRule as follows. In the Then add free form drl ![](<../.gitbook/assets/action03 (7).png>)

![](<../.gitbook/assets/action02 (8).png>)

## Testing the rule

Create the test scenario by inserting Objects like follows.

![](<../.gitbook/assets/action06 (6).png>)
