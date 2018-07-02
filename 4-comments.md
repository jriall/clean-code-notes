# Comments

Nothing can be quite so helpful as a well-placed comment. Nothing can clutter up a module more than frivolous dogmatic comments. Nothing can be quite so damaging as an old crufty comment that propagates lies and misinformation. Comments are not like Schindler’s List. They are not “pure good.” Indeed, comments are, at best, a necessary evil. If our programming languages were expressive enough, or if we had the talent to subtly wield those languages to express our intent, we would not need comments very much—perhaps not at all. The proper use of comments is to compensate for our failure to express ourself in code.

*Examples of good comments:*

1. Legal or licence comments.

2. Informative comments which express something which is difficult or impossible to do in code.

Example:

```
// format matched kk:mm:ss EEE, MMM dd, yyyy
Pattern timeMatcher = Pattern.compile(
    "\\d*:\\d*:\\d* \\w*, \\w* \\d*, \\d*");
```

3. Explanation of intent

Giving useful context to the intent behind a decision which was made in the code.

4. Clarification

Sometimes it is just helpful to translate the meaning of some obscure argument or return value into something that’s readable. In general it is better to find a way to make that argument or return value clear in its own right; but when its part of the standard library, or in code that you cannot alter, then a helpful clarifying comment can be useful.

5. Warning of consequences

For example, tests which will take a long time to run.

6. TODO comments

Use the format `// TODO:` and make sure to go back and clean them up regularly.

7. Amplification

A comment may be used to amplify the importance of something that may otherwise seem
inconsequential.

Example:

```
String listItemContent = match.group(3).trim();
// the trim is real important. It removes the starting
// spaces that could cause the item to be recognized
// as another list.
new ListItemWidget(this, listItemContent, this.level + 1);
return buildList(text.substring(match.end()));
```

*Examples of bad comments:*

1. Mumbling

Make sure your comments will be clear to other developers reading your code.

2. Redundant comments

Comments which are simply stating what we have expressed (or should express) in our code.

3. Misleading comments

Comments which don't exactly describe what a function or variable does. This can sometimes be caused by code being rewritten, but not the comments. Another reason to prefer expression in code instead of comments.

4. Mandated comments

It's a silly rule to enforce all functions/variables having a comment.

5. Journal comments

We have git for this.

6. Noise comments

Comments which restate the obvious.

7. Using comments when you could use a function or a variable.

Consider the following stretch of code:

```
// does the module from the global list <mod> depend on the
// subsystem we are part of?
if (smodule.getDependSubsystems().contains(subSysMod.getSubSystem()))
```
This could be rephrased without the comment as

```
ArrayList moduleDependees = smodule.getDependSubsystems();
String ourSubSystem = subSysMod.getSubSystem();
if (moduleDependees.contains(ourSubSystem))
```

The author of the original code may have written the comment first (unlikely) and then written the code to fulfill the comment. However, the author should then have refactored the code, as I did, so that the comment could be removed.

8. Commenting out code

Do not leave commented out code in your codebase.

9. HTML comments

Leave them our. We have all the tools in HTML to semantically express our code structure, so comments are unnecessary.

10. Non-local information

Make sure all comments are placed as close as possible to the code they are commenting.

11. Too much information

12. Function headers

Just name the functions clearly.



