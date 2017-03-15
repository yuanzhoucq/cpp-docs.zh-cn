---
title: "国际支持 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "全球化 [C++], 字符集"
  - "本地化 [C++], 字符集"
  - "MBCS [C++], 启用"
  - "字符串 [C++], 国际支持"
  - "Unicode [C++], 启用"
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# 国际支持
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大多数传统的 C 和 C\+\+ 代码采用不适用于国际应用程序的字符和字符串操作。  虽然 MFC 和运行库都支持 Unicode 或 MBCS，但您仍需要亲自完成一些工作。  为了向您提供一些指导，本节将解释 Visual C\+\+ 中的“国际支持”的含义：  
  
-   通过 MFC 函数参数列表和返回类型中的可移植数据类型来支持 Unicode 和 MBCS。  根据您的版本是否定义了 **\_UNICODE** 符号或 **\_MBCS**（即 DBCS）符号，按条件用合适的方式来定义这些类型。  根据您的版本定义的符号（即这两个符号中的一个），MFC 库的不同变量自动与应用程序链接。  
  
-   类库代码使用可移植的运行时函数和其他方法来确保正确的 Unicode 或 MBCS 行为。  
  
-   您仍必须在代码中处理特定类型的国际化任务：  
  
    -   使用相同的可移植运行时函数，使 MFC 在任一环境下可移植。  
  
    -   使用 **\_T** 宏使字符串和字符在任一环境下可移植。  有关更多信息，请参见 [Tchar.h 中的一般文本映射](../text/generic-text-mappings-in-tchar-h.md)。  
  
    -   在 MBCS 下分析字符串时有一些注意事项。  而在 Unicode 下分析字符串时则不需要注意这些事项。  有关更多信息，请参见 [MBCS 编程提示](../text/mbcs-programming-tips.md)。  
  
    -   在应用程序中混合使用 ANSI（8 位）和 Unicode（16 位）字符时要小心。  可以在程序的某些部分使用 ANSI 字符，而在其他部分使用 Unicode 字符，但不能在同一字符串中混合使用这两种字符。  
  
    -   在应用程序中不要硬编码字符串。  而应通过将它们添加到应用程序的 .rc 文件使其成为 STRINGTABLE 资源。  然后就可以在不必更改或重新编译源代码的情况下本地化应用程序。  有关 STRINGTABLE 资源的更多信息，请参见 [字符串编辑器](../mfc/string-editor.md)。  
  
> [!NOTE]
>  欧洲和 MBCS 字符集的某些字符（如重音字母）的字符代码大于 0x80。  由于大多数代码使用有符号字符，因此这些大于 0x80 的代码在转换为 `int` 时是带符号扩展的。  这对数组索引是个问题，因为如果带符号扩展的字符为负值，则索引将超出数组范围。  使用 MBCS（如日语）的语言也很独特。  由于一个字符可能由单字节或双字节组成，因此应始终同时处理两个字节。  
  
## 请参阅  
 [Unicode 和 MBCS](../text/unicode-and-mbcs.md)   
 [国际化策略](../text/internationalization-strategies.md)