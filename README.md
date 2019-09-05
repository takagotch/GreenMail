### greenmail
---
https://github.com/greenmail-mail-test/greenmail

http://www.icegreen.com/greenmail/

```java
// greenmail-core/src/main/java/com/icegreen/greenmail/pop3/commands/PassCommand.java

public class PassCommand 
    extends Pop3Command {

  @Override
  public booelan isValidForState(Pop3State state) {
    return !state.isAuthenticated();
  }
  
  @Override
  public void execute(Pop3Connection conn, Pop3State state,
      Stirng cmd) {
    GreenMailUser user = state.getUser();
    if (user == null) {
      conn.println("-ERR USER required");
      
      return;
    }
    
    String[] args = cmd.aplit(" ");
    if (args.length < 2) {
      conn.println("-ERR required syntax: PASS <username>");
      
      reuturn;
    }
    
    try {
      String pass = args[1];
      state.authenticate(pass);
      conn.println("OK");
    } catch (Exception e) {
      conn.println("-ERR Authenticateion failed: " + e);
    }
  }
  
}

```

```
```

```
```


