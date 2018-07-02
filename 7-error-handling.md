# Error handling

Error handling is important, but if it obscures logic, it’s wrong.

* *Use Exceptions Rather Than Return Codes*

Returning error codes and not separating out error logic can lead to cluttered methods. Try separating out and try and catch parts of methods into their own methods. Exampl:

```
public class DeviceController {
  public void sendShutDown() {
    try {
      tryToShutDown();
    } catch (DeviceShutDownError e) {
      logger.log(e);
    }
  }
  ...
}
```

Notice how much cleaner it is. This isn’t just a matter of aesthetics. The code is better because two concerns that were tangled, the algorithm for device shutdown and error handling, are now separated. You can look at each of those concerns and understand them independently.

* *Write Your Try-Catch-Finally Statement First*

* *Provide Context with Exceptions*

Each exception that you throw should provide enough context to determine the source and location of an error. In Java, you can get a stack trace from any exception; however, a stack trace can’t tell you the intent of the operation that failed.

Create informative error messages and pass them along with your exceptions. Mention the operation that failed and the type of failure. If you are logging in your application, pass along enough information to be able to log the error in your catch.