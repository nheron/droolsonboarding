# Implementation the promotion step

## Creating the rule

Creating a new Guided Rule that you call YougestUnder3yearsOldFree

then Add a new Constraint


![](BRMS/Step3-5-Implementation/action01.png)



![](BRMS/Step3-5-Implementation/action02.png)

Select the List class.
Click on the "There is a list.." and the click on the Expression Builder button


![](BRMS/Step3-5-Implementation/action03.png)




on the first "Choose" select the size() function and on the second "greater than"


![](BRMS/Step3-5-Implementation/action04.png)

Then click on the pencil 
![](BRMS/Step3-5-Implementation/action05.png)
Click on the "From Collect" link and then  chose the person fact type 

![](BRMS/Step3-5-Implementation/action06.png)


![](BRMS/Step3-5-Implementation/action07.png)

Then click on the "All Person with" link an dselect the age attribute and add the following constraint.

![](BRMS/Step3-5-Implementation/action08.png)

Then Add a new constraint of type Accumulatte

![](BRMS/Step3-5-Implementation/action09.png)

And select the Number type from the add a pattern link.

![](BRMS/Step3-5-Implementation/action11.png)


Then make the rule look like this

![](BRMS/Step3-5-Implementation/action13.png)




## Test the rule











