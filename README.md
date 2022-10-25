# Terminal Helper

Simple library for having some fun with the terminal in Linux with C++.

Still alpha version. Can still contain bugs.

## Demo

Basic demo of "curly-pacman":

```cpp
#include <iostream>
#include <chrono>
#include <thread>
#include "terminal.h"

using namespace std;
using namespace Bios;

int main() {

  Terminal::clear();
  Terminal::hide_cursor();
  Terminal::background_color("white");
  Terminal::foreground_color("blue", true);

  for (int i = 0; i < 10; i++) {

    Terminal::move_cursor(5, 5);
    printf("}");
    Terminal::flush();
    std::this_thread::sleep_for(500ms);

    Terminal::move_cursor(5, 5);
    printf(">");
    Terminal::flush();
    std::this_thread::sleep_for(500ms);

  }

  Terminal::show_cursor();
  Terminal::reset_background_color();
  Terminal::reset_foreground_color();
  Terminal::clear();

  return 0;
}
```

Compile with:

```bash
g++ main.cpp terminal.cpp -o fun
```