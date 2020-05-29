---
title: MSVC 实验预处理器概述
description: MSVC 预处理器正在更新，以便符合 C/C++ 标准。
ms.date: 02/09/2020
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: 00c34ef75270e505d3781cf7eedf4d8aba95ee6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337482"
---
# <a name="msvc-experimental-preprocessor-overview"></a>MSVC 实验预处理器概述

::: moniker range="vs-2015"

Visual Studio 2015 使用传统的预处理器，这不符合标准C++。 使用[/实验前](../build/reference/experimental-preprocessor.md)处理器编译器开关，在 Visual Studio 2017 和 Visual Studio 2019 中提供了一个实验预处理器。 有关在 Visual Studio 2017 和 Visual Studio 2019 中使用新预处理器的详细信息，请访问。 要查看您首选版本的 Visual Studio 的文档，请使用**版本**选择器控件。 它位于此页面的目录顶部。

::: moniker-end

::: moniker range=">=vs-2017"

我们正在更新 Microsoft C++预处理器，以提高标准一致性、修复长期存在的 Bug 并更改一些正式未定义的行为。 我们还添加了新的诊断程序来警告宏定义中的错误。

这些更改可通过在 Visual Studio 2017 或 Visual Studio 2019 中使用[/实验前处理器](../build/reference/experimental-preprocessor.md)编译器开关。 默认预处理器行为与早期版本相同。

从 Visual Studio 2019 版本 16.5 开始，C++20 标准的实验预处理器支持已完成。

## <a name="new-predefined-macro"></a>新的预定义宏

您可以检测编译时正在使用的预处理器。 检查预定义的宏[\_MSVC\_传统](predefined-macros.md)值，以判断是否正在使用传统的预处理器。 此宏由支持它的编译器版本无条件设置，独立于调用预处理器的版本。 其值对于传统的预处理器为 1。 对于符合要求的预处理器，它是 0。

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>实验预处理器的行为变化

实验预处理器的初步工作重点是使所有宏扩展都符合标准。 它允许您将 MSVC 编译器与当前被传统行为阻止的库一起使用。 我们在真实项目中测试了更新的预处理器。 以下是我们发现的一些更常见的突发性更改：

### <a name="macro-comments"></a>宏注释

传统的预处理器基于字符缓冲区，而不是预处理器令牌。 它允许异常行为，如以下前处理器注释技巧，这在符合的预处理器下不起作用：

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

符合标准的修复程序是在相应的`int myVal``#ifdef/#endif`指令中声明：

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L_val

传统的预处理器错误地将字符串前缀与[字符串化运算符 （#）](stringizing-operator-hash.md)运算符的结果合并：

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

在这种情况下，前缀是`L`不必要的，因为相邻的字符串文本无论如何都在宏扩展后合并。 向后兼容的修复程序是更改定义：

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

在将参数"串"到宽字符串文本的便利宏中也发现了同样的问题：

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

您可以通过多种方式解决此问题：

- 使用 和`L""``#str`的字符串串联来添加前缀。 相邻的字符串文本在宏扩展后合并：

   ```cpp
   #define STRING1(str) L""#str
   ```

- 使用其他宏扩展`#str`字符串化后添加前缀

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- 使用串联运算符`##`组合令牌。 `##`和 的操作`#`顺序未指定，尽管在这种情况下，所有编译器似乎都在评估`#`运算符之前。 `##`

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>无效警告\#\#

当[令牌粘贴运算符 （#）](token-pasting-operator-hash-hash.md)不产生单个有效的预处理令牌时，该行为未定义。 传统的预处理器无法悄悄地组合令牌。 新的预处理器与大多数其他编译器的行为匹配，并发出诊断。

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>变异宏中的逗号消除

传统的 MSVC 前处理器始终在空`__VA_ARGS__`替换之前删除逗号。 实验前处理器更密切地遵循其他流行的跨平台编译器的行为。 要删除逗号，必须缺少可变参数（而不仅仅是空），并且必须用`##`运算符标记它。 请考虑以下示例：

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // In the traditional preprocessor, the
    // following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor replaces the
    // following macro with: func(1, ), which
    // results in a syntax error.
    FUNC(1, );
}
```

在下面的示例中，在调用的宏中`FUNC2(1)`缺少对可变参数的调用。 在调用`FUNC2(1, )`变量参数时为空，但不丢失（请注意参数列表中的逗号）。

```cpp
#define FUNC2(a, ...) func(a , ## __VA_ARGS__)
int main()
{
   // Expands to func(1)
   FUNC2(1);

   // Expands to func(1, )
   FUNC2(1, );
}
```

在即将出台的C++20标准中，此问题已通过添加`__VA_OPT__`得到解决。 Visual Studio 2019 版本 16.5 中提供了实验前处理器支持`__VA_OPT__`。

### <a name="c20-variadic-macro-extension"></a>C++20可变宏扩展

实验前处理器支持C++20变幻宏参数消除：

```cpp
#define FUNC(a, ...) __VA_ARGS__ + a
int main()
  {
  int ret = FUNC(0);
  return ret;
  }
```

此代码不符合 C++20 标准。 在 MSVC 中，实验前处理器将此C++20 行为扩展到较低的语言**`/std:c++14`** 标准**`/std:c++17`** 模式 （，）。 此扩展与其他主要跨平台C++编译器的行为匹配。

### <a name="macro-arguments-are-unpacked"></a>宏参数"解压缩"

在传统的预处理器中，如果宏将其参数之一转发到另一个从属宏，则在插入参数时不会"解压缩"。 通常，这种优化被忽视，但它可能导致异常行为：

```cpp
// Create a string out of the first argument, and the rest of the arguments.
#define TWO_STRINGS( first, ... ) #first, #__VA_ARGS__
#define A( ... ) TWO_STRINGS(__VA_ARGS__)
const char* c[2] = { A(1, 2) };

// Conforming preprocessor results:
// const char c[2] = { "1", "2" };

// Traditional preprocessor results, all arguments are in the first string:
// const char c[2] = { "1, 2", };
```

扩展`A()`时，传统的预处理器将所有打包的参数转发`__VA_ARGS__`到TWO_STRINGS的第一个参数，从而留下空的`TWO_STRINGS`可变参数。 这将导致结果`#first`为"1，2"，而不仅仅是"1"。 如果你紧随其后，那么您可能想知道传统前处理器扩展的结果`#__VA_ARGS__`发生了什么：如果变量参数为空，则应该导致一个空字符串文本。 `""` 另一个问题阻止生成空字符串文本令牌。

### <a name="rescanning-replacement-list-for-macros"></a>重新扫描宏的替换列表

替换宏后，将重新扫描生成的令牌以替换其他宏标识符。 传统的预处理器用于进行再扫描的算法不符合，如本示例中基于实际代码所示：

```cpp
#define CAT(a,b) a ## b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)

// MACRO chooses the expansion behavior based on the value passed to macro_switch
#define DO_THING(macro_switch, b) CAT(IMPL, macro_switch) ECHO(( "Hello", b))
DO_THING(1, "World");

// Traditional preprocessor:
// do_thing_one( "Hello", "World");
// Conforming preprocessor:
// IMPL1 ( "Hello","World");
```

尽管此示例看起来有点精心设计，但我们在真实世界代码中看到了它。 为了了解发生了什么，我们可以从 以下开始分解扩展`DO_THING`：

1. `DO_THING(1, "World")`扩展到`CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)`扩展到`IMPL ## 1`， 扩展到`IMPL1`
1. 现在令牌处于此状态：`IMPL1 ECHO(("Hello", "World"))`
1. 预处理器查找类似于函数的宏标识符`IMPL1`。 因为它没有后跟 ，`(`它不被视为类似于函数的宏调用。
1. 预处理器将转到以下令牌。 它发现调用类似于函数的宏`ECHO`： `ECHO(("Hello", "World"))``("Hello", "World")`
1. `IMPL1`永远不会再考虑扩展，因此扩展的全部结果是：`IMPL1("Hello", "World");`

要修改宏在实验前处理器和传统前处理器下的行为方式相同，请添加另一层间接：

```cpp
#define CAT(a,b) a##b
#define ECHO(...) __VA_ARGS__
// IMPL1 and IMPL2 are macros implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)
#define CALL(macroName, args) macroName args
#define DO_THING_FIXED(a,b) CALL( CAT(IMPL, a), ECHO(( "Hello",b)))
DO_THING_FIXED(1, "World");

// macro expands to:
// do_thing_one( "Hello", "World");
```

## <a name="incomplete-features"></a>功能不完整

从 Visual Studio 2019 版本 16.5 开始，实验预处理器功能齐全，适用于 C++20。 在 Visual Studio 的早期版本中，实验预处理器大部分完成，尽管某些预处理器指令逻辑仍可以追溯到传统行为。 以下是 16.5 之前 Visual Studio 版本中不完整功能的部分列表：

- `_Pragma` 支持
- C++20 功能
- 增强阻塞错误：在版本 16.5 之前，预处理器常量表达式中的逻辑运算符未在新的预处理器中完全实现。 在某些`#if`指令中，新的预处理器可以回落到传统的前处理器。 只有当与传统预处理器不兼容的宏得到扩展时，效果才会明显。 在构建 Boost 预处理器插槽时，可能会发生这种情况。

::: moniker-end
