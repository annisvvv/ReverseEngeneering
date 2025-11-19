The `switch` statement in C is a control flow statement that allows for multi-way branching based on the value of an expression. It provides an alternative to using a series of `if-else if` statements when comparing a single variable against multiple constant values.

The basic syntax of a `switch` statement is:
```
switch (expression) {    case constant_value_1:        // code to be executed if expression matches constant_value_1        break; // Optional: exits the switch statement    case constant_value_2:        // code to be executed if expression matches constant_value_2        break; // Optional: exits the switch statement    // ... more cases    default: // Optional: executed if no case matches        // code to be executed if no case matches        break; // Optional: not strictly necessary after default}
```

### Equivalent to asm
