When working with drools, there are things you have to define :

1\) The data model on which the rules applies. As we are working in the java language, a data model is a set of java classes.

2\) The conditions on the left side \(called LHS or the Head\) express constraints on the data model, which have the class name and their attributes.

 3\) The consequence on the right side \(called RHS or the Tail\) which will act on the facts which are in the working memory.

When you want to apply some rules on some data, you will instantiate a java class and give it to the rules engine. This instance is called a Fact object.

To work with the rules engine, we have to instantiate a KieContainer. We will see later how to program it. This kieContainer contains a set of rules. The KieContainer also contains other types of artifacts, which are common to other components like jbpm and optoplanner.

When you want to work with drools, you have to get a KieSession from the KieContainer. This KieSession will allow you to give facts to the rules engine and to ask to fire rules.

