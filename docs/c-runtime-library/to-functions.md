---
title: "to 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "To"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "大小写, 转换"
  - "字符, 转换"
  - "lowercase, 转换字符串"
  - "字符串转换, 大小写"
  - "字符串转换, 为不同的字符"
  - "到函数"
  - "大写, 转换字符串"
ms.assetid: f636a4c6-8c9f-4be2-baac-064f9dbae300
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# to 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果存在，每个**to** 函数及其关联的宏中，将单个字符转变到另一个字符。  
  
|||  
|-|-|  
|[\_\_toascii](../c-runtime-library/reference/toascii-toascii.md)|[toupper, \_toupper, towupper](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|  
|[tolower, \_tolower, towlower](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)||  
  
## 备注  
 **到** 函数和宏转换如下所示。  
  
|例程|宏|说明|  
|--------|-------|--------|  
|`__toascii`|`__toascii`|将 `c` 转换为 ASCII 字符|  
|`tolower`|`tolower`|如果合适，`c` 转换为小写字符|  
|`_tolower`|`_tolower`|`c` 转换为小写。|  
|`towlower`|无|将 `c` 强制转换为相应的宽字符小写字母|  
|`toupper`|`toupper`|如果合适，`c` 转换为大写字符|  
|`_toupper`|`_toupper`|将 `c` 转换为大写|  
|`towupper`|无|转换 c 到相应的宽字符大写字母|  
  
 若要使用宏，也定义为 **到** 例程的函数版本移除宏定义使用 `#undef` 指令或不包含 CTYPE.H。  如果使用 \/Za 编译器选项，编译器使用 `toupper` 或 `tolower`函数版本。  `toupper` 和 `tolower` 函数的声明在 STDLIB.H。  
  
 例程 `__toascii` 设置所有除了低序 7 位 `c` 为0，因此，转换的值表示 ASCII 字符集中的一个字符。  如果 `c` 已经表示 ASCII 字符，`c` 不更改。  
  
 `tolower` 和 `toupper` 例程：  
  
-   当前依赖于区域设置的 `LC_CTYPE` 类别 \(`tolower` 调用 `isupper`，并调用 `toupper` `islower`\)。  
  
-   请将 `c` 强制转换，如果`c` 代表在当前区域的相应的可变的字符，并且在相反的情况下为该区域设置提供。  否则，`c` 不更改。  
  
 `_tolower` 和 `_toupper` 例程：  
  
-   为 `tolower` 区域设置无关，较快的生成和 **toupper.**  
  
-   只有当 **isascii\(**`c`**\)** 并且 **大于\(**`c`**\)** 或 **小于\(**`c`**\)**, 分别为零，可以使用.  
  
-   如果`c`不是一个要转换的合适用例的ASCII字符，结果未定义。  
  
 `towlower` 和 `towupper` 函数会返回 `c` 的变换的复制，如果只有以下两个条件皆为非零值。  否则，`c` 不更改。  
  
-   `c` 为适合的情况的宽字符 \(即 `iswupper` 或 **iswlower,**，要分别为非零\)。  
  
-   具有目标用例的相应的宽字符 \(即要 `iswlower` 或 **iswupper,**，分别为非零\)。  
  
## 示例  
  
```  
// crt_toupper.c  
/* This program uses toupper and tolower to  
 * analyze all characters between 0x0 and 0x7F. It also  
 * applies _toupper and _tolower to any code in this  
 * range for which these functions make sense.  
 */  
  
#include <ctype.h>  
#include <string.h>  
  
char msg[] = "Some of THESE letters are Capitals.";  
char *p;  
  
int main( void )  
{  
   printf( "%s\n", msg );  
  
   /* Reverse case of message. */  
   for( p = msg; p < msg + strlen( msg ); p++ )  
   {  
      if( islower( *p ) )  
         putchar( _toupper( *p ) );  
      else if( isupper( *p ) )  
         putchar( _tolower( *p ) );  
      else  
         putchar( *p );  
   }  
}  
```  
  
  **Some of THESE letters are Capitals.**  
**sOME OF these LETTERS ARE cAPITALS.**   
## 请参阅  
 [数据转换](../c-runtime-library/data-conversion.md)   
 [区域设置](../c-runtime-library/locale.md)   
 [is、isw 例程](../c-runtime-library/is-isw-routines.md)