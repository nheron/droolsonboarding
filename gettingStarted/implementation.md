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


## Create functions 
We will need some java functions to help us writing rules
Go to new ITems/DRL FIle and create a rule called function and put in the  rule content the following code : 


```
import java.util.Calendar;
import java.util.Date;

function int dateCalculation(Date currentDate,Date birthDate) {

   long ageInMillis = currentDate.getTime()-birthDate.getTime();
   Date age = new Date(ageInMillis);
   return (int)(ageInMillis/1000/60/60/24/365);

}

function boolean isBirthday(Date currentDate,Date birthDate){
   boolean result = false;
   Calendar c1 = Calendar.getInstance();
   c1.setTime(currentDate);
   Calendar c2 = Calendar.getInstance();
   c2.setTime(birthDate);
   int day1 = c1.get(Calendar.DAY_OF_MONTH);
   int month1 = c1.get(Calendar.MONTH);
   int day2 = c2.get(Calendar.DAY_OF_MONTH);
   int month2= c2.get(Calendar.MONTH);
   if (day1==day2 && month1==month2){
	result = true;
   }
   return result;
}


function double AgeCalculationYear(Date d1,Date d2) {
	Calendar c1 = Calendar.getInstance();
	c1.setTime(d1);
	int day1=   c1.get(Calendar.DAY_OF_MONTH);
	int month1 = c1.get(Calendar.MONTH);
	int year1 = c1.get(Calendar.YEAR);
	Calendar c2 = Calendar.getInstance();
	c2.setTime(d2);
	int day2=   c2.get(Calendar.DAY_OF_MONTH);
	int month2 = c2.get(Calendar.MONTH);
	int year2 = c2.get(Calendar.YEAR); 
	double val1= (year2-year1);
	double val2=(month2-month1)/12.0;
	double val3=(day2-day1)/365.0;
	double age = val1+val2+val3;
	return age;
}
function double AgeCalculationMonth(Date d1,Date d2) {
	Calendar c1 = Calendar.getInstance();
	c1.setTime(d1);
	int day1=   c1.get(Calendar.DAY_OF_MONTH);
	int month1 = c1.get(Calendar.MONTH);
	int year1 = c1.get(Calendar.YEAR);
	Calendar c2 = Calendar.getInstance();
	c2.setTime(d2);
	int day2=   c2.get(Calendar.DAY_OF_MONTH);
	int month2 = c2.get(Calendar.MONTH);
	int year2 = c2.get(Calendar.YEAR); 
	double val1= (year2-year1)*12;
	double val2=(month2-month1);
	double val3=(day2-day1)/30.0;
	double age = val1+val2+val3;
	return age;
}
```

![](BRMS/Step3-1-Implementation/action08.png)


## Create the initial step

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

![](BRMS/step3-2-Implementation/action18.png)


## Create the decision table for the standard price


## Implement the promotion


## Implement the reduction

## 




