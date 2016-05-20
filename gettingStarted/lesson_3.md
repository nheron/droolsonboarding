# lesson 3 : Some more drools languages

In lesson 1 et 2, we concentrate on how the rule engine works in the first lesson. In the second lesson, we introduced how to express constraint between facts.
In this lesson, we will concentrate on the available constraint in the drools language.

## Some more classes
To be able to see some more advanced features, we are goig to add 2 new classes in src/main/java droolscours package.

```
package droolscours;

public class Customer {
    private String name;
    private String surname;
    private String country;

    public Customer(String name, String surname, String country) {
        super();
        this.name = name;
        this.surname = surname;
        this.country = country;
    }

    public Customer() {
        super();
        // TODO Auto-generated constructor stub
    }

    public String getCountry() {
        return country;
    }

    public void setCountry(String country) {
        this.country = country;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getSurname() {
        return surname;
    }

    public void setSurname(String surname) {
        this.surname = surname;
    }

    @Override
    public String toString() {
        StringBuffer buff = new StringBuffer();
        buff.append("-----Customer-----)\n");
        buff.append("Name=" + this.name + "\n");
        buff.append("Surname Name=" + this.surname + "\n");
        buff.append("Country=" + this.country + "\n");
        buff.append("-----Customer end-)");
        return buff.toString();
    }

}
```

```
package droolscours;

public class PrivateAccount extends Account {
    private Customer owner;

    public Customer getOwner() {
        return owner;
    }

    public void setOwner(Customer owner) {
        this.owner = owner;
    }

    @Override
    public String toString() {
        StringBuffer buff = new StringBuffer();
        buff.append("-----Private Account-)");
        buff.append(super.toString());
        if (this.owner != null) {
            buff.append(this.owner.toString());
        }
        buff.append("-----Private Account end-)");
        return buff.toString();
    }
}

```



## In Constraint

![](drools/lesson3_fig1.png)


## Nested Accessor

## And/or

## not

## exist

## ForAll

## From

## counting

## Summing


