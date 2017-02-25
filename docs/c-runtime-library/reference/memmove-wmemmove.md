---
title: "memmove、wmemmove | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "memmove"
  - "wmemmove"
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
  - "ntdll.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "memmove"
  - "wmemmove"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "memmove 函数"
  - "wmemmove 函数"
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# memmove、wmemmove
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

移动一缓冲区到另一种缓冲区。  提供这些函数的更多安全版本；请参见 [memmove\_s、wmemmove\_s](../../c-runtime-library/reference/memmove-s-wmemmove-s.md)。  
  
## 语法  
  
```  
void *memmove(  
   void *dest,  
   const void *src,  
   size_t count   
);  
wchar_t *wmemmove(  
   wchar_t *dest,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### 参数  
 `dest`  
 目标对象。  
  
 `src`  
 源对象。  
  
 `count`  
 复制 \(`memmove`\) 的字节数或字符 \(`wmemmove`\)。  
  
## 返回值  
 `dest` *.* 的值。  
  
## 备注  
 从`src`复制 `count` 字节\(`memmove`\) 或字符\(`wmemmove`\) 到 `dest`*.*。如果源区的某些区域与目标的重叠，函数确保了在重叠区域中的原始源字节在覆盖之前被复制。  
  
 **Security Note**，确保目标缓冲区的大小和源缓冲区大小相同。  有关更多信息，请参见[避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
 如果常数`_CRT_SECURE_DEPRECATE_MEMORY`先于声明定义以便否决函数，`memmove` 和 `wmemmove` 函数才会被否决，如下面的示例所示：  
  
```  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <string.h>  
or  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <wchar.h>  
```  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`memmove`|\<string.h\>|  
|`wmemmove`|\<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_memcpy.c  
// Illustrate overlapping copy: memmove  
// always handles it correctly; memcpy may handle  
// it correctly.  
//  
  
#include <memory.h>  
#include <string.h>  
#include <stdio.h>  
  
char str1[7] = "aabbcc";  
  
int main( void )  
{  
   printf( "The string: %s\n", str1 );  
   memcpy( str1 + 2, str1, 4 );  
   printf( "New string: %s\n", str1 );  
  
   strcpy_s( str1, sizeof(str1), "aabbcc" );   // reset string  
  
   printf( "The string: %s\n", str1 );  
   memmove( str1 + 2, str1, 4 );  
   printf( "New string: %s\n", str1 );  
}  
```  
  
  **字符串：aabbcc**  
**新字符串：aaaabb**  
**字符串：aabbcc**  
**新字符串：aaaabb**   
## .NET Framework 等效项  
 [System::Buffer::BlockCopy](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx)  
  
## 请参阅  
 [缓冲区操作](../../c-runtime-library/buffer-manipulation.md)   
 [\_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memcpy、wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)