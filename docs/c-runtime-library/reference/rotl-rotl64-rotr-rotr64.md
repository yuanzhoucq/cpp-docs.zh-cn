---
title: "_rotl、_rotl64、_rotr、_rotr64 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_rotr64"
  - "_rotl"
  - "_rotr"
  - "_rotl64"
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
  - "_rotr64"
  - "rotl64"
  - "_rotl64"
  - "rotr64"
  - "rotr"
  - "_rotr"
  - "_rotl"
  - "rotl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_rotl 函数"
  - "_rotl64 函数"
  - "_rotr 函数"
  - "_rotr64 函数"
  - "位, 旋转"
  - "旋转位"
  - "rotl 函数"
  - "rotl64 函数"
  - "rotr 函数"
  - "rotr64 函数"
ms.assetid: cfce439b-366f-4584-8ab1-d527b13fcfc6
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _rotl、_rotl64、_rotr、_rotr64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

旋转位到左边 \(`_rotl`\) 右侧或 \(`_rotr`\)。  
  
## 语法  
  
```  
  
      unsigned int _rotl(  
   unsigned int value,  
   int shift   
);  
unsigned __int64 _rotl64(  
   unsigned __int64 value,   
   int shift  
);  
unsigned int _rotr(  
   unsigned int value,  
   int shift   
);  
unsigned __int64 _rotr64(  
   unsigned __int64 value,  
   int shift  
);  
```  
  
#### 参数  
 *值*  
 将旋转的值。  
  
 `shift`  
 移动位的数目。  
  
## 返回值  
 旋转的值。  无错误返回。  
  
## 备注  
 `_rotl` 和 `_rotr` 函数。`shift` 旋转位无符号 *值*。  `_rotl` 旋转值。  `_rotr` 旋转值权限。  两位包装函数旋转 *值* 结束到另一端。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|**\_rotl，\_rotl64**|\<stdlib.h\>|  
|**\_rotr，\_rotr64**|\<stdlib.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_rot.c  
/* This program shifts values to rotate an integer.  
 */  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   unsigned val = 0x0fd93;  
   __int64 val2 = 0x0101010101010101;  
  
   printf( "0x%4.4x rotated left three times is 0x%4.4x\n",   
           val, _rotl( val, 3 ) );  
   printf( "0x%4.4x rotated right four times is 0x%4.4x\n",   
           val, _rotr( val, 4 ) );  
  
   printf( "%I64x rotated left three times is %I64x\n",  
           val2, _rotl64( val2, 3 ) );  
   printf( "%I64x rotated right four times is %I64x\n",   
           val2, _rotr64( val2, 4 ) );  
}  
```  
  
## Output  
  
```  
0xfd93 rotated left three times is 0x7ec98  
0xfd93 rotated right four times is 0x30000fd9  
101010101010101 rotated left three times is 808080808080808  
101010101010101 rotated right four times is 1010101010101010  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [\_lrotl、\_lrotr](../../c-runtime-library/reference/lrotl-lrotr.md)