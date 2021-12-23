This project offers a `sal.h` that disables all [SAL annotations][SAL] defined
by the original `sal.h` contained in Microsoft Visual Studio’s CRT library.

Using this header, instead of the original, renders all static analysis tools,
depending on valid SAL annotations in C and C++ code, useless.

# Why

Some libraries, like [DirectX Math][DXM], needs `sal.h` to be included.
Including the original, which is only available on Windows (SDK), is either not
possible or doing so leads compiler errors in GCC and Clang.

Unless your project code uses SAL annotations, it should be safe to disable it
in third-party code.


[SAL]: https://docs.microsoft.com/en-us/cpp/c-runtime-library/sal-annotations
[DXM]: https://github.com/Microsoft/DirectXMath
