---
title: MSVC 实验预处理器概述
description: 正在更新 MSVC 预处理器，使其符合 C/C++标准。
ms.date: 11/06/2019
helpviewer_keywords:
- preprocessor, experimental
ms.openlocfilehash: 446603b34d9309c256afba9abd7234ae2ab16f5c
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73797186"
---
# <a name="msvc-experimental-preprocessor-overview"></a>MSVC 实验预处理器概述

当前正在C++更新 Microsoft 预处理器以改善标准一致性、修复长久持续 bug 并更改正式定义的某些行为。 此外，还添加了新诊断，以便在宏定义中出现错误时发出警告。

使用 Visual Studio 2017 或 Visual Studio 2019 中的[/experimental：预处理器](../build/reference/experimental-preprocessor.md)编译器开关可以使用其当前状态的更改。 默认预处理器行为与以前版本中的行为相同。

## <a name="new-predefined-macro"></a>新建预定义宏

可以在编译时检测正在使用的预处理器。 检查预定义宏[\_MSVC\_](predefined-macros.md)的值，以了解传统预处理器是否正在使用。 此宏由支持它的编译器的版本无条件设置，与调用的预处理器无关。 对于传统预处理器，其值为1。 对于一致的实验预处理器，它是0：

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

## <a name="behavior-changes-in-the-experimental-preprocessor"></a>实验预处理器中的行为更改

实验预处理器的初始工作重点在于使所有宏展开一致，以便能够将 MSVC 编译器与当前由于传统行为而被阻止的库配合使用。 下面列出了在使用实际项目测试更新的预处理器时所遇到的一些更常见的重大更改。

### <a name="macro-comments"></a>宏注释

传统预处理器基于字符缓冲区，而不是预处理器标记。 这允许异常行为，如以下预处理器注释技巧，这在符合预处理器的情况下将无法使用：

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
DISAPPEARING_TYPE myVal;
```

符合标准的修复方法是在适当的 `#ifdef/#endif` 指令中声明 `int myVal`：

```cpp
#define MYVAL 1

#ifdef MYVAL
int myVal;
#endif
```

### <a name="lval"></a>L # val

传统预处理器将字符串前缀错误地组合到[字符串化运算符（#）](stringizing-operator-hash.md)运算符的结果中：

```cpp
 #define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

在这种情况下，不需要 `L` 前缀，因为在宏展开后，相邻字符串文本会合并在一起。 向后兼容的修复是将定义更改为以下内容：

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

在方便的宏中，还会出现相同的问题： "stringize" 宽字符串文本的参数：

```cpp
 // The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str
```

可以通过多种方式解决该问题：

- 使用 `L""` 和 `#str` 的字符串串联来添加前缀。 这样做是因为在宏展开后会合并相邻字符串文本：

   ```cpp
   #define STRING1(str) L""#str
   ```

- `#str` stringized 后添加前缀，并添加其他宏展开

   ```cpp
   #define WIDE(str) L##str
   #define STRING2(str) WIDE(#str)
   ```

- 使用串联运算符 `##` 来合并标记。 未指定 `##` 和 `#` 操作的顺序，但在这种情况下，所有编译器似乎都计算 `#` `##` 运算符。

   ```cpp
   #define STRING3(str) L## #str
   ```

### <a name="warning-on-invalid-"></a>对无效的 \#\# 发出警告

当[标记粘贴运算符（# #）](token-pasting-operator-hash-hash.md)不产生单个有效的预处理标记时，该行为是不确定的。 传统预处理器将悄悄地组合标记。 新的预处理器将与大多数其他编译器的行为匹配，并发出诊断。

```cpp
// The ## is unnecessary and does not result in a single preprocessing token.
#define ADD_STD(x) std::##x
// Declare a std::string
ADD_STD(string) s;
```

### <a name="comma-elision-in-variadic-macros"></a>可变参数宏中的逗号省略

传统的 MSVC 预处理器始终删除空的空 `__VA_ARGS__` 替换项。 试验性预处理器更严格地遵循其他常用跨平台编译器的行为。 若要移除逗号，可变参数参数必须缺失（不只是空），并且必须使用 `##` 运算符进行标记。 请看下面的示例：

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // In the traditional preprocessor, the following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor will replace the following macro with: func(1, ), which will result in a syntax error.
    FUNC(1, );
}
```

在下面的示例中，在调用中 `FUNC2(1)` 在引发的宏中缺少可变参数参数。 在对的调用中 `FUNC2(1, )` 可变参数参数为空，但不缺少（请注意参数列表中的逗号）。

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

在即将推出的 C + + 2a 标准中，此问题已得到解决，因为添加了尚未实现的 `__VA_OPT__`。

### <a name="macro-arguments-are-unpacked"></a>宏参数为 "解压缩"

在传统预处理器中，如果宏将其参数之一转发给另一个依赖宏，则替换该参数时，该参数不会 "解包"。 通常，此优化会被忽略，但可能导致异常行为：

```cpp
// Create a string out of the first argument, and the rest of the arguments.
#define TWO_STRINGS( first, ... ) #first, #__VA_ARGS__
#define A( ... ) TWO_STRINGS(__VA_ARGS__)
const char* c[2] = { A(1, 2) };

// Conformant preprocessor results:
// const char c[2] = { "1", "2" };

// Traditional preprocessor results, all arguments are in the first string:
// const char c[2] = { "1, 2", };
```

展开 `A()`时，传统预处理器会将 `__VA_ARGS__` 打包的所有参数转发到 TWO_STRINGS 的第一个参数，这将可变参数 `TWO_STRINGS` 参数留空。 这会导致 `#first` 的结果为 "1，2" 而不只是 "1"。 如果你密切关注，你可能会想知道传统预处理器扩展中 `#__VA_ARGS__` 的结果：如果可变参数参数为空，则它应导致空字符串文本 `""`。 由于存在单独的问题，因此未生成空字符串文本标记。

### <a name="rescanning-replacement-list-for-macros"></a>重新扫描宏的替换列表

替换宏后，将重新扫描生成的令牌，以查找需要替换的其他宏标识符。 传统预处理器用于执行重新扫描的算法不符合，如以下示例中所示：

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
// Conformant preprocessor:
// IMPL1 ( "Hello","World");
```

尽管此示例看起来有点精心设计，但却发现它发生了实际的代码。 若要查看正在进行的操作，可以从 `DO_THING`开始分解扩展：

1. `DO_THING(1, "World")` 扩展到 `CAT(IMPL, 1) ECHO(("Hello", "World"))`
1. `CAT(IMPL, 1)` 扩展到扩展到的 `IMPL ## 1` `IMPL1`
1. 现在，令牌处于以下状态： `IMPL1 ECHO(("Hello", "World"))`
1. 预处理器将查找类似于函数的宏标识符 `IMPL1`，但后面不是 `(`，因此不会将其视为类似于函数的宏调用。 
1. 它将移到以下标记上，并查找 `ECHO` 调用的与函数类似的宏： `ECHO(("Hello", "World"))`，该宏扩展到 `("Hello", "World")`
1. 永远不会将 `IMPL1` 视为展开，因此扩展的完整结果是： `IMPL1("Hello", "World");`

通过添加其他间接层，可以修改宏，使其在实验预处理器和传统预处理器下的行为相同：

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

试验性预处理器大多是完整的，尽管一些预处理器指令逻辑仍然会回退到传统行为。 下面是不完整功能的部分列表：

- 支持 `_Pragma`
- C + + 20 功能
- 增大阻止 bug：预处理器常数表达式中的逻辑运算符未在新的预处理器中完全实现。 在某些 `#if` 指令上，新的预处理器可能会回退到传统预处理器。 仅当与传统预处理器不兼容的宏展开时才会出现这种情况，这可能会在生成提升的预处理器槽时出现。
