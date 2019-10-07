---
title: '#if、#elif、#else 和 #endif 指令 (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#else'
- '#endif'
- '#if'
- '#elif'
- defined
- __has_include
helpviewer_keywords:
- '#elif directive'
- conditional compilation, directives
- endif directive (#endif)
- preprocessor, directives
- '#else directive'
- '#endif directive'
- if directive (#if)
- else directive (#else)
- '#if directive'
- elif directive (#elif)
- defined directive
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
ms.openlocfilehash: 2b7ed4733dcafda793b9a945c3f40739b52e040a
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220344"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>#if、#elif、#else 和 #endif 指令 (C/C++)

使用 **#elif**、 **#else**和 **#endif**指令的 **#if**指令控制源文件部分的编译。 如果您编写的表达式 (在 **#if**后) 有一个非零值, 则紧跟在 **#if**指令后面的行组将保留在翻译单元中。

## <a name="grammar"></a>语法

*条件*: \
&nbsp;&nbsp;&nbsp;&nbsp;*elif 部分*<sub>opt</sub>*else-部分*<sub>opt</sub>*endif 行*

*如果-部分*: \
&nbsp;&nbsp;&nbsp;&nbsp;*if-line 文本*

*如果为-line* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *常量表达式*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *标识符*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *标识符*

*elif* :
&nbsp;&nbsp;&nbsp;&nbsp;*elif 文本*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif part elif text*

*elif* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif**  *constant-expression*

*else-部分*: \
&nbsp;&nbsp;&nbsp;&nbsp;*else-线条文本*

*else-line* : \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif 行*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

## <a name="remarks"></a>备注

源文件中的每个 **#if**指令必须通过关闭 **#endif**指令来匹配。 **#If**和 **#endif**指令之间可以出现任意数量的 **#elif**指令, 但最多允许一个 **#else**指令。 **#Else**指令 (如果有) 必须是 **#endif**前的最后一个指令。

**#If**、 **#elif**、 **#else**和 **#endif**指令可以嵌套在其他 **#if**指令的*文本*部分中。 每个嵌套的 **#else**、 **#elif**或 **#endif**指令属于最近的 **#if**指令。

所有条件编译指令 (如 **#if**和 **#ifdef**) 必须与结束 **#endif**指令在文件结尾之前匹配。 否则, 会生成错误消息。 当条件编译指令包含在包含文件中时, 它们必须满足相同的条件:包含文件的末尾不能有不匹配的条件编译指令。

宏替换是在 **#elif**命令后面的行部分完成的, 因此可以在*常数表达式*中使用宏调用。

预处理器选择*文本*的给定匹配项之一以进行进一步处理。 *Text*中指定的块可以是任何文本序列。 它可占用多个行。 通常,*文本*是对编译器或预处理器有意义的程序文本。

预处理器处理选定的*文本*, 并将其传递给编译器。 如果*文本*包含预处理器指令, 则预处理器将执行这些指令。 仅编译预处理器所选的文本块。

预处理器通过计算每个 **#if**或 **#elif**指令后面的常数表达式来选择单个*文本*项, 直到它找到 true (非零) 常数表达式。 它将选择所有文本 (包括从其他预处理器指令 **#** ) 直到其关联 **#elif**， **#else**，或 **#endif**.

如果出现的所有*常量表达式*均为 false, 或者如果没有出现 **#elif**指令, 则预处理器将在 **#else**子句之后选择文本块。 如果没有 **#else**子句, 且 **#if**块中的*常量表达式*的所有实例均为 false, 则不会选择任何文本块。

*常数表达式*是具有以下附加限制的整数常量表达式:

- 表达式的类型必须为整型, 并且只能包含整数常量、字符常量和**定义**的运算符。

- 表达式不能使用`sizeof`或类型转换运算符。

- 目标环境可能无法表示整数的所有范围。

- 翻译的类型为**int**的方法与类型**long**和无符号**整数**的类型相同, 其方式与**无符号长**。

- 转换器可以将字符常量转换为与目标环境的集不同的代码值集。 若要确定目标环境的属性, 请使用为该环境构建的应用来检查限制的值 *。H*宏。

- 表达式不能查询环境, 必须与目标计算机上的实现细节保持不变。

## <a name="preprocessor-operators"></a>预处理器运算符

### <a name="defined"></a>已定义

**定义**的预处理器运算符可用于特殊常量表达式, 如以下语法所示:

> **定义 (** *标识符* **)** \
> **定义** *标识符*

如果当前定义了*标识符*, 则将此常量表达式视为 true (非零)。 否则，条件为 false (0)。 定义为空文本的标识符被视为已定义。 **定义**的运算符可用于 **#if**和 **#elif**指令中, 但其他地方不能使用。

在下面的示例中, **#if**和 **#endif**指令控制三个函数调用之一的编译:

```C
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```

如果定义了标识符 `credit`，则编译对 `CREDIT` 的函数调用。 如果定义了标识符 `DEBIT`，则编译对 `debit` 的函数调用。 如果两个标识符都未定义，则编译对 `printerror` 的调用。 和都是 C 中的不同标识符C++ , 因为它们的事例不同。 `credit` `CREDIT`

以下示例中的条件编译语句假定一个名为 `DLEVEL` 的之前定义的符号常量。

```C
#if DLEVEL > 5
    #define SIGNAL  1
    #if STACKUSE == 1
        #define STACK   200
    #else
        #define STACK   100
    #endif
#else
    #define SIGNAL  0
    #if STACKUSE == 1
        #define STACK   100
    #else
        #define STACK   50
    #endif
#endif
#if DLEVEL == 0
    #define STACK 0
#elif DLEVEL == 1
    #define STACK 100
#elif DLEVEL > 5
    display( debugptr );
#else
    #define STACK 200
#endif
```

第一个 **#if**块显示两组嵌套 **#if**、 **#else**和 **#endif**指令。 仅当 `DLEVEL > 5` 为 true 时，才会处理第一组指令。 否则, 将处理 **#else**后的语句。

第二个示例中的 **#elif**和 **#else**指令用于根据的值`DLEVEL`进行四个选项之一。 将常量 `STACK` 设置为 0、100 或 200，具体取决于 `DLEVEL` 的定义。 如果 `DLEVEL` 大于 5，则编译

```C
#elif DLEVEL > 5
display(debugptr);
```

已编译, `STACK`未定义。

条件编译的常见用途是防止多次包含同一个头文件。 在C++中, 通常在头文件中定义类, 此类构造可用于防止多个定义:

```cpp
/*  EXAMPLE.H - Example header file  */
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
    //...
};

#endif // !defined( EXAMPLE_H )
```

前面的代码将检查以查看是否定义了符号常量 `EXAMPLE_H`。 如果是这样, 则该文件已包含在中, 不需要重新处理。 否则，定义常量 `EXAMPLE_H` 以将 EXAMPLE.H 标记为已处理。

### <a name="__has_include"></a>__has_include

**Visual Studio 2017 版本 15.3 及更高版本**：确定库标头是否可用于包含:

```cpp
#ifdef __has_include
#  if __has_include(<filesystem>)
#    include <filesystem>
#    define have_filesystem 1
#  elif __has_include(<experimental/filesystem>)
#    include <experimental/filesystem>
#    define have_filesystem 1
#    define experimental_filesystem
#  else
#    define have_filesystem 0
#  endif
#endif
```

## <a name="see-also"></a>请参阅

[预处理器指令](../preprocessor/preprocessor-directives.md)
