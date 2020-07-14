# I. JavaScript Foundation

## JavaScript Engine

### What is it?

The machine to translate JavaScript files into machine code that the computer understands, e.g. the V8 Engine by Google written in C++.

### Inside the Engine

* Lexical Analysis \(break the code into a series of tokens\)
* Forming Abstract Syntax Tree \(the AST\)
* Interpreter -&gt; Byte Code
* Interpreter -&gt; Profiler -&gt; Compiler -&gt; Optimized Code

**The interpreter** translates code line-by-line on the fly. It can be quick to get up running. However, it can get really slow if not optimized.

**The compiler**, however, creates a translation and compiles down to a result \(lower-level code\) which can be understood by the machine. It can be slow since it should go through the code first, but the compiled result might be optimized and simplified.

### JIT Compiler \(Just-in-time Compiler\)

Combine both compiler and interpreter into the design. The profiler between the interpreter and the compiler acted like a monitor which inspects the interpreted result and let the compiler to optimize the result.

The final result will be that the JavaScript code will gradually be more efficient as the optimization goes by.

Knowing how the compiler optimizes the code, we can reversely write efficient code in advance.

## Writing Optimized Code

### Cautious About Syntax

Be really careful about these:

* `eval()` function
* `arguments`
* the `for...in...` loop \(use `Object.keys` as an alternative\)
* `with` keyword
* `delete` keyword

### Inline Caching



### Hidden Classes

