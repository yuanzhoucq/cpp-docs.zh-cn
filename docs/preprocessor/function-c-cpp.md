---
title: "函数 (C/C++) | Microsoft Docs"
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
  - "function_CPP"
  - "vc-pragma.function"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "函数杂注"
  - "杂注, 函数"
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
caps.latest.revision: 10
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 函数 (C/C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定生成对杂注的参数列表中指定的函数的调用。  
  
## 语法  
  
```  
  
#pragma function( function1 [, function2, ...] )  
```  
  
## 备注  
 如果使用 **intrinsic** 杂注（或 \/Oi）指示编译器生成内部函数（内部函数生成为内联代码而不是函数调用），则可以使用 **function** 杂注来显式强制实现函数调用。  一旦显示函数杂注，它将在包含指定的内部函数的第一个函数定义中生效。  该效果持续到源文件的结尾或指定相同内部函数的 **intrinsic** 杂注的出现位置。  **function** 杂注仅能在函数的外部使用 \- 在全局级别。  
  
 有关具有内部形式的函数的列表，请参阅 [\#pragma intrinsic](../preprocessor/intrinsic.md)。  
  
## 示例  
  
```  
// pragma_directive_function.cpp  
#include <ctype.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
  
// use intrinsic forms of memset and strlen  
#pragma intrinsic(memset, strlen)  
  
// Find first word break in string, and set remaining  
// chars in string to specified char value.  
char *set_str_after_word(char *string, char ch) {  
   int i;  
   int len = strlen(string);  /* NOTE: uses intrinsic for strlen */  
  
   for(i = 0; i < len; i++) {  
      if (isspace(*(string + i)))   
         break;  
   }  
  
   for(; i < len; i++)   
      *(string + i) = ch;  
  
   return string;  
}  
  
// do not use strlen intrinsic  
#pragma function(strlen)  
  
// Set all chars in string to specified char value.  
char *set_str(char *string, char ch) {  
   // Uses intrinsic for memset, but calls strlen library function  
   return (char *) memset(string, ch, strlen(string));  
}  
  
int main() {  
   char *str = (char *) malloc(20 * sizeof(char));  
  
   strcpy_s(str, sizeof("Now is the time"), "Now is the time");  
   printf("str is '%s'\n", set_str_after_word(str, '*'));  
   printf("str is '%s'\n", set_str(str, '!'));  
}  
```  
  
  **str 为“Now\*\*\*\*\*\*\*\*\*\*\*\*”**  
**str 为“\!\!\!\!\!\!\!\!\!\!\!\!\!\!\!”**   
## 请参阅  
 [Pragma 指令和 \_\_Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)