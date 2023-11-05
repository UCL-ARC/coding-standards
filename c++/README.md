# C++

C++ and C code should conform to the [Google coding conventions](https://google.github.io/styleguide/cppguide.html) in terms of variable names and layout.

We will use modern C++ features - including range-based for loops and lambda expressions - where this improves readability.
This means we prefer to work with [C++11](](http://en.wikipedia.org/wiki/C++11)), [C++17](http://en.wikipedia.org/wiki/C++17), or newer.

We use the [clang-tidy](https://clang.llvm.org/extra/clang-tidy/) linter configured to obey Google style.
That is:

```sh
clang-tidy  --format-style='google'
```

We also recommend using [cppcheck](https://github.com/cpplint/cpplint), a [static analyser](https://en.wikipedia.org/wiki/Static_program_analysis). It can be helpful to improve code quality in general.

Our preferred build system for C++ code projects is [CMake](https://cmake.org/).

## Further reading

* More pedagogical guidance can be found in C++ course, [PHAS0100: Research Computing with C++](https://github-pages.ucl.ac.uk/research-computing-with-cpp).
* [ISO C++ Core Guidelines](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines) - useful resource although less complete than Google's style.