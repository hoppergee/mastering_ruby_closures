Chapter 1 - Note

A closure is a function whose body references a variable that is declared in the parent scope.

**Lexical scoping rule** serve to answer a question: what is the value of this variable at this line?

**Scope of variable** is the area where a variable maintains a value.

**Free variable** is a variable that is defined in a parent scope.

Lambdas are Ruby's version of anonymous function.

The parent scope is also called the surrounding lexical scope.

Free variable is the key point of the **closure**.

The advantage of implement class with lambda:

  * Prevent private variable leak out.
  * Prevent method been override.

Closure restrict access to the variables they wrap.
