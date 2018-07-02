# Functions

So what is it that makes a function easy to read and understand? How can we make a function communicate its intent? What attributes can we give our functions that will allow a casual reader to intuit the kind of program they live inside?

  * *Small*

The first rule of functions is that they should be small. The second rule of functions is that they should be smaller than that.

Functions should hardly ever be as long as even 20 lines. Ideally they shouldn't be more than 10, and many of them can be 3-5 lines.

Within if, else and while statements, ideally the code within the block should only be one line - often a function call.

Functions should not have nested structures and should not be indented by more than one or two levels.

  * *Do one thing*

Functions should do one thing. THey should do it well. They should do it only.

If a function does more than one thing, create a function at a level of abstraction one level higher.

So, another way to know that a function is doing more than “one thing” is if you can extract another function from it with a name that is not merely a restatement of its implementation

  * *One level of abstraction per function*

In order to make sure our functions are doing “one thing,” we need to make sure that the statements within our function are all at the same level of abstraction.

We want the code to read like a top-down narrative.5 We want every function to be followed by those at the next level of abstraction so that we can read the program, descending one level of abstraction at a time as we read down the list of functions. This is called The Stepdown Rule.

To say this differently, we want to be able to read the program as though it were a set of TO paragraphs, each of which is describing the current level of abstraction and referencing subsequent TO paragraphs at the next level down.

  1. To include the setups and teardowns, we include setups, then we include the test page content, and then we include the teardowns.
  2. To include the setups, we include the suite setup if this is a suite, then we include the regular setup.
  3. To include the suite setup, we search the parent hierarchy for the “SuiteSetUp” page and add an include statement with the path of that page.
  4. To search the parent. . .

It turns out to be very difficult for programmers to learn to follow this rule and write functions that stay at a single level of abstraction. But learning this trick is also very important. It is the key to keeping functions short and making sure they do “one thing.” Making the code read like a top-down set of TO paragraphs is an effective technique for keeping the abstraction level consistent.

  * *A note on switch statements*

Try to avoid switch statements as much as possible - they violate the principle of functions only doing one thing.

  * *Use descriptive names*

Remember Ward’s principle: “You know you are working on clean code when each routine turns out to be pretty much what you expected.”

Don’t be afraid to make a name long. A long descriptive name is better than a short enigmatic name. A long descriptive name is better than a long descriptive comment.

  * *Function arguments*

The ideal number of arguments for a function is zero (niladic). Next comes one (monadic), followed closely by two (dyadic). Three arguments (triadic) should be avoided where possible. More than three (polyadic) requires very special justification — and then shouldn’t be used anyway.

Typical uses for monadic functions:

You may be asking a question about that argument, as in boolean `fileExists(“MyFile”)`. Or you may be operating on that argument, transforming it into something else and returning it. For example, `InputStream fileOpen(“MyFile”)` transforms a file name String into an InputStream return value. These two uses are what readers expect when they see a function.

A somewhat less common, but still very useful form for a single argument function, is an *event*. In this form there is an input argument but no output argument. The overall program is meant to interpret the function call as an event and use the argument to alter the state of the system, for example, `void passwordAttemptFailedNtimes(int attempts)`. Use this form with care. It should be very clear to the reader that this is an event. Choose names and contexts carefully.

Dyadic functions:

The more arguments we have the more complexity we introduce. Arguments have no order and so increase complications in remembering the order of the arguments.

We obivously sometimes need to use them, but we should always try to refactor them into monadic functions.

Triads:

Add complexity and harm readability.

Argument objects - where we need to pass in multiple arguemnts, consider refactoring them into an object. For example increase of

```
function loadSound(muted, preload) {};
loadSound(true, true);
```

we could instead write this as function

```
interface Settings {
  muted: boolean;
  preload: boolean;
}

loadSound(settings: Settings) {}
loadSound({muted: true, preload: true});
```

We have the benefit of having increased readability dramatically here. Sometimes we would want to refactor the arguments into a class of their own.

  * *Have no side effects*

Do not have side effects in your functions.

Example:

```
public class UserValidator {
  private Cryptographer cryptographer;
  public boolean checkPassword(String userName, String password) {
    User user = UserGateway.findByName(userName);
    if (user != User.NULL) {
      String codedPhrase = user.getPhraseEncodedByPassword();
      String phrase = cryptographer.decrypt(codedPhrase, password);
      if ("Valid Password".equals(phrase)) {
        Session.initialize();
        return true;
      }
    }
    return false;
  }
}
```

`Session.initialize()` is a side effect of this function and should be avoided for the following reasons:

1. This could be unexpected to someone who wants to simply validate a user.
2. The name of the function does not indicate that it will initialize a session.
3. It creates a temporal coupling - checkPassword can now only be called when a session is ready to be initialized.
4. Also violates the *do one thing* directive.

  * *Output arguments*

Avoid output arguments in general to improve readability.

Example:

```
appendFooter(s)
```

It's not clear whether the function takes s as an input and appends it somwhere or whether s is passed to take the output of that function. This is better:

```
report.appendFooter()
```

  * *Command query separation*

Functions should either do something or answer something, but not both. Either your function should change the state of an object, or it should return some information about that object. Doing both often leads to confusion.

  * *Prefer Exceptions to Returning Error Codes*

Returning error codes and handling them in functions leads to deeply nested strcutures. Use try catch blocks instead.

Functions should do one thing. Error handing is one thing. Thus, a function that handles errors should do nothing else.

  * *DRY*

Don't repeat yourself, obviously...
