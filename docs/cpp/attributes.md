---
title: C + + 中的特性
ms.date: 05/06/2019
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
ms.openlocfilehash: efdc62e2343135aee483520f633bac99519455b4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229202"
---
# <a name="attributes-in-c"></a>C + + 中的特性

C + + 标准定义了一组属性，还允许编译器供应商定义其自己的属性（在特定于供应商的命名空间中），但编译器只需要识别在标准中定义的属性。

在某些情况下，标准属性与特定于编译器的 declspec 参数重叠。 在 Visual C++ 中，可以使用 `[[deprecated]]` 属性，而不是使用 `declspec(deprecated)` ，任何符合的编译器都将识别属性。 对于所有其他 declspec 参数（如 dllimport 和 dllexport），尚无等效属性，因此必须继续使用 declspec 语法。 属性不影响类型系统，并且不会更改程序的含义。 编译器将忽略它们无法识别的特性值。

**Visual Studio 2017 版本15.3 及更高版本**（可用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）：在属性列表的作用域中，可以使用单个引导指定所有名称的命名空间 **`using`** ：

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>C + + 标准特性

在 c + + 11 中，特性提供了一种标准化的方法，用于批注 c + + 构造（包括但不限于类、函数、变量和块）以及可能或不可能是特定于供应商的其他信息。 编译器可以使用此信息来生成信息性消息，或在编译特性化代码时应用特殊逻辑。 编译器会忽略它无法识别的任何属性，这意味着您不能使用此语法定义您自己的自定义属性。 属性用双方括号括起来：

```cpp
[[deprecated]]
void Foo(int);
```

属性表示特定于供应商的扩展的标准化替代项，例如 #pragma 指令、__declspec （）（Visual C++）或 &#95;&#95;特性&#95;&#95;  （GNU）。 但是，您仍需要出于大多数目的使用特定于供应商的构造。 标准版当前指定了符合一致性的编译器应识别的下列属性：

- `[[noreturn]]`指定函数从不返回;换句话说，它总是引发异常。 编译器可以调整实体的编译规则 `[[noreturn]]` 。

- `[[carries_dependency]]`指定该函数将传播与线程同步相关的数据依赖项排序。 特性可应用于一个或多个参数，以指定传入的参数将依赖项传递到函数体中。 特性可应用于函数本身，以指定返回值将依赖项移出函数。 编译器可使用此信息生成更高效的代码。

- `[[deprecated]]`**Visual Studio 2015 及更高版本：** 指定不打算使用某个函数，并且该函数可能不存在于库接口的未来版本中。 当客户端代码尝试调用函数时，编译器可以使用此功能生成信息性消息。 可应用于类的声明、typedef 名称、变量、非静态数据成员、函数、命名空间、枚举、枚举器或模板特殊化。

- `[[fallthrough]]`**Visual Studio 2017 及更高版本：** （可与[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)一起使用） `[[fallthrough]]` 属性可以在[switch](switch-statement-cpp.md)语句的上下文中用作对编译器（或任何读取代码的人）的提示，以指示 fallthrough 行为的行为。 Microsoft c + + 编译器当前不会对 fallthrough 行为发出警告，因此此属性不会影响编译器行为。

- `[[nodiscard]]`**Visual Studio 2017 版本15.3 及更高版本：** （与[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)一起提供）指定不应丢弃函数的返回值。 引发警告 C4834，如以下示例中所示：

    ```cpp
    [[nodiscard]]
    int foo(int i) { return i * i; }

    int main()
    {
        foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
        return 0;
    }
    ```

- `[[maybe_unused]]`**Visual Studio 2017 版本15.3 及更高版本：** （与[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)一起提供）指定变量、函数、类、typedef、非静态数据成员、枚举或模板特殊化可能不会被有意使用。 当未使用标记的实体时，编译器不会发出警告 `[[maybe_unused]]` 。 稍后可使用属性重新声明未使用特性声明的实体，反之亦然。 在分析标记的第一个声明后，或在当前翻译单元的其余翻译中，实体被视为标记。

## <a name="microsoft-specific-attributes"></a>特定于 Microsoft 的属性

- `[[gsl::suppress(rules)]]`此特定于 Microsoft 的属性用于禁止在代码中强制执行[准则支持库（GSL）](https://github.com/Microsoft/GSL)规则的跳棋中出现警告。 例如，考虑以下代码片段：

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

  当你在安装和激活 CppCoreCheck 代码分析工具的情况下编译此代码时，将激发前两个警告。 但由于属性的原因，第三个警告不会激发。 您可以通过编写 [[gsl：：抑制（边界）]] 来禁止整个边界配置文件，而无需包含特定的规则号。 C++ Core Guidelines 旨在帮助你编写更好、更安全的代码。 "取消" 属性可在不需要时关闭警告。
  