---
title: "_STATIC_ASSERT 宏 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_STATIC_ASSERT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_STATIC_ASSERT 宏"
ms.assetid: 89b0350c-2c2f-4be6-9786-8b1f0780a5da
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# _STATIC_ASSERT 宏
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在编译时计算表达式当如果结果为 `FALSE`，则会生成错误。  
  
## 语法  
  
```  
_STATIC_ASSERT(  
    booleanExpression  
);  
```  
  
#### 参数  
 `booleanExpression`  
 计算表达式 \(包含指针\)为非0 \(`TRUE`\) 或 0 \(`FALSE`\)。  
  
## 备注  
 此宏类似于 [\_ASSERT 和\_ASSERTE 宏](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)，但 `booleanExpression` 在编译时计算而非运行时。  如果 `booleanExpression` 计算结果为 `FALSE` \(0\)，则生成 [编译器错误 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md)。  
  
## 示例  
 在此示例中，我们检查是否 `sizeof` `int` 大于或等于 2 字节，并且是否 `sizeof` `long` 为 1 字节。  程序将不编译，并将生成 [编译器错误 C2466](../../error-messages/compiler-errors-1/compiler-error-c2466.md)，由于 `long` 大于 1 字节。  
  
```  
// crt__static_assert.c  
  
#include <crtdbg.h>  
#include <stdio.h>  
  
_STATIC_ASSERT(sizeof(int) >= 2);  
_STATIC_ASSERT(sizeof(long) == 1);  // C2466  
  
int main()  
{  
    printf("I am sure that sizeof(int) will be >= 2: %d\n",  
        sizeof(int));  
    printf("I am not so sure that sizeof(long) == 1: %d\n",  
        sizeof(long));  
}  
```  
  
## 要求  
  
|宏|必需的标头|  
|-------|-----------|  
|`_STATIC_ASSERT`|\<CRTDBG.H\>|  
  
## .NET Framework 等效项  
 [System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)  
  
## 请参阅  
 [按字母顺序的函数参考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [\_ASSERT、\_ASSERTE、\_ASSERT\_EXPR 宏](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)