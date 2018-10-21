When working with drools, there are things you have to define :

1\) The data model on which the rules apply. As we are working in the Java language, a data model is a set of Java classes.

2\) Rules which are going on one side \(called left side or LHS\) express constraints on the data model, which are class name and their attributes and on the other side \(called right side or RHS\) which will act on the facts which are in the working memory.

When you want to apply some rules on some data, you will instantiate a Java class and give it to the rule engine. This instance is called a Fact object.

To work with the rule engine, we have to instantiate a KieContainer. We will see later how to program it. This KieContainer contains a set of rules. The KieContainer allows also to contain other types of artifacts that are common to other components like jbpm and optoplanner.

When you want to work with drools, you have to get a KieSession from the KieContainer. This KieSession will allow you to give facts to the rule engine and to ask to fire rules.

