### 1. **`getch()` 不是标准 C++ 函数**

`getch()` 是 **conio.h** 库中的一个函数，通常用于控制台程序中接受用户输入。它并不属于 C++ 标准库，因此，很多现代编译器默认不包含它。

#### 解决方法：

你可以通过以下方式来替代 `getch()`：

- 使用 **`_getch()`**（适用于 MSVC 编译器和部分环境）。
- 使用 **`cin.get()`** 来等待用户输入，`cin.get()` 会在用户按下回车键时继续执行。

### 2. **使用 `_getch()` 代替 `getch()`**

如果你使用的是 **Visual Studio** 或 **MinGW**，有时 `_getch()`（下划线前缀）会有效，因为它是 Visual Studio 中的扩展函数。你可以尝试替换 `getch()` 为 `_getch()`。

```cpp
#include <graphics.h>
#include <conio.h>  // 包含 conio.h 头文件

int main() {
    initgraph(640, 480);
    outtextxy(100, 100, "Press any key to exit...");

    // 使用 _getch() 来等待用户输入
    _getch();

    closegraph();
    return 0;
}
```

如果你使用 MinGW 编译器并且 `getch()` 无法工作，可以尝试改用 `_getch()`。

### 3. **使用 `cin.get()` 代替 `getch()`**

如果你不想依赖任何外部库，最简单的解决方案是使用 **`cin.get()`** 来替代 `getch()`。`cin.get()` 会等待用户按下回车键后继续执行。

```cpp
#include <graphics.h>
#include <iostream>

int main() {
    initgraph(640, 480);
    outtextxy(100, 100, "Press Enter to exit...");

    // 使用 cin.get() 来等待用户按下回车键
    std::cin.get();

    closegraph();
    return 0;
}
```

这种方法是标准的 C++ 方法，兼容大部分编译器，并且不依赖于任何非标准库。

### 4. **检查编译器配置**

有时，`getch()` 不工作是因为你的编译器没有启用对 `conio.h` 的支持。你可以通过以下方法来确认并解决：

#### 4.1 **对于 MinGW（GCC）**

MinGW 本身并不包含 `conio.h`，因此你无法直接使用 `getch()`。你可以改为使用 `cin.get()` 来代替。

#### 4.2 **对于 Visual Studio（MSVC）**

如果你在 Visual Studio 中编译程序，`conio.h` 和 `getch()` 是支持的。确保你正确包含了 `conio.h` 头文件，像这样：

```cpp
#include <graphics.h>
#include <conio.h>

int main() {
    initgraph(640, 480);
    outtextxy(100, 100, "Press any key to exit...");

    // 使用 getch() 来等待用户输入
    getch();  

    closegraph();
    return 0;
}
```

### 5. **不使用等待输入（自动关闭）**

如果你不希望使用 `getch()` 等待输入，也可以考虑在一定时间后自动关闭图形窗口。你可以使用 **`Sleep()`** 来暂停一定时间，或者使用图形库的 **`delay()`** 函数（但 `delay()` 在某些环境下可能不可用）。

```cpp
#include <graphics.h>
#include <windows.h>  // 包含 Windows 的 Sleep() 函数

int main() {
    initgraph(640, 480);
    outtextxy(100, 100, "This window will close in 3 seconds.");

    // 等待 3000 毫秒（3 秒）后关闭窗口
    Sleep(3000);

    closegraph();
    return 0;
}
```

在这个示例中，程序会在 3 秒后自动关闭图形窗口，不需要用户输入。

------

### 总结

- **如果你的 `getch()` 不工作，最常见的原因是编译器不支持 `conio.h`。**
- 你可以使用 **`_getch()`** 代替，或者更推荐使用标准的 **`cin.get()`** 来等待用户输入。
- 另外，也可以通过 **`Sleep()`** 等方法控制窗口的自动关闭时间。