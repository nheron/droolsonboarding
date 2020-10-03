# Drools tutorial

When working with drools, there are things you have to define :

1\) The data model on which the rules apply. As we are working in the java language, a data model is a set of java classes.

2\) Rules which are going on one side \(called left side or LHS\) express constraints on the data model, which here class name and their attributes and on the other side \(called right side or RHS\) which will act on the facts which are in the working memory.

When you want to apply some rules on some data, you will instantiate a java class and give it to the rule engine. This instance is called a Fact object.

To work with the rule engine, we have to instantiate a KieContainer. We will see later how to program it. This kieContainer contains a set of rules. The KieContainer can also be used in jbpm and Optaplanner projects.

When you want to work with drools, you have to get a KieSession from the KieContainer. This KieSession will allow you to give facts to the rule engine and to ask to fire rules.

