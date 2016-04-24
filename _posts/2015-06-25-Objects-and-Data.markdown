---
layout: post
title: "Ew, you got methods in your data"
date: 2015-06-25
comments: true
categories: [Development]
---

I think we might have gone a bit too far with objects.

Whilst combining state with functions is a fantastic tool, it
shouldn't be the default. In fact, from this point forward I shall be
treating it as a smell.

The default should be data structures that are operated on by
functions, not objects that are manipulated by their own methods.

Clearly, I am not even close to the first at reaching this conclusion.
UNIX, functional programming, imperitive programming, declaritive
programming, micro-services all of them work on this principle, and
yet in the OO world, it is heresy to even think about seperating state
and functions.

I'm going to explore this via an imaginary project that has at its
heart a dataset of People and an evolving set of reasonable
requirements. The examples are roughly Java/C# style, as static typing
and single inheritence really help to magnify the problem, and most
developers are familiar with this style of syntax. 

~~~
public class Person {
    Date dateOfBirth;
    String firstName;
    String lastName;

    public Date age(){
        return Date.now().minus(dateOfBirth);
    }

    public String fullName(){
        return firstName + " " + lastName;
    }
}

public class DeadPerson extends Person {
    Date dateOfDeath;
    
    public Date age(){
        return dateOfDeath.minus(dateofBirth);
    }
}
~~~
{: .language-java}

Here we have a lovely example of the beauty of object orienation. By
grouping together functions with the data that they're supposed to be
operating on I have managed to provide a consistent interface to the
pesky problem of age() of a DeadPerson and I can still leverage the
name logic. Mission Accomplished.

Wait. What? Some people want their first name, second?

OK!

~~~
public class ChinesePerson extends Person {
    public String fullName(){
        return lastName + " " + firstName;
    }
}
~~~
{: .language-java}

Excellent, mission accomplished.

Wait? We need to track Dead Chinese people?

OK!

~~~
public class DeadChinesePerson extends DeadPerson {
    public String fullName(){
        return lastName + " " + firstName;
    }
}
~~~
{: .language-java}

Hmmmm, that is less cool. We now have a bit of Copy-Paste-Modify in
there. That's ok! I'll just inherit from two objects... oh, I can't do
that in Java, Ruby, Scala.

At this point the multiple inheritence language folks are chuckling,
but even they will struggle to differentiate which version of the
method they should call, as it usually ends up being determined by
order of inheritence. Good job we wrote some unit tests and our
developers never make mistakes.

However, we're going to see this through Java. So we're cool with the copy
and paste? I thought so too.

A few days later...

You want the user to be able to be able to sort each Person by their
age?

Sure, thats easy!

I'll just modify the Person class on it so its Comparable.

~~~
public class Person implements Comparable{
    Date dateOfBirth;
    String firstName;
    String lastName;

    public Date age(){
        return Date.now().minus(dateOfBirth);
    }

    public String fullName(){
        return firstName + " " + lastName;
    }

    public int compare(Person b){
        return age() - b.age();
    }
}
~~~
{. language-java}

Mission accomplished!

What do you mean there is a bug?

Of course James Dean, River Phoenix and Adele all sort to the same
point and not always in the same order. They're same age. Oh, you want
to toggle the ability to choose between: age at death, age since birth
and if one is alive and one is dead I should tie break on age since
birth... unless the user changes their mind. Fuck you. I mean,I guess I can do that, I'll just open up and change compare on
DeadPerson and DeadChinesePerson. Yes I know that is more copy and
paste.

Mission accomplished?!

What do you mean the Icelanders are complaining?

What about them? No lastname? That's not true! Bjork has a lastname...
oh it needs to be calculated? How? I need to
know the parent... fuckkkkk.  And whilst I'm at it I should fix the age for
Koreans? What do you mean? They take their age from the start of the year? Thats
interesting, and you want users to be able to choose how they are
ordered, at runtime... 

I hate my job... what was the mission again?

These problems go away the minute we stop including the functions with
the Person. We can have a series of different fullname and comparator
objects that we can combine in different ways, via dependecy injection,
at runtime.

~~~
public class Person {
    Date dateOfBirth;
    String firstName;
    String lastName;
    Date dateOfDeath;
    Person parent1;
    Person parent2;
    boolean gender;
}
    
public interface Agist {
    int age(Person p);
}

public class AgeSinceBirth implements Agist {...}
public class AgeAtDeath implements Agist { ...}
public class AgeSinceStartOfFirstYear implements Agist{...}
public class AgeAtYearofDeath implements Agist{...}

public interface DisplayNamer {
    String name(Person p);
}

public class IcelandicNamer implements DisplayNamer {...}

public class CompareByAge implements Comparator{
    Map<Tuple<Class, Class>, Tuple<Agist, Agist>> agism;

    public CompareByAge(Map<Tuple<Class, Class>, Tuple<Agist, Agist>> agism){
        this.agism = agism;
    }

    public int compare(Person a, Person b){
        Tuple<Agism, Agism> agers = agism.get(new Tuple(a.class,
            b.class));
    
        return agers.first.age(a) - agers.second.age(b);
    }
}

public class KoreanPerson extends Person {}
public class IcelandicPerson extends Person {}
public class ChinesePerson extends Person {}
public class DeadPerson extends Person {}
public class Dead...
~~~
{: language-java}

Okay, so we've got rid of the cut and paste code, thats good, and now
we just have a bunch of Decorator classes. Never been a huge fan of
the pattern, but its working for as the moment. There is a really good
chance that we'll have to modify the Person class in the future...
shame its public.

Mission Accomplished!

We're getting sued by an LGBT group? Gender isn't binary? But if its not
binary, how do I decide which parent to use for the Icelandic name?
Shit, divorced parents, same gender parents, adopted parents... ok ok.

So I'll make gender a float, and allow a list of parents and pick the
parent with gender closest to person.

Mission Accomplished!

Wow! All this extra work is paying off, we're really starting to grow
and as more complaints come in we have a clear path to improve out
code base and only the configuration is growing excellent work.

You bought more data? Ok, thats cool. Huh, they return a Person class
too, hooray for namespaces. Hmmm, they don't use a float for gender,
they don't track parents and the person class has naive implementation
of Comparable attached.

Thats ok, we'll just build a tool that translates from their Person to
our Person. It'll take a few weeks, but we're good. I'm sure with
enough unit tests and test data we'll figure out all the edge cases.

Its at this point the dynamic oo folks start laughing. Different
person class, who cares, if it looks like a duck... We'll just add a
few null and type checks here and there with configurable defaults and they'll
be fine.

Another datastore? Sure, that will take a few weeks too. Nope, that
code isn't reusable, it expects the other person class. OK,
fine, we'll refactor so that we're using composable translators.

A few weeks later...

Yeah the refactoring took a week and saved us a week, so we broke even.

Two more datastores. Shit, assumptions we made about incoming People
was wrong. They don't use any primitives and have different classes
for each of the properties on the object. We will have to refactor again. This will take about a
month. What do you mean we don't have a month?

The dynamic folks are shitting themselves a bit here. They may have
got lucky, but its likely they are also scrambling to get data from
this more complex, more OO object... but they're still in better shape
than the Java folks.

However, the functional folks are still sitting pretty. Because all
their code still works. Sure they have to compose a new translator,
but its made up of well tested, often mathematically proven functions
that operate on primitives. So what if firstname is nested in a
different map?

Transforming datastructure is what functional, dynamic languages
excel at. However, its not like statically type OO languages are bad
at manipulating primitives, they just don't get the chance to do it
very often, because we like to hide our primitives in objects.

Even if we could translate our objects to dictionaries like pythonista
and rubyists are so fond of doing, we still have to remove the
methods before we can start to process.

What happens if we don't have a Person class at all?

~~~
public interface Agist {
    int age(Map<Object> p);
}

public class AgeSinceBirth implements Agist {...}
public class AgeAtDeath implements Agist { ...}
public class AgeSinceStartOfFirstYear implements Agist{...}
public class AgeAtYearofDeath implements Agist{...}

public interface DisplayNamer {
    String name(Map<Object> p);
}

public class IcelandicNamer implements DisplayName {...}
public class CompareByAge implements Comparator{
Map<Tuple<Schema, Schema>, Tuple<Agist, Agist>> agism;
SchemaIdentifier magic;
    
public CompareByAge(Map<Tuple<Schema, Schema>,Tuple<Agist,Agist>> agism
    SchemaIdentifier magic){
    this.agism = agism;
    this.magic = magic;
}

public int compare(Map<Object> a, Map<Object> b){
            
    Tuple<Agism, Agism> agers = agism.get(new Tuple(magic.getSchema(a),
    magic.getSchema(b)));

    return agers.first.age(a) - agers.second.age(b);
    }
}
~~~
{: .language-java}

Now if we can get our datastores to output something like JSON, we can
spend the rest of our happy careers writing code that translates one
JSON format to anyone of our valid schema in mathematically provable
ways. Worst case, we leverage serializers for the ones
that won't play ball. Then we just add new schemas, namers and agifiers as and when we
discover them.

The key thing here is that functions that care less about the class of
their arguments and more about the shape are ultimately much more
flexible. Sure, we could spend a significant amount of time updating
the various Person classes, but if we don't we create this magical
entity: the library.

The code outline above is portable. You could release it as open
source, and anyone who has a Person problem could use it... provided
that they don't make the mistake of describing their domain
data in objects.

It is also trivial to translate output of these classes back into
JSON, so we have the foundation of a Person service. 

One of the reasons I chose Java as my example code is because it
runs on the JVM, much like Clojure, JRuby, Scala, Jython, Javascript
(Rhino) to name but a few. Whilst all of these languages jump through hoops to be
compatible with Java's statically typed objects, they are much happier
dealing with primitives and built in datastructures like List and Map,
as they don't necessarily embrace static typing or even objects for
that matter.

So separating data from our objects allows to solve problems in less
code, in more flexible ways and makes it easier to compose applications
from collections of object agnostic libraries in any language
compatible with the runtime.

Now I posit that this is still OO code. Its not functional, we're
still using objects and a bit of inheritance, but we're building
objects designed to operate on data, not other objects.

Building applications on libraries that interact via passing messages
containing data is exactly what Alan Kay had in mind. It is the
foundation of Unix, functional programming, imperitive programming and
I hope I've demonstrated that Object Orientated should be writen this
way too.
