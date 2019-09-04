---
title: /experimental：预处理器（启用预处理器一致性模式）
description: 使用/experimental：预处理器编译器选项启用标准相容预处理器的实验性编译器支持。
ms.date: 09/03/2019
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 3055cfa2a32d1d668dbe0c51b5542415b5bb0af4
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294434"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>/experimental：预处理器（启用预处理器一致性模式）

此选项可启用符合 c + + 11 标准（包括 C99 预处理器功能）的试验性、基于令牌的预处理器。

## <a name="syntax"></a>语法

> **/experimental：预处理器**[ **-** ]

## <a name="remarks"></a>备注

使用 **/experimental：预处理器**编译器选项可以启用试验性相容预处理器。 可以使用 **/experimental：预处理器-** 选项显式指定传统预处理器。

从 Visual Studio 2017 版本15.8 开始，可以使用 **/experimental：预处理器**选项。

可以在编译时检测正在使用的预处理器。 检查预定义宏[ \_MSVC\_](../../preprocessor/predefined-macros.md)的值，以判断传统预处理器是否正在使用。 此宏由支持它的编译器的版本无条件设置，与调用的预处理器无关。 对于传统预处理器，其值为1。 对于一致的实验预处理器，它是0：

```cpp
#if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
// Logic using the traditional preprocessor
#else
// Logic using cross-platform compatible preprocessor
#endif
```

### <a name="behavior-changes-in-the-experimental-preprocessor"></a>实验预处理器中的行为更改

下面是启用了预处理器一致性模式时发现的一些更常见的重大更改：

#### <a name="macro-comments"></a>宏注释

传统预处理器使用字符缓冲区，而不是预处理器标记。 这将允许一些异常行为，如此预处理器注释技巧，这在符合预处理器的情况下不起作用：

```cpp
#if DISAPPEAR
#define DISAPPEARING_TYPE /##/
#else
#define DISAPPEARING_TYPE int
#endif

// myVal disappears when DISAPPEARING_TYPE is turned into a comment
// To make standards compliant, wrap the following line with the appropriate #if/#endif
DISAPPEARING_TYPE myVal;
```

#### <a name="string-prefixes-lval"></a>字符串前缀（L # val）

传统预处理器将字符串前缀错误地组合到[字符串化运算符（#）](../../preprocessor/stringizing-operator-hash.md)的结果中：

```cpp
#define DEBUG_INFO(val) L"debug prefix:" L#val
//                                       ^
//                                       this prefix

const wchar_t *info = DEBUG_INFO(hello world);
```

此处不需要前缀，因为在宏展开后，相邻字符串文本会合并在一起。 `L` 向后兼容的修复是将定义更改为：

```cpp
#define DEBUG_INFO(val) L"debug prefix:" #val
//                                       ^
//                                       no prefix
```

此问题也可以在方便的宏中找到，其中 "stringize" 宽字符串文本的参数：

```cpp
// The traditional preprocessor creates a single wide string literal token
#define STRING(str) L#str

// Potential fixes:
// Use string concatenation of L"" and #str to add prefix
// This works because adjacent string literals are combined after macro expansion
#define STRING1(str) L""#str

// Add the prefix after #str is stringized with additional macro expansion
#define WIDE(str) L##str
#define STRING2(str) WIDE(#str)

// Use concatenation operator ## to combine the tokens.
// The order of operations for ## and # is unspecified, although all compilers
// checked perform the # operator before ## in this case.
#define STRING3(str) L## #str
```

#### <a name="warning-on-invalid"></a>对无效的警告 ##

当[标记粘贴运算符（# #）](../../preprocessor/token-pasting-operator-hash-hash.md)不产生单个有效的预处理标记时，该行为是不确定的。 传统预处理器以静默方式组合标记失败。 新的预处理器匹配大多数其他编译器的行为，并发出诊断。

```cpp
// The ## is unnecessary and doesn't result in a single preprocessing token.
#define ADD_STD(x) std::##x

// Declare a std::string
ADD_STD(string) s;
```

#### <a name="comma-elision-in-variadic-macros"></a>可变参数宏中的逗号省略

请看下面的示例：

```cpp
void func(int, int = 2, int = 3);
// This macro replacement list has a comma followed by __VA_ARGS__
#define FUNC(a, ...) func(a, __VA_ARGS__)
int main()
{
    // The following macro is replaced with:
    // func(10,20,30)
    FUNC(10, 20, 30);

    // A conforming preprocessor replaces the following macro with:
    // func(1, );
    // which results in a syntax error.
    FUNC(1, );
}
```

所有主要编译器都具有可帮助解决此问题的预处理器扩展。 传统的 MSVC 预处理器在空`__VA_ARGS__`替换之前始终删除逗号。 更新的预处理器更严格地遵循其他流行的跨平台编译器的行为。 若要移除逗号，可变参数参数必须缺失，而不是仅为空，并且必须用`##`运算符进行标记：

```cpp
#define FUNC2(a, ...) func(a , ## __VA_ARGS__)
int main()
{
    // The variadic argument is missing in the macro being evoked
    // The comma is removed and replaced with:
    // func(1)
    FUNC2(1);

    // The variadic argument is empty, but not missing. (Notice the
    // comma in the argument list.) The comma isn't removed
    // when the macro is replaced:
    // func(1, )
    FUNC2(1, );
}
```

在即将推出的 C + + 2a 标准中，已通过添加`__VA_OPT__`实现了此问题的解决方法。

#### <a name="macro-arguments-are-unpacked"></a>宏参数为 "解压缩"

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

展开`A()`时，传统预处理器会将`__VA_ARGS__`打包的所有参数转发`TWO_STRINGS`到的第一个参数。 的可变参数参数`TWO_STRINGS`为空，这将导致`"1, 2"`的`#first`结果不只`"1"`是。 您可能想知道传统预处理器扩展`#__VA_ARGS__`中的结果发生了什么情况。 如果可变参数参数为空，则它应导致空字符串 ""。 由于有一个单独的问题，因此不会生成空字符串文本标记。

#### <a name="rescanning-replacement-list-for-macros"></a>重新扫描宏的替换列表

替换宏后，将重新扫描生成的令牌，以便替换其他宏标识符。 传统预处理器使用的重新扫描算法不符合，如以下示例中所示：

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

若要查看此示例中发生的情况，我们将从开始`DO_THING`细分扩展：

`DO_THING(1, "World")` ->
`CAT(IMPL, 1) ECHO(("Hello", "World"))`

其次，CAT 已展开：

`CAT(IMPL, 1)` -> `IMPL ## 1` -> `IMPL1`

这会将令牌置于此状态：

`IMPL1 ECHO(("Hello", "World"))`

预处理器会查找类似函数的宏标识符`IMPL1`，但后面不是 "（"，因此不会将其视为类似于函数的宏调用。 它将移到以下标记并查找`ECHO`调用的函数（类似于函数）：

`ECHO(("Hello", "World"))` -> `("Hello", "World")`

`IMPL1`永远不会被视为展开，因此扩展的完整结果为：

`IMPL1("Hello", "World");`

可以修改宏，使其在实验预处理器和传统预处理器上的行为方式相同。 解决方案是添加其他间接层：

```cpp
#define CAT(a,b) a##b
#define ECHO(...) __VA_ARGS__

// IMPL1 and IMPL2 are macros implementation details
#define IMPL1(prefix,value) do_thing_one( prefix, value)
#define IMPL2(prefix,value) do_thing_two( prefix, value)

#define CALL(macroName, args) macroName args
#define DO_THING_FIXED(a,b) CALL( CAT(IMPL, a), ECHO(( "Hello",b)))

DO_THING_FIXED(1, "World");
// macro expanded to:
// do_thing_one( "Hello", "World");
```

### <a name="conformance-mode-conformance"></a>一致性模式一致性

实验预处理器尚未完成，一些预处理器指令逻辑仍然会回退到传统行为。 下面是不完整功能的部分列表：

- 支持`_Pragma`
- C + + 20 功能
- 其他诊断改进
- 用于控制/E 和/P 下的输出的开关
- 增大阻止 bug：预处理器常量表达式中的逻辑运算符未在新的预处理器中完全实现。 在某些`#if`指令上，新的预处理器可能会回退到传统的预处理器。 仅当与传统预处理器不兼容的宏展开时才会出现这种情况，这可能会在生成提升的预处理器槽时出现。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择“配置属性” > “C/C++” > “命令行”属性页。

1. 修改 "**附加选项**" 属性以包含 **/experimental：预处理器**，然后选择 **"确定"** 。

## <a name="see-also"></a>请参阅

[/Zc（一致性）](zc-conformance.md)
