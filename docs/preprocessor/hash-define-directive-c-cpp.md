---
title: "#define 指令 (C/C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#define"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#define 指令"
  - "#define 指令, 语法"
  - "定义指令 (#define)"
  - "定义指令 (#define), 语法"
  - "预处理器, 指令"
ms.assetid: 33cf25c6-b24e-40bf-ab30-9008f0391710
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #define 指令 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`#define` 创建一个宏，该宏是标识符或参数化标识符与标记字符串的关联。  在定义宏之后，编译器可用标记字符串替换源文件中标识符的每个匹配项。  
  
## 语法  
 `#define` *identifier* *token\-string*opt  
  
 `#define` *identifier*`(` *identifier*opt`,` *...* `,` *identifier*opt `)` *token\-string*opt  
  
## 备注  
 `#define` 指令促使编译器用 *token\-string* 替换源文件中 *identifier* 的每个匹配项。  仅当 *identifier* 构成标记时才替换它。  也就是说，如果 *identifier* 出现在注释、字符串或较长的标识符中，则不会替换它。  有关详细信息，请参阅 [C\+\+ 标记](../cpp/tokens-cpp.md)。  
  
 *token\-string* 参数由关键字、常量或完整语句等一系列标记构成。  一个或多个空白字符必须将 *token\-string* 与 *identifier* 隔开。  此空白不会被视为替换文本的一部分，也不是跟在文本最后一个标记后面的任何空白。  
  
 没有 *token\-string* 的 `#define` 将从源文件中移除 *identifier* 的匹配项。  *identifier* 将保持定义，并可以使用 `#if defined` 和 `#ifdef` 指令进行测试。  
  
 第二种语法形式定义一个带有参数的类似函数的宏。  此形式接受必须出现在括号内的参数的可选列表。  定义宏之后，*identifier* 的每个后续匹配项（*identifier*opt、...、*identifier*opt）将替换为 *token\-string* 参数的一个版本（具有替换形参的实参）。  
  
 形参名称将出现在 *token\-string* 中以标记实际值的替换位置。  每个参数名称可在 *token\-string* 中出现多次，并且名称可以按任意顺序出现。  调用中的参数数目必须与宏定义中的参数数目一致。  对括号的自由使用将确保正确解释复杂的实参。  
  
 将用逗号分隔列表中的形参。  列表中的每个名称必须是唯一的，并且列表必须用括号括起。  *identifier* 与左括号之间不能有空格。  对于多个源行上的长指令，请使用行串连，即在换行符前紧接着放置一个反斜杠 \(`\`\)。  形参名称的范围将扩展到结束 *token\-string* 的新行。  
  
 使用第二种语法形式定义宏之后，后面跟有参数列表的后续文本实例指示一个宏调用。  跟在源文件中的 *identifier* 实例后面的实参将与宏定义中对应的形参匹配。  *token\-string* 中前面未带 stringizing \(`#`\)、charizing \(`#@`\) 或 token\-pasting \(`##`\) 运算符或后面未跟 `##` 运算符的每个形参将由对应的实参替换。  实参中的所有宏都将在指令替换形参之前扩展。（[预处理器运算符](../preprocessor/preprocessor-operators.md)中介绍了运算符。）  
  
 下面带参数的宏的示例演示了 `#define` 语法的第二种形式：  
  
```  
// Macro to define cursor lines   
#define CURSOR(top, bottom) (((top) << 8) | (bottom))  
  
// Macro to get a random integer with a specified range   
#define getrandom(min, max) \  
    ((rand()%(int)(((max) + 1)-(min)))+ (min))  
```  
  
 有副作用的参数有时会导致宏产生意外的结果。  给定形参可能会多次出现在 *token\-string* 中。  如果将该形参替换为有副作用的表达式，则可能多次计算该表达式及其副作用。（请参阅 [Token\-Pasting 运算符 \(\#\#\)](../preprocessor/token-pasting-operator-hash-hash.md) 下的示例。）  
  
 `#undef` 指令促使忘记标识符的预处理器定义。  有关详细信息，请参阅 [\#undef 指令](../preprocessor/hash-undef-directive-c-cpp.md)。  
  
 如果要定义的宏的名称出现在 *token\-string* 中（即使是作为另一个宏扩展的结果），将不会扩展该名称。  
  
 除非第二个标记序列与第一个标记序列相同，否则名称相同的宏的第二个 `#define` 将生成警告。  
  
 **Microsoft 专用**  
  
 如果新定义在语法上与原始定义相同，则 Microsoft C\/C\+\+ 允许您重新定义宏。  换言之，这两个定义可以具有不同的参数名称。  此行为不同于 [!INCLUDE[vcpransi](../preprocessor/includes/vcpransi_md.md)] C，后者需要两个词法相同的定义。  
  
 例如，下面两个宏除参数名称外完全相同。  [!INCLUDE[vcpransi](../preprocessor/includes/vcpransi_md.md)] C 不允许此类重定义，但 Microsoft C\/C\+\+ 编译它时不会出错。  
  
```  
#define multiply( f1, f2 ) ( f1 * f2 )  
#define multiply( a1, a2 ) ( a1 * a2 )  
```  
  
 另一方面，下面两个宏完全不同，将在 Microsoft C\/C\+\+ 中生成一条警告。  
  
```  
#define multiply( f1, f2 ) ( f1 * f2 )  
#define multiply( a1, a2 ) ( b1 * b2 )  
```  
  
 **结束 Microsoft 专用**  
  
 此示例演示了 `#define` 指令：  
  
```  
#define WIDTH       80  
#define LENGTH      ( WIDTH + 10 )  
```  
  
 第一个语句将标识符 `WIDTH` 定义为整数常量 80，并根据 `WIDTH` 将 `LENGTH` 定义为整数常量 10。  `LENGTH` 的每个匹配项将由 \(`WIDTH + 10`\) 替换。  接下来，`WIDTH + 10` 的每个匹配项将由表达式 \(`80 + 10`\) 替换。  `WIDTH + 10` 两边的括号非常重要，因为它们控制语句中的解释，如下所示：  
  
```  
var = LENGTH * 20;  
```  
  
 在预处理阶段之后，语句将变为：  
  
```  
var = ( 80 + 10 ) * 20;  
```  
  
 其计算结果为 1800。  如果没有括号，则结果将为：  
  
```  
var = 80 + 10 * 20;  
```  
  
 其计算结果为 280。  
  
 **Microsoft 专用**  
  
 使用 [\/D](../build/reference/d-preprocessor-definitions.md) 编译器选项定义宏和常量具有与在文件开头使用 `#define` 处理指令一样的效果。  通过使用 \/D 选项，最多可定义 30 个宏。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [预处理器指令](../preprocessor/preprocessor-directives.md)