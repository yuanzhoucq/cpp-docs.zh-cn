---
title: "#line 指令 (C/C++) | Microsoft Docs"
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
  - "#line"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#line 指令"
  - "行指令 (#line)"
  - "预处理器, 指令"
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# #line 指令 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`#line` 指令告诉预处理器将编译器内部存储的行号和文件名更改为给定行号和文件名。  
  
## 语法  
  
```  
  
#line   
digit-sequence ["filename"]  
```  
  
## 备注  
 该编译器使用行号和选项文件名来引用它在编译时发现的错误。  行号通常指当前输入行，文件名指当前输入文件。  处理了每行后递增行号。  
  
 *digit\-sequence* 值可以是任何整数常数。  宏替换在预处理标记可执行，但结果必须计算为正确的语法。  *filename* 可以为字符的任意组合，且必须括在双引号 \(**" "**\) 内。  如果省略 *filename* ，前面的文件名保持不变。  
  
 您还可以通过编写 `#line` 指令更改源行号和文件名。  转换器使用行号和文件名确定预定义宏 **\_\_FILE\_\_** 和 **\_\_LINE\_\_**的值。  可以使用这些宏将自述性的错误消息插入程序文本。  有关这些预定义的宏的更多信息，请参见[预定义的宏](../preprocessor/predefined-macros.md)。  
  
 **\_\_FILE\_\_** 宏扩展到目录是文件名的字符串，并放在双引号内 \(**" "**\)。  
  
 如果更改行号和文件名，该编译器忽略以前的值并用新值继续处理。  程序生成器通常使用 `#line` 指令导致错误消息以引用原始源文件而不是已生成的程序。  
  
 以下示例阐释 `#line` 和 **\_\_LINE\_\_** 以及 **\_\_FILE\_\_** 宏。  
  
 在此语句中，在内部存储的行号将设置为 151，文件名更改为 `copy.c`。  
  
```  
#line 151 "copy.c"  
```  
  
 在此示例中，如果给定的“断言”未得到满足，宏 `ASSERT` 使用预定义的宏 **\_\_LINE\_\_** 和 **\_\_FILE\_\_** 打印有关源文件中的错误消息。  
  
```  
#define ASSERT(cond)  
  
if( !(cond) )\  
{printf( "assertion error line %d, file(%s)\n", \  
__LINE__, __FILE__ );}  
```  
  
## 请参阅  
 [预处理器指令](../preprocessor/preprocessor-directives.md)