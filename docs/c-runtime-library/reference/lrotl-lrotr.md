---
title: "_lrotl、_lrotr | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_lrotl"
  - "_lrotr"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "lrotr"
  - "lrotl"
  - "_lrotr"
  - "_lrotl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_lrotl 函数"
  - "_lrotr 函数"
  - "位"
  - "位, 旋转"
  - "lrotl 函数"
  - "lrotr 函数"
  - "旋转位"
ms.assetid: d42f295b-35f9-49d2-9ee4-c66896ffe68e
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lrotl、_lrotr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

旋转位到左边 \(`_lrotl`\) 右侧或 \(`_lrotr`\)。  
  
## 语法  
  
```  
  
      unsigned long _lrotl(  
   unsigned long value,  
   int shift   
);  
unsigned long _lrotr(  
   unsigned long value,  
   int shift   
);  
```  
  
#### 参数  
 *值*  
 将旋转的值。  
  
 `shift`  
 将 *值的*位的数目。  
  
## 返回值  
 两个函数返回一个值。  无错误返回。  
  
## 备注  
 `_lrotl` 和 `_lrotr` 函数。`shift` 位旋转 *值*。  `_lrotl` 旋转值。  `_lrotr` 旋转值权限。  两位包装函数旋转 *值* 结束到另一端。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_lrotl`|\<stdlib.h\>|  
|`_lrotr`|\<stdlib.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_lrot.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   unsigned long val = 0x0fac35791;  
  
   printf( "0x%8.8lx rotated left eight times is 0x%8.8lx\n",   
            val, _lrotl( val, 8 ) );  
   printf( "0x%8.8lx rotated right four times is 0x%8.8lx\n",   
            val, _lrotr( val, 4 ) );  
}  
```  
  
## Output  
  
```  
0xfac35791 rotated left eight times is 0xc35791fa  
0xfac35791 rotated right four times is 0x1fac3579  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [\_rotl、\_rotl64、\_rotr、\_rotr64](../../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)