---
title: C + + 中的属性 |Microsoft Docs
ms.custom: ''
ms.date: 06/01/2018
ms.topic: language-reference
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c573f3e170929df1b988bf3e74535dd12b83a2f8
ms.sourcegitcommit: f7703076b850c717c33d72fb0755fbb2215c5ddc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/28/2018
ms.locfileid: "43131794"
---
# <a name="attributes-in-c"></a>C++ 中的属性

C++ 标准定义的一组特性，并允许编译器供应商来定义其自己的属性 （在某个特定于供应商命名空间），但编译器所需识别只有标准中定义的属性。

在某些情况下，标准属性与特定于编译器 declspec 参数相重叠。 在 Visual C++ 中，你可以使用`[[deprecated]]`属性而不是使用`declspec(deprecated)`和属性将由任何符合的编译器识别。 所有其他 declspec 参数如 dllimport 和 dllexport，目前还没有特性等效项因此必须继续使用 declspec 语法。 属性不会影响类型系统中，并且它们不会更改程序的含义。 编译器忽略它们无法识别的属性值。

**Visual Studio 2017 版本 15.3 及更高版本**(适用于[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)): 在属性列表的范围内，可以指定所有名称的命名空间使用单个**使用**引导：

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

属性表示 #pragma 指令，__declspec() （Visual C++），例如供应商特定扩展的标准化的替代或 & #95; & #95; 属性 & #95; & #95;(GNU)。 但是，仍需要使用特定于供应商的构造在大多数情况。 标准当前指定符合编译器应识别的下列属性：

- `[[noreturn]]` 指定一个函数永远不会返回;换而言之，它总是引发异常。 编译器可以调整其编译规则`[[noreturn]]`实体。

- `[[carries_dependency]]` 指定该函数将传播数据依赖项排序方面线程同步。 该特性可以应用到一个或多个参数，以指定传入的参数传送到函数体的依赖项。 该特性可以应用于函数自身，以指定返回值包含函数的依赖项。 编译器可以使用此信息来生成更高效的代码。

- `[[deprecated]]` **Visual Studio 2015 及更高版本：** 指定函数不应使用，但可能不存在在将来版本的库界面。 编译器可以使用此客户端代码尝试调用函数时生成一条信息性消息。 可以应用于类、 typedef 名称、 变量、 非静态数据成员、 函数、 命名空间、 枚举、 一个枚举器或模板专用化的声明。  

- `[[fallthrough]]`**2017年及更高版本的 visual Studio:** (适用于[/std:C++ 17](../build/reference/std-specify-language-standard-version.md))`[[fallthrough]]`的上下文中可以使用属性[切换](switch-statement-cpp.md)语句作为对的提示编译器 （或任何人阅读代码） 是旨在 fallthrough 行为。 Visual C++ 编译器当前不会警告 fallthrough 行为，因此此特性没有任何效果编译器行为。

- `[[nodiscard]]`**15.3 及更高版本的 visual Studio 2017:** (适用于[/std:C++ 17](../build/reference/std-specify-language-standard-version.md)) 指定函数的返回值不应被丢弃。 引发警告 C4834，在此示例中所示：

   ```cpp
   [[nodiscard]]
   int foo(int i) { return i * i; }

   int main()
   {
       foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
       return 0;
   }
   ```

- `[[maybe_unused]]`**15.3 及更高版本的 visual Studio 2017:** (适用于[/std:C++ 17](../build/reference/std-specify-language-standard-version.md)) 指定的变量，函数，类，typedef、 非静态数据成员、 枚举类型或模板专用化可能特意不使用。 实体标记时，编译器不会警告`[[maybe_unused]]`不使用。 如果没有属性声明的实体可以更高版本被重新声明具有属性，反之亦然。 实体被视为标记分析标记其第一个声明后，并在当前翻译单元的翻译的其余部分。

## <a name="microsoft-specific-attributes"></a>Microsoft 特定的属性

- `[[gsl::suppress(rules)]]` 用于取消强制执行的检查器中的警告使用此特定于 Microsoft 的特性[准则支持库 (GSL)](https://github.com/Microsoft/GSL)在代码中的规则。 例如，考虑此代码片段：

    ```cpp
    void main()
    {
        int arr[10]; // GSL warning 26494 will be fired
        int* p = arr; // GSL warning 26485 will be fired
        [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1
        {
            int* q = p + 1; // GSL warning 26481 suppressed
            p = q--; // GSL warning 26481 suppressed
        }
    }
    ```

   该示例将引发这些警告：

   - 26494 (类型规则 5： 始终初始化对象。)

   - 26485 (边界规则 3： 组到指针的衰减。)

   - 26481 (边界规则 1： 请勿使用指针算法。 改为使用 span。）

   当使用 CppCoreCheck 代码分析工具安装和激活编译此代码时，将触发前两个警告。 但第三条警告，因属性而不会激发。 你可以在不包括特定的规则数的情况下编写 [[gsl::suppress(bounds)]] 来取消显示整个边界配置文件。 C++ 核心准则旨在帮助你编写更好、 更安全的代码。 禁止显示属性，可以轻松若要关闭的警告，它们都并不需要时。