# Classes

* *Class organisation*

Following the standard Java convention, a class should begin with a list of variables. Public static constants, if any, should come first. Then private static variables, followed by private instance variables. There is seldom a good reason to have a public variable.

* *Encapsulation*

Keep our variables and utility functions private as much as possible.

* *Classes should be small*

The first rule of classes is that they should be small. The second rule of classes is that they should be smaller than that. No, we’re not going to repeat the exact same text from the Functions chapter. But as with functions, smaller is the primary rule when it comes to designing classes. As with functions, our immediate question is always “How small?”

With functions we measured size by counting physical lines. With classes we use a different measure. We count responsibilities.

The name of a class should describe what responsibilities it fulfills. In fact, naming is probably the first way of helping determine class size. If we cannot derive a concise name for a class, then it’s likely too large. The more ambiguous the class name, the more likely it has too many responsibilities. For example, class names including weasel words like Processor or Manager or Super often hint at unfortunate aggregation of responsibilities.

We should also be able to write a brief description of the class in about 25 words, without using the words “if,” “and,” “or,” or “but.”

* *The single responsibility principle*

The Single Responsibility Principle (SRP) states that a class or module should have one, and only one, reason to change (responsibility). This principle gives us both a definition of responsibility, and a guidelines for class size. Classes should have one responsibility—one reason to change.

Trying to identify responsibilities (reasons to change) often helps us recognize and create better abstractions in our code.

To restate the former points for emphasis: We want our systems to be composed of many small classes, not a few large ones. Each small class encapsulates a single responsibility, has a single reason to change, and collaborates with a few others to achieve the desired system behaviors.

* *Cohesion*

Classes should have a small number of instance variables. Each of the methods of a class should manipulate one or more of those variables. In general the more variables a method manipulates the more cohesive that method is to its class. A class in which each variable is used by each method is maximally cohesive.

* *Maintaining Cohesion Results in Many Small Classes*