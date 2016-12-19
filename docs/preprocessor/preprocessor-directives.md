---
title: "预处理器指令 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "指令, 预处理器"
  - "预处理器, 指令"
ms.assetid: e0fc4564-b6cf-4a36-bf51-6ccd7abd0a94
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 预处理器指令
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

预处理器指令（如 `#define` 和 **\#ifdef**）通常用于简化源程序在不同的执行环境中的更改和编译。  源文件中的指令告知预处理器执行特定操作。  例如，预处理器可以替换文本中的标记，将其他文件的内容插入源文件，或通过移除几个部分的文本来取消一部分文件的编译。  在扩展宏之前，将识别并执行预处理器行。  因此，如果宏扩展到类似于预处理器命令的内容，该预处理器无法识别此命令。  
  
 预处理器语句使用的字符集与源文件语句的相同，只不过转义序列不受支持。  预处理器语句中使用的字符集与[执行字符集](http://msdn.microsoft.com/zh-cn/a7901c61-524d-47c6-beb6-d9dacc2e72ed)相同。  预处理器还可识别负字符值。  
  
 预处理器可识别下列指令：  
  
|||||  
|-|-|-|-|  
|[\#define](../preprocessor/hash-define-directive-c-cpp.md)|[\#error](../preprocessor/hash-error-directive-c-cpp.md)|[\#import](../preprocessor/hash-import-directive-cpp.md)|[\#undef](../preprocessor/hash-undef-directive-c-cpp.md)|  
|[\#elif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[\#if](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[\#include](../preprocessor/hash-include-directive-c-cpp.md)|[\#using](../preprocessor/hash-using-directive-cpp.md)|  
|[\#else](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|[\#ifdef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[\#line](../preprocessor/hash-line-directive-c-cpp.md)|[\#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|  
|[\#ifndef](../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md)|[\#pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)|||  
  
 数字符号 \(**\#**\) 必须是包含指令的行上的第一个非空白字符；空白字符可能出现在数字符号与指令的第一个字母之间。  某些指令包含参数或值。  所有跟在指令后面（指令包含的参数或值除外）的文本的前面必须有单行注释分隔符 \(**\/\/**\) 或者必须括在注释分隔符 \(**\/\* \*\/**\) 中。  包含预处理器指令的行可以通过紧靠在结束行标记前放置反斜杠 \(**\\**\) 继续。  
  
 预处理器指令可以出现在源文件中的任何位置，但是它们仅应用于源文件的剩余部分。  
  
## 请参阅  
 [预处理器运算符](../preprocessor/preprocessor-operators.md)   
 [预定义的宏](../preprocessor/predefined-macros.md)   
 [C\/C\+\+ 预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)