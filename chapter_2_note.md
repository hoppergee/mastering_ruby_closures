# Chapter 2 - Note

Blocks are effectively a type of closure. They just act anonymous functions.

Blocks carry
  * a bunch of code
  * the context which it was defined

`yield`'s argument-passing behavior: missing arguments will be set to nil, and extra arguments will be silently discarded. (be called parallel assignment behavior)

Block patterns: enumeration, managing resource, object initialization

Key things about closure for DSL:

  * In a block, `self()` is in the context where the block was defined.
  * If you want to change the `self()`'s scope, you should tell ruby to evaluate other context
    * use `instance_eval` to replace `yield`
      * Example: `instance_eval(&block)`

**Block-to-Proc Conversion**

1. *Block -> Proc* if `&block` is in a method argument
2. *Proc -> Block* if `&block` is in method body