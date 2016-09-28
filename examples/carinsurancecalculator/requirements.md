# Car Insurance Calculator



This project is used by the jbpm tutorial.



The purpose is to implement a calculator that shall give a a list of prices to insure a car for a given car and a list of drivers.

The car data contains when it was first registered, the fiscal power, the brand name and the model name



In Input, the calculator should receive a quote requet, containing the car , the list of drivers. The calculator should send back the same request object with added objects :



* the list of propositions with options



* the list of yellow or red rules that were fired.





If a red rule is fired, the calculation can stop. If a yellow rule is fired, the calculation can continu.



| Red Rule name | Description |

| --- | --- |

| OnlyDriverUnder18yearsold | If there is only one driver given and the age is under 16 years old. |



| Yellow Rule Name | Description |

| --- | --- |

| OneDriverBetween16And18YearsOld | If one driver is between 16 and 18 years and no other driver is over 25 years old and has no accident in the last 2 years and maximum 2 accidents in the last 5 years |

| OneDriverTooOld | If one driver is over 75 years old |



Base Price



| Fiscal Power bigger than | Fiscal powwer less than | Base Price per year | Comment |

| --- | --- | --- | --- |

| | 0 | 300 | Electrical Car |

| 1 | 4 | 500 | |

| 5 | 7 | 700 | |

| 8 | 11 | 950 | |

| 12 | 17 | 1200 | |

| 18 | | 1400 | |



Here are the available options.



| Fiscal Power bigger than | Fiscal powwer less than | Option price per year | Comment |

| --- | --- | --- | --- |

| 1 | 4 | 600 | Full Risk |

| 5 | 7 | 800 | Full Risk |

| 8 | 11 | 1200 | Full Risk |

| 12 | 17 |2000 | Full Risk |

| 1 | 4 | 400 | Stolen Damage |

| 5 | 7 | 300 | Stolen Damage |

| 8 | 11 | 600 | Stolen Damage |

| 12 | 17 | 1000 | Stolen Damage |

| 1 | 4 | 200 | Car Glass Damage |

| 5 | 7 | 300 | Car Glass Damage |

| 8 | 11 | 400 | Car Glass Damage|

| 12 | 17 | 500 | Car Glass Damage |







Here are the prices to add (to be applied per declared driver and per base+option).





| Age bigger than | Age smaller than | Maximum number accident last 2 years | number accident last 5 years less than | % to add to base price |

| --- | --- | --- | --- | --- |

| 16 | 18 | | | +20% |

| 18 | 30 | 0| 0| +5% |

| 18 | 30 | 0| 2 | +10% |

| 18 | 30 | 2| 4| +12% |

| 30 | | 0| 0| +0% |

| 30 | | 5 | 5 | +10% |

All other cases +25% per driver



If more than 4 drivers are declared in the request, starting from the fourth driver and over are free. The 3 drivers to take are the most expansive.





At the end, there can be only one yellow rule that can be fired.
















