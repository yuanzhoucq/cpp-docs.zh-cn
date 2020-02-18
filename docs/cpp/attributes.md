---
title: C++ 中的属性
ms.date: 05/06/2019
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: b3ed21b033c0e606d02d3aa845f09f72118a3c5e
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416076"
---
# <a name="attributes-in-c"></a>C++ 中的属性

C++ 标准定义的一组特性，并允许编译器供应商来定义其自己的属性 （在某个特定于供应商命名空间），但编译器所需识别只有标准中定义的属性。

在某些情况下，标准属性与特定于编译器 declspec 参数相重叠。 在视觉C++对象中，可以使用 `[[deprecated]]` 特性，而不是使用 `declspec(deprecated)`，任何符合的编译器都将识别属性。 所有其他 declspec 参数如 dllimport 和 dllexport，目前还没有特性等效项因此必须继续使用 declspec 语法。 属性不会影响类型系统中，并且它们不会更改程序的含义。 编译器忽略它们无法识别的属性值。

**Visual Studio 2017 版本15.3 及更高版本**（可用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）：在属性列表的作用域中，可以**使用**引导指定所有名称的命名空间：

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>C++ 标准属性

在 C++ 11 中，属性提供一种标准化的方法添加批注的其他信息，也可能不是特定于供应商的 C++ 构造 （包括但不是限于类、 函数、 变量和块）。 用于生成信息性消息，或应用特殊逻辑，编译特性化的代码时，编译器可以使用此信息。 编译器将忽略无法识别，任何属性这意味着你不能定义自己自定义属性，使用此语法。 属性将由双方括号括：

```cpp
[[deprecated]]
void Foo(int);
```

属性表示 #pragma 指令，__declspec() （Visual C++），例如供应商特定扩展的标准化的替代或 &#95; &#95; 属性 &#95; &#95; (GNU)。 但是，仍需要使用特定于供应商的构造在大多数情况。 标准版当前指定了符合一致性的编译器应识别的下列属性：

- `[[noreturn]]` 指定函数从不返回;换句话说，它总是引发异常。 编译器可以为 `[[noreturn]]` 实体调整其编译规则。

- `[[carries_dependency]]` 指定该函数将传播与线程同步相关的数据依赖关系排序。 特性可应用于一个或多个参数，以指定传入的参数将依赖项传递到函数体中。 特性可应用于函数本身，以指定返回值将依赖项移出函数。 编译器可使用此信息生成更高效的代码。

- `[[deprecated]]` **Visual Studio 2015 及更高版本：** 指定不应使用某个函数，并且该函数可能不存在于库接口的未来版本中。 当客户端代码尝试调用函数时，编译器可以使用此功能生成信息性消息。 可应用于类的声明、typedef 名称、变量、非静态数据成员、函数、命名空间、枚举、枚举器或模板特殊化。

- `[[fallthrough]]` **Visual Studio 2017 及更高版本：** （可与[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)一起使用），`[[fallthrough]]` 属性可以在[switch](switch-statement-cpp.md)语句的上下文中用作对编译器（或读取代码的任何人）的提示。 Microsoft C++编译器当前不会对 fallthrough 行为发出警告，因此此属性不会影响编译器行为。

- `[[nodiscard]]` **Visual Studio 2017 版本15.3 及更高版本：** （可用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）指定函数的返回值不应被丢弃。 引发警告 C4834，如以下示例中所示：

    ```cpp
    [[nodiscard]]
    int foo(int i) { return i * i; }

    int main()
    {
        foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
        return 0;
    }
    ```

- `[[maybe_unused]]` **Visual Studio 2017 版本15.3 及更高版本：** （与[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)一起提供）指定变量、函数、类、typedef、非静态数据成员、枚举或模板特殊化可能不会被有意使用。 当未使用标记为 `[[maybe_unused]]` 的实体时，编译器不会发出警告。 稍后可使用属性重新声明未使用特性声明的实体，反之亦然。 在分析标记的第一个声明后，或在当前翻译单元的其余翻译中，实体被视为标记。

## <a name="microsoft-specific-attributes"></a>特定于 Microsoft 的属性

- `[[gsl::suppress(rules)]]` 此特定于 Microsoft 的属性用于禁止在代码中实施[指导原则支持库（GSL）](https://github.com/Microsoft/GSL)规则的跳棋中出现警告。 例如，考虑以下代码片段：

    ```cpp
    int main()
    {
        int arr[10]; // GSL warning C26494 will be fired
        int* p = arr; // GSL warning C26485 will be fired
        [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
        {
            int* q = p + 1; // GSL warning C26481 suppressed
            p = q--; // GSL warning C26481 suppressed
        }
    }
    ```

  该示例引发了以下警告：

  - 26494（类型规则5：始终初始化对象。）

  - 26485（边界规则3：没有数组到指针的衰减。）

  - 26481（边界规则1：不要使用指针算法。 请改用跨距。）

  当使用 CppCoreCheck 代码分析工具安装和激活编译此代码时，将触发前两个警告。 但第三条警告，因属性而不会激发。 你可以在不包括特定的规则数的情况下编写 [[gsl::suppress(bounds)]] 来取消显示整个边界配置文件。 C++ 核心准则旨在帮助你编写更好、 更安全的代码。 禁止显示属性，可以轻松若要关闭的警告，它们都并不需要时。
  