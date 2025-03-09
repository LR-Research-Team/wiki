## ``fake.White``
!!! note
   
    These functions can be accessed by using ``import fake.White``.

### compareString

Compares two strings and returns `1` if equal, and `0` if not equal.

**Parameter(s) :**

* String var0 : first string to compare
* String var1 : second string to compare

```java
public static native int compareString(String var0, String var1);
```

## ``fld.com``
!!! note

    These functions can be accessed by using ``import fld.com``.

### sfShowWindowWithKeyWait

Displays a message window that can be closed on user input. the function will always return `-1`.<br>

**Parameter(s) :**

* String string : message to display

```java
public static int sfShowWindowWithKeyWait(String string) { 

}
```

### sfCallAskChoiceWindow

Draws a message window with options. the function will return the message window id.<br>

**Parameter(s) :**

* String string : title of the message window
* String[] stringArray : options to display
* int n : index where the cursor should default to, after the last option

```java
public static int sfCallAskChoiceWindow(String string, String[] stringArray, int n) { 

}
```

### sfWaitAskChoiceWindow

Makes an options window, interactable. this has to be used after the sfCallAskChoiceWindow function is used and the function will return the **selected** option's index.<br>

**Parameter(s) :**

* String string : title used for the options window. 

```java
public static int sfWaitAskChoiceWindow(String string) {

}
```

