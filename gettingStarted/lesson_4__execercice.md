# Cost transport calculator


The purpose of the exercise is to go through all steps of a real project when using a rule engine like drools. The use case is simple enough to be realized within one or two working days. We first expose the business requirements like they may be expressed by users. Then we are going to design the implementation we shall use. Feel free to modify the implementation if you think it is not how you would have done it. The only point of view you should keep is to use declarative programming versus procedural code.

It is very common for newcomers to write a few rules with huge then parts. It works. But you should remember that the implemented algorithms that are behind drools will work best if you express a lot of pattern expressions (constraints) on java facts and if you insert new facts that are the result of a rule. 
For example, in a loyalty system in a retail industry, if a customer is coming more than twice per month on the web site or in the shop, then he is a gold customer. This is a fact that can be used in other rules as input. 

This is how the rules engine was designed to be used, and when you see business requirements it is how they are expressed naturally.
