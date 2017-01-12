# Cost transport calculator


The purpose of the exercise is to go through all steps of a real project when using a rule engine like drools. The use case is simple enough to be realize withing one or two working days. 
We first expose the business requirements like they may be expressed by users. Then we are going to design the implementation we shall use. Feel free to modify the implementation if you think it is not how you would have done. The only point of view you should keep is to use declarative programming versus procedural code.
It is very common for new comers to write a few rules and implement huge then part of rules. It works. But you should remember that the implemented algorithms that are behind drools will work best if you express a lot a pattern expressions (constraints) on java facts and if you insert new fact that are the result of a rule. 
For example, in a loyalty system in retail industry, if a customer is comming more than twice per month on the web site or in the shop, than he is a gold customer. this is a fact that can be used in other rules as input. 
This is how the rule engine was thought to be used and when you see business requirements it is how it is expressed naturally.