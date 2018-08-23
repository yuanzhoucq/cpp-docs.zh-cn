---
title: 函数 （C/c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- function_CPP
- vc-pragma.function
dev_langs:
- C++
helpviewer_keywords:
- function pragma
- pragmas, function
ms.assetid: cbd1bd60-fabf-4b5a-9c3d-2d9f4b871365
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 76ab5b2911d349c62ff18967e7a660cdc3589ddd
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/10/2018
ms.locfileid: "42539943"
---
# <a name="function-cc"></a>函数 (C/C++)
指定生成对杂注的自变量列表中指定的函数的调用。  
  
## <a name="syntax"></a>语法  
  
```  
#pragma function( function1 [, function2, ...] )  
```  
  
## <a name="remarks"></a>备注  

如果您使用`intrinsic`杂注 （或 /Oi） 告诉编译器生成内部函数 （内部函数生成为内联代码而不是作为函数调用），可以使用**函数**杂注来显式强制函数调用。 一旦显示函数杂注，它将在包含指定的内部函数的第一个函数定义中生效。 该效果持续到源文件的末尾或外观的`intrinsic`杂注指定相同内部函数。 **函数**杂注可以仅在函数的外部使用，在全局级别。  
  
有关具有内部形式的函数列表，请参阅[#pragma 内部](../preprocessor/intrinsic.md)。  
  
## <a name="example"></a>示例  
  
```cpp  
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
  
```Output  
str is 'Now************'  
str is '!!!!!!!!!!!!!!!'  
```  
  
## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)