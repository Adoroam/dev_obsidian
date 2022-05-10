# C
Hello World Example
```C
#include <stdio.h>

int main(void) {
  printf("hello world\n");
}
```

`stdio.h` means "standard input/output"
C has many [standard libraries](https://en.cppreference.com/w/c/header) that you can import to save time and headaches on simple or common problems.

To template strings using `printf`, you can use `%s` and supply a second argument.
```C
printf("hello %s", some_var)
```
hello