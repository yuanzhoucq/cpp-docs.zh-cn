---
title: "字符串文本串联 | Microsoft Docs"
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
  - "串联字符串"
  - "字符串 [C++], 串联"
ms.assetid: 51486b1f-4b1e-4061-9add-1aa38c6cdb3c
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# 字符串文本串联
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要形成占用多行的字符串文本，则可以将两个字符串串联起来。  为此，请键入反斜杠，然后按 Return 键。  反斜杠将使编译器忽略以下换行符。  例如，字符串文本  
  
```  
"Long strings can be bro\  
ken into two or more pieces."  
```  
  
 等同于字符串  
  
```  
"Long strings can be broken into two or more pieces."  
```  
  
 在之前可能已使用过反斜杠后跟换行符的任何地方，都可以使用字符串串联，用来输入长于一行的字符串。  
  
 若要在字符串文本中强制换行，请在字符串中要换行的位置输入换行转义序列 \(**\\n**\)，如下所示：  
  
```  
"Enter a number between 1 and 100\nOr press Return"  
```  
  
 由于字符串可以在源代码的任何列中开始，而长字符串可以在后面的行的任何列中继续，因此可以放置字符串以增强源代码可读性。  在任一情况下，在输出时，字符串的屏幕表示形式都不受影响。  例如：  
  
```  
printf_s ( "This is the first half of the string, "  
           "this is the second half ") ;  
```  
  
 只要将字符串中的每个部分都用双引号括起来，则各个部分都将作为单个字符串进行串联和输出。  此串联根据[翻译阶段](../preprocessor/phases-of-translation.md)指定的编译期间的事件顺序发生。  
  
```  
"This is the first half of the string, this is the second half"  
```  
  
 初始化为仅用空白分隔的两个不同的字符串文本的字符串指针将作为单个字符串存储（指针在[指针声明](../c-language/pointer-declarations.md)中讨论）。  当正确引用后（如以下示例所示），结果与上一示例的相同：  
  
```  
char *string = "This is the first half of the string, "  
               "this is the second half";  
  
printf_s( "%s" , string ) ;  
```  
  
 在翻译阶段 6 中，相邻字符串文本或相邻宽字符串文本的任意序列指定的多字节字符序列被串联为一个多字节字符序列。  因此，不要设计在执行期间允许修改字符串文本的程序。  ANSI C 标准规定，修改字符串的结果是不确定的。  
  
## 请参阅  
 [C 字符串文本](../c-language/c-string-literals.md)