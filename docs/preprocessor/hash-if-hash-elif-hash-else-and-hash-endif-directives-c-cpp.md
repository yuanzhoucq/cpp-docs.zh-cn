---
title: '#如果 #elif，#else 和 #endif 指令 （C/c + +）'
ms.date: 11/04/2016
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
ms.openlocfilehash: 76b8be265145896105490a82946c50bc576e6f9f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50520412"
---
# <a name="if-elif-else-and-endif-directives-cc"></a>#if、#elif、#else 和 #endif 指令 (C/C++)

**#If**指令与 **#elif**， **#else**，以及 **#endif**指令，控件编译的源代码文件的部分。 如果您编写的表达式 (后 **#if**) 具有非零值，行组之后立即 **#if**指令都保留在翻译单元中。

## <a name="grammar"></a>语法

*条件*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*if 部分命令部件*<sub>opt</sub> *else 部分*<sub>opt</sub> *endif 行*

*if 部分*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*如果行文本*

*如果行*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#if***常量表达式*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifdef***标识符*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#ifndef***标识符*

*命令部件*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*命令行文本*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*命令部件命令行文本*

*命令行*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#elif***常量表达式*

*其他部件*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*其他行文本*

*其他行*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#else**

*endif 行*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**#endif**

每个 **#if**源文件中的指令必须匹配的右 **#endif**指令。 任意数量的 **#elif**指令可以出现在之间 **#if**并 **#endif**指令，但最多一个 **#else**允许指令。 **#Else**指令，如果存在，必须在之前的最后一个指令 **#endif**。

**#If**， **#elif**， **#else**，以及 **#endif**指令可以嵌套在其他的文本部分 **#if**指令。 每个嵌套 **#else**， **#elif**，或 **#endif**指令属于最靠近的前面 **#if**指令。

所有条件编译指令，如 **#if**并 **#ifdef**，必须匹配与右 **#endif**指令之前的文件结束; 否则为错误生成消息。 当条件编译指令包含在包含文件中时，这些指令必须满足相同的条件：包含文件的末尾不能有未匹配的条件编译指令。

命令行后面的部分中执行宏替换 **#elif**命令，因此可以在中使用宏调用*常数表达式*。

预处理器将选择其中一个给定的出现次数*文本*进行进一步处理。 中指定的块*文本*可以是任何序列的文本。 它可占用多个行。 通常*文本*是对编译器或预处理器有意义的程序文本。

预处理器处理选定*文本*并将其传递给编译器。 如果*文本*包含预处理器指令，预处理器将执行这些指令。 仅编译预处理器所选的文本块。

预处理器选择单个*文本*通过以下每个常量表达式求值的项 **#if**或 **#elif**指令直到找到，则返回 true （非零） 常量表达式。 它将选择所有文本 (包括从其他预处理器指令**#**) 直到其关联 **#elif**， **#else**，或 **#endif**.

如果出现的所有*常数表达式*都为 false，或如果没有 **#elif**指令出现，则预处理器选择后的文本块 **#else**子句。 如果 **#else**省略子句和的所有实例*常数表达式*中 **#if**块都为 false，不选择任何文本块。

*常数表达式*是具有下列其他限制的整数常量表达式：

- 表达式必须具有整型类型和可以包括整数常量、 字符常量和**定义**运算符。

- 表达式不能使用 `sizeof` 或 type-cast 运算符。

- 目标环境无法表示整数的所有范围。

- 转换表示类型**int**类型相同**长**，并**无符号的 int**相同**无符号长**。

- 转换器可以将字符常量转换为与目标环境的集不同的代码值集。 若要确定目标环境的属性，请从为目标环境生成的应用程序中的 LIMITS.H 中检查宏的值。

- 该表达式不得执行任何环境查询，并且必须不受与目标计算机上的实现详细信息的影响。

## <a name="defined"></a>已定义

预处理器运算符**定义**可在特殊常量表达式，如以下语法所示：

defined( `identifier` )

defined `identifier`

此常量表达式被视为 true （非零），是否*标识符*当前定义; 否则，条件为 false (0)。 定义为空文本的标识符被视为已定义。 **定义**中，可以使用指令 **#if**和一个 **#elif**指令，但在其他位置不可用。

在以下示例中， **#if**并 **#endif**指令控制三个函数调用之一的编译：

```C
#if defined(CREDIT)
    credit();
#elif defined(DEBIT)
    debit();
#else
    printerror();
#endif
```

如果定义了标识符 `credit`，则编译对 `CREDIT` 的函数调用。 如果定义了标识符 `DEBIT`，则编译对 `debit` 的函数调用。 如果两个标识符都未定义，则编译对 `printerror` 的调用。 请注意，`CREDIT` 和 `credit` 是 C 和 C++ 中的不同标识符，因为它们的情况不同。

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

第一个 **#if**块显示两组嵌套 **#if**， **#else**，以及 **#endif**指令。 仅当 `DLEVEL > 5` 为 true 时，才会处理第一组指令。 否则为后面的语句 **#else**进行处理。

**#Elif**并 **#else**第二个示例中的指令用于使值的基础的四个选项之一`DLEVEL`。 将常量 `STACK` 设置为 0、100 或 200，具体取决于 `DLEVEL` 的定义。 如果 `DLEVEL` 大于 5，则编译

```C
#elif DLEVEL > 5
display(debugptr);
```

该语句，并且不会定义 `STACK`。

条件编译的常见用途是防止多次包含同一个头文件。 在 C++ 中，通常在头文件中定义类，如下构造可用于防止多个定义：

```cpp
/*  EXAMPLE.H - Example header file  */
#if !defined( EXAMPLE_H )
#define EXAMPLE_H

class Example
{
...
};

#endif // !defined( EXAMPLE_H )
```

前面的代码将检查以查看是否定义了符号常量 `EXAMPLE_H`。 如果是这样，则已包括该文件，并且不需要重新处理该文件。 否则，定义常量 `EXAMPLE_H` 以将 EXAMPLE.H 标记为已处理。

## <a name="hasinclude"></a>__has_include

**Visual Studio 2017 版本 15.3 及更高版本**： 确定库标头是否可用于包含：

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