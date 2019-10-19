# Chapter 3 - Note

Block are not object.

Proc and lambda are both object.

lambda is a kind of Proc. lambda's class is Proc.

**Four ways to call Proc**

1. `Proc#call()`
2. `.(arg)()` i.e. `Run.()` is equal to `Run.call()`
3. Threequals `===`, it make the proc can be used with `case when`
4. lambada

`Proc#lambda?()` can be used to check whether it's a lambda or a proc.

**Difference between Proc and lambda**

1. arity
  * lambda will check the input arguments number
2. `return` semantics
  * Proc always return from the scope it was declared.

`[1,2,3].map(&:to_s)` is just use the magic method `:to_proc`. We can use this strategy by add `to_proc` method to any object we want to put as the map method argument with the proc convert `&` operator.

`Proc#curry` Currying is the process of turning a function that takes n arguments into one that takes a single argument, but returns n functions that take one argument.



