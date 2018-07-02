# Meaningful Names

  * *Use intention revealing names*

Names should reveal intent. They should answer the big questions. Why who, how. If a name needs a comment, then the name is not revealing its intent.

Rather than `const d; // elapsed time in days`, use something like the following:

```
const elapsedTimeInDays;
const daysSinceCreation;
const daysSinceModification;
const fileAgeInDays;
```

  * *Avoid disinformation*

Try to use abbreviations as little as possible to improve readability. Avoid names which are very similar to other functions/variables/methods.

  * *Make meaningful distinctions*

Distinguish names so the reader can easily discern what similarly named variables/methods do. Avoid similarly named functions/variables like this:

```
getActiveAccount();
getActiveAccounts();
getActiveAccountInfo();
```

  * *Use pronouncable names*

Everything should be pronouncable. It allows us to communicate with peers better about the code and our brain is much more adept about reasoning when using pronouncable words.

Bad example: `genymdhms` (generation date, year, month, day, hour, minute, and second)

  * *Use searchable names*

The length of a name should correspond to the size of its scope. Single-letter names can ONLY be used as local variable inside short methods, and potentially avoided altogether.

Do not use magic numbers or values - instead place them in a descriptively named constant.

  * *Class names*

Classes and objects should have noun or noun phrase names like Customer, WikiPage, Account, and AddressParser. Avoid words like Manager, Processor, Data, or Info in the name of a class. A class name should not be a verb.

  * *Method names*

Methods should have verb or verb phrase names like postPayment, deletePage, or save. Accessors, mutators, and predicates should be named for their value and prefixed with `get`, `set`, and `is`. Good example:

```
string name = employee.getName();
customer.setName("mike");
if (paycheck.isPosted())...
```

When constructors are overloaded, use static factory methods with names that describe the arguments. For example,

```
Complex fulcrumPoint = Complex.FromRealNumber(23.0);
```

is generally better than

```
Complex fulcrumPoint = new Complex(23.0);
```

  * *Pick one word per concept*

Pick one word for one abstract concept and stick with it. For instance, it’s confusing to have `fetch`, `retrieve`, and `get` as equivalent methods of different classes.

  * *Don't pun*

Avoid using the same word for two purposes. Using the same term for two different ideas is essentially a pun.

If you follow the “one word per concept” rule, you could end up with many classes that have, for example, an `add` method. As long as the parameter lists and return values of the various `add` methods are semantically equivalent, all is well.

However one might decide to use the word `add` for “consistency” when he or she is not in fact adding in the same sense. Let’s say we have many classes where `add` will create a new value by adding or concatenating two existing values. Now let’s say we are writing a new class that has a method that puts its single parameter into a collection. Should we call this method `add`? It might seem consistent because we have so many other `add` methods, but in this case, the semantics are different, so we should use a name like `insert` or `append` instead. To call the new method add would be a pun.

  * *Use solution domain names*

The people reading your code are programmers - it's fine to use commonly known technical names.

  * *Add meaningful context*

Imagine that you have variables named `firstName`, `lastName`, `street`, `houseNumber`, `city`,`state`, and `zipcode`. Taken together it’s pretty clear that they form an address. But what if you just saw the state variable being used alone in a method? Would you automatically infer that it was part of an address?

You can add context by using prefixes: `addrFirstName`, `addrLastName`, `addrState`, and so on. At least readers will understand that these variables are part of a larger structure. Of course, a better solution is to create a class named `Address`. Then, even the compiler knows that the variables belong to a bigger concept.

  * *Don't add gratuitous context*

Shorter names are generally better than longer ones, so long as they are clear. Add no more context to a name than is necessary.