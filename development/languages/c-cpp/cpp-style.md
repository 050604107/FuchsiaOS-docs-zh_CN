C++ style guide
===============

The Fuchsia project follows the [Google C++ style guide][google-guide], with a
few exceptions.

By policy, code should be formatted by clang-format which should handle many
decisions.

### Exceptions

#### Braces

Always use braces `{ }` when the contents of a block are more than one line.
This is something you need to watch since Clang-format doesn't know to add
these.

```cpp
// Don't do this.
while (!done)
  doSomethingWithAReallyLongLine(
       wrapped_arg);

// Correct.
while (!done) {
  doSomethingWithAReallyLongLine(
       wrapped_arg);
}
```


#### Conditionals and loops

Do not use spaces inside parentheses (the Google style guide discourages but
permits this).

Do not use the single-line form for short conditionals and loops (the Google
style guide permits both forms):

```cpp
// Don't do this:
if (x == kFoo) return new Foo();

// Correct.
if (x == kFoo)
  return new Foo
```

#### Namespace Names

* Nested namespaces are forbidden, with the following exceptions:
  - `internal` (when required to hide implementation details of templated code)
  - code generated by the FIDL compiler
* The following top-level namespaces are forbidden:
  - `internal`
  - `fuchsia` (except in code generated by the FIDL compiler)
* Namespaces in SDK libraries must be kept to as short a list as possible.
  A later document will provide an explicit list of allowed namespaces; in the
  meantime, new namespaces should be introduced thoughtfully.
* Namespaces in non-SDK libraries should also be chosen so as to reduce the risk
  of clashes. Very generic nouns (eg. `media`) are best avoided.

Rationale: [Tip of the Week #130: Namespace Naming][totw-130]

[google-guide]: https://google.github.io/styleguide/cppguide.html
[totw-130]: https://abseil.io/tips/130