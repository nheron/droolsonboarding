# Car Insurance Calculator

This project is used by the jbpm tutorial.

The purpose is to implement a calculator that shall give a a list of prices to insure a car for a given car and a list of drivers.

In Input, the calculator should receive a quote requet, containing the car , the list of drivers. The calculator should send back the same request object with added objects :

* the list of propositions with options

* the list of yellow or red rules that were fired.


If a red rule is fired, the calculation can stop. If a yellow rule is fired, the calculation can continu.



| Red Rule name | Description |
| --- | --- |
| OnlyDriverUnder18yearsold | If there is only one driver given and the age is under 16 years old. |



| Yellow Rule Name | Description |
| --- | --- |
| OneDriverBetween16And18YearsOld | If one driver is between 16 and 18 years and no other driver is  over 25 years old and has no accident in the last 2 years and maximum 2 accident ont he last 5 years |



