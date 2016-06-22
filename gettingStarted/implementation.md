# Implementation


## Create the process flow

We are going to implement a rule flow with 5 steps.


| Name | ruleflow group name |
| -- | -- |
| init data | init |
| standard price | standard |
| Promotion | promotion |
| Reduction | reduction |
| Subscription | subscription |



![](BRMS/Step3-1-Implementation/action01.png)

We shall give him a name in a package

![](BRMS/Step3-1-Implementation/action02.png)


Select the start event and select the task element : 
[](BRMS/Step3-1-Implementation/action03.png)

Click on the wrench and select "Business Rule Task"


![](BRMS/Step3-1-Implementation/action04.png)


Clock on the "<<" on the right part and the properties will appear. Enter the Name and Ruleflow group name as follows : 

![](BRMS/Step3-1-Implementation/action05.png)

Do the same with other business tasks.

![](BRMS/Step3-1-Implementation/action06.png)

And do not forget to save the process.


## Cloning the git repository
Before going further, if you have git installed on your machine, you can checkout the code by cloning the repository  : 

```
git clone git://machine_ip:9418/nautic
```

![](BRMS/Step3-1-Implementation/action07.png)

In my example, I use a docker container that is in a virtualBox Machine at ip 192.168.99.100 and at port 19418.


## Create the initial step



## Create the decision table for the standard price


## Implement the promotion


## Implement the reduction

## 




