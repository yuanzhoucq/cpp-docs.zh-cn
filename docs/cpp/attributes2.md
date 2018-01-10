---
title: "C + + 标准属性 |Microsoft 文档"
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 748340d9-8abf-4940-b0a0-91b6156a3ff8
caps.latest.revision: "11"
manager: ghogen
ms.openlocfilehash: d2dcce6b0e289588c426792a334ee4ec38d1ab5f
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2017
---
# <a name="attributes-in-c"></a>C + + 中的属性

C + + 标准定义的一组特性，并允许编译器供应商来定义其自己的属性 （在某个特定于供应商命名空间），但编译器所需识别只有标准中定义的属性。

在某些情况下，标准属性与特定于编译器 declspec 参数相重叠。 在 Visual c + + 中，你可以使用`[[deprecated]]`属性而不是使用`declspec(deprecated)`和属性将由任何符合的编译器识别。 所有其他 declspec 参数如 dllimport 和 dllexport，目前还没有特性等效项因此必须继续使用 declspec 语法。 属性不会影响类型系统中，并且它们不会更改程序的含义。 编译器忽略它们无法识别的属性值。

**Visual Studio 2017 15.3 及更高版本**(适用于[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): 在范围内的属性列表中,，你可以指定所有名称的命名空间与单个`using`引导：

```cpp
void g() {
    [[using rpr: kernel, target(cpu,gpu)]] // equivalent to [[ rpr::kernel, rpr::target(cpu,gpu) ]]
    do task();
}
```

## <a name="c-standard-attributes"></a>C + + 标准属性

在 C + + 11 中，属性提供一种标准化的方法添加批注的其他信息，也可能不是特定于供应商的 c + + 构造 （包括但不是限于类、 函数、 变量和块）。 用于生成信息性消息，或应用特殊逻辑，编译特性化的代码时，编译器可以使用此信息。 编译器将忽略无法识别，任何属性这意味着你不能定义自己自定义属性，使用此语法。 属性将由双方括号括：

```cpp
[[deprecated]]
void Foo(int);
```

属性表示 #pragma 指令，__declspec() （Visual c + +），例如供应商特定扩展的标准化的替代或 &#95; &#95; 属性 &#95; &#95;(GNU)。 但是，你将仍需要在大多数情况下使用的特定于供应商构造。 标准当前指定的一致编译器应认识到的下列属性：

- `[[noreturn]]`指定，则函数将永远不会返回;换而言之，它总是引发异常。 编译器可以调整其编译规则`[[noreturn]]`实体。

- `[[carries_dependency]]`指定该函数将传播排序方面线程同步的数据依赖项。 特性可以应用于一个或多个参数，以指定传入的参数传送到函数体的依赖项。 特性可以应用于该函数本身，以指定返回的值会带来跳出函数依赖关系。 编译器可以使用此信息来生成更高效的代码。

- `[[deprecated]]`**Visual Studio 2015 及更高版本：**指定函数并非旨在使用，并且可能不存在在将来版本的库接口。 编译器可以使用此客户端代码尝试调用函数时生成一条信息性消息。 可以应用于声明的类、 typedef 名称、 变量、 非静态数据成员、 函数、 命名空间、 枚举、 枚举数或模板专用化。  

- `[[fallthrough]]`**2017年及更高版本的 visual Studio:** (适用于[/std:c + + 17](../build/reference/std-specify-language-standard-version.md))`[[fallthrough]]`的上下文中可以使用属性[切换](switch-statement-cpp.md)语句作为对的提示编译器 （或任何人阅读代码） 是旨在 fallthrough 行为。 Visual c + + 编译器当前不会警告 fallthrough 行为，因此此特性没有任何效果编译器行为。

- `[[nodiscard]]`**15.3 及更高版本的 visual Studio 2017:** (适用于[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)) 指定函数的返回值不应被丢弃。 引发警告 C4834，此示例中所示：

   ```cpp
   [[nodiscard]]
   int foo(int i) { return i * i; }

   int main()
   {
       foo(42); //warning C4834: discarding return value of function with 'nodiscard' attribute
       return 0;
   }
   ```

- `[[maybe_unused]]`**15.3 及更高版本的 visual Studio 2017:** (适用于[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)) 指定的变量，函数，类，typedef、 非静态数据成员、 枚举类型或模板专用化可能特意不使用。 实体标记时，编译器不会警告`[[maybe_unused]]`未使用。 如果没有该属性声明的实体可以更高版本能重新声明具有属性，反之亦然。 实体被视为标记分析标记其第一个声明后，并转换在当前翻译单元的其余部分。

## <a name="microsoft-specific-attributes"></a>Microsoft 特定的属性

- `[[gsl::suppress(rules)]]`用于此特定于 Microsoft 的特性禁止显示警告强制执行的检查器从[准则支持库 (GSL)](https://github.com/Microsoft/GSL)在代码中的规则。 例如，考虑此代码片段：

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

   该示例可引发以下警告：

   - 26494 (类型规则 5： 始终初始化的对象。)

   - 26485 (边界规则 3： 阵列没有到指针 decay。)

   - 26481 (边界规则 1： 不要使用指针算法。 改为使用 span。）

   当使用 CppCoreCheck 代码分析工具安装和激活编译此代码时，将触发前两个警告。 但第三条警告，因属性而不会激发。 你可以在不包括特定的规则数的情况下编写 [[gsl::suppress(bounds)]] 来取消显示整个边界配置文件。 C + + 核心准则旨在帮助你编写更好、 更安全的代码。 禁止显示属性，可以轻松若要关闭的警告，它们都并不需要时。
