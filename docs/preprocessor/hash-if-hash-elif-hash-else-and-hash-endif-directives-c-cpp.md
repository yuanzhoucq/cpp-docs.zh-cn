---
title: "#if、#elif、#else 和 #endif 指令 (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#else"
  - "#endif"
  - "#if"
  - "#elif"
  - "Defined"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#elif 指令"
  - "#else 指令"
  - "#endif 指令"
  - "#if 指令"
  - "条件编译, 指令"
  - "defined 指令"
  - "elif 指令 (#elif)"
  - "else 指令 (#else)"
  - "endif 指令 (#endif)"
  - "if 指令 (#if)"
  - "预处理器, 指令"
ms.assetid: c77a175f-6ca8-47d4-8df9-7bac5943d01b
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #if、#elif、#else 和 #endif 指令 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`#if` 指令与 `#elif`、`#else` 和 `#endif` 指令一起控制源文件部分的编译。  如果您编写的表达式（在 `#if` 后）有一个非零值，则在翻译单元中保留紧跟 `#if` 指令的行组。  
  
## 语法  
 *conditional* :  
 *if\-part elif\-parts* opt *else\-part*opt *endif\-line*  
  
 *if\-part* :  
 *if\-line text*  
  
 *if\-line* :  
 **\#if**  *constant\-expression*  
  
 **\#ifdef**  *identifier*  
  
 **\#ifndef**  *identifier*  
  
 *elif\-parts* :  
 *elif\-line text*  
  
 *elif\-parts elif\-line text*  
  
 *elif\-line* :  
 **\#elif**  *constant\-expression*  
  
 *else\-part* :  
 *else\-line text*  
  
 *else\-line* :  
 `#else`  
  
 *endif\-line* :  
 `#endif`  
  
 源文件中的每个 `#if` 指令必须与表示结束的 `#endif` 指令匹配。  任意数量的 `#elif` 指令可以出现在 `#if` 和 `#endif` 指令之间，但最多允许一个 `#else` 指令。  `#else` 指令（如果有）必须是 `#endif` 之前的最后一个指令。  
  
 `#if`、`#elif`、`#else` 和 `#endif` 指令可以嵌套在其他 `#if` 指令的文本部分中。  每个嵌套的 `#else`、`#elif` 或 `#endif` 指令属于最靠近的前面的 `#if` 指令。  
  
 所有条件编译指令（例如，`#if` 和 **\#ifdef**）都必须与文件末尾前面的表示结束的 `#endif` 指令匹配；否则，将生成错误消息。  当条件编译指令包含在包含文件中时，这些指令必须满足相同的条件：包含文件的末尾不能有未匹配的条件编译指令。  
  
 在 `#elif` 命令后面的命令行部分中执行宏替换，以便能够在 *constant\-expression* 中使用宏调用。  
  
 预处理器选择 *text* 的给定匹配项之一以进行进一步处理。  *text* 中指定的块可以是文本的任意序列。  它可占用多个行。  通常，*text* 是对编译器或预处理器有意义的程序文本。  
  
 预处理器处理选定的 *text*，并将其传递给编译器。  如果 *text* 包含预处理器指令，则预处理器将执行这些指令。  仅编译预处理器所选的文本块。  
  
 预处理器通过计算每个 `#if` 或 `#elif` 指令后面的常数表达式来选择单个 *text* 项，直到找到实际（非零）常量表达式。  它选择所有文本（包括以 **\#** 开头的其他预处理器指令），直到其关联的 `#elif`、`#else` 或 `#endif`。  
  
 如果 *constant\-expression* 的所有匹配项都为 false，或者 `#elif` 指令未出现，则预处理器将选择 `#else` 子句后面的文本块。  如果 `#else` 子句被省略，并且 `#if` 块中的 *constant\-expression* 的所有实例都为 false，则不选择文本块。  
  
 *constant\-expression* 是具有下列其他限制的整数常量表达式：  
  
-   表达式必须具有整型，并且只能包含整数常量、字符常量和 **defined** 运算符。  
  
-   表达式不能使用 `sizeof` 或 type\-cast 运算符。  
  
-   目标环境无法表示整数的所有范围。  
  
-   转换表示与类型 `int`（与类型 **long** 相同）和 `unsigned int`（与 `unsigned long` 相同）。  
  
-   转换器可以将字符常量转换为与目标环境的集不同的代码值集。  若要确定目标环境的属性，请从为目标环境生成的应用程序中的 LIMITS.H 中检查宏的值。  
  
-   该表达式不得执行任何环境查询，并且必须不受与目标计算机上的实现详细信息的影响。  
  
 预处理器运算符 **defined** 可用于特定常量表达式中，如以下语法所示：  
  
 defined\( `identifier` \)  
  
 defined `identifier`  
  
 如果当前定义了 *identifier*，则该常量表达式被视为 true（非零）；否则条件为 false \(0\)。  定义为空文本的标识符被视为已定义。  **defined** 指令可用于 `#if` 和 `#elif` 指令，但在其他位置不可用。  
  
 在下面的示例中，`#if` 和 `#endif` 指令控制三个函数调用之一的编译：  
  
```  
#if defined(CREDIT)  
    credit();  
#elif defined(DEBIT)  
    debit();  
#else  
    printerror();  
#endif  
```  
  
 如果定义了标识符 `CREDIT`，则编译对 `credit` 的函数调用。  如果定义了标识符 `DEBIT`，则编译对 `debit` 的函数调用。  如果两个标识符都未定义，则编译对 `printerror` 的调用。  请注意，`CREDIT` 和 `credit` 是 C 和 C\+\+ 中的不同标识符，因为它们的情况不同。  
  
 以下示例中的条件编译语句假定一个名为 `DLEVEL` 的之前定义的符号常量。  
  
```  
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
  
 第一个 `#if` 块显示两组嵌套的 `#if`、`#else` 和 `#endif` 指令。  仅当 `DLEVEL > 5` 为 true 时，才会处理第一组指令。  否则，处理 \#**else** 后面的语句。  
  
 第二个示例中的 `#elif` 和 `#else` 指令用于根据 `DLEVEL` 的值做出四种选择之一。  将常量 `STACK` 设置为 0、100 或 200，具体取决于 `DLEVEL` 的定义。  如果 `DLEVEL` 大于 5，则编译  
  
```  
#elif DLEVEL > 5  
display(debugptr);  
```  
  
 该语句，并且不会定义 `STACK`。  
  
 条件编译的常见用途是防止多次包含同一个头文件。  在 C\+\+ 中，通常在头文件中定义类，如下构造可用于防止多个定义：  
  
```  
/*  EXAMPLE.H - Example header file  */  
#if !defined( EXAMPLE_H )  
#define EXAMPLE_H  
  
class Example  
{  
...  
};  
  
#endif // !defined( EXAMPLE_H )  
```  
  
 前面的代码将检查以查看是否定义了符号常量 `EXAMPLE_H`。  如果是这样，则已包括该文件，并且不需要重新处理该文件。  否则，定义常量 `EXAMPLE_H` 以将 EXAMPLE.H 标记为已处理。  
  
## 请参阅  
 [预处理器指令](../preprocessor/preprocessor-directives.md)