---
title: "memcpy_s、wmemcpy_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "memcpy_s"
  - "wmemcpy_s"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wmemcpy_s"
  - "memcpy_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "memcpy_s 函数"
  - "wmemcpy_s 函数"
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# memcpy_s、wmemcpy_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在缓冲区之间复制字节。 一些版本 [memcpy、wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) 因安全性增强中所述 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 语法  
  
```  
errno_t memcpy_s(  
   void *dest,  
   size_t destSize,  
   const void *src,  
   size_t count   
);  
errno_t wmemcpy_s(  
   wchar_t *dest,  
   size_t destSize,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### 参数  
 `dest`  
 新缓冲区。  
  
 `destSize`  
 目标缓冲区，以字节为单位 memcpy\_s 和 wmemcpy\_s 的宽字符 \(wchar\_t\) 的大小。  
  
 `src`  
 从中进行复制操作的缓冲区。  
  
 `count`  
 要复制的字符数。  
  
## 返回值  
 如果成功，则为零；如果失败，则为错误代码。  
  
### 错误条件  
  
|`dest`|`destSize`|`src`|返回值|`dest` 的内容|  
|------------|----------------|-----------|---------|----------------|  
|`NULL`|any|any|`EINVAL`|未修改|  
|any|any|`NULL`|`EINVAL`|`dest` 归零|  
|any|\< `count`|any|`ERANGE`|`dest` 归零|  
  
## 备注  
 `memcpy_s` 从 `count` 中将 `src` 个字节复制到 `dest` 中；`wmemcpy_s` 复制 `count` 个宽字符（两个字节）。 如果源和目标重叠，则 `memcpy_s` 的行为是未定义的。 使用 `memmove_s` 处理重叠区域。  
  
 这些函数验证其参数。 如果 `dest` 或 `src` 是 null 指针，或 `destSize` 小于 `count`, ，这些函数将调用无效参数处理程序，如中所述 [参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将返回 `EINVAL` 并将 `errno` 设置为 `EINVAL`。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`memcpy_s`|\<memory.h\> 或 \<string.h\>|  
|`wmemcpy_s`|\<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_memcpy_s.c  
// Copy memory in a more secure way.  
  
#include <memory.h>  
#include <stdio.h>  
  
int main()  
{  
   int a1[10], a2[100], i;  
   errno_t err;  
  
   // Populate a2 with squares of integers  
   for (i = 0; i < 100; i++)  
   {  
      a2[i] = i*i;  
   }  
  
   // Tell memcpy_s to copy 10 ints (40 bytes), giving  
   // the size of the a1 array (also 40 bytes).  
   err = memcpy_s(a1, sizeof(a1), a2, 10 * sizeof (int) );      
   if (err)  
   {  
      printf("Error executing memcpy_s.\n");  
   }  
   else  
   {  
     for (i = 0; i < 10; i++)  
       printf("%d ", a1[i]);  
   }  
   printf("\n");  
}  
```  
  
```Output  
0 1 4 9 16 25 36 49 64 81   
```  
  
## .NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [缓冲区操作](../../c-runtime-library/buffer-manipulation.md)   
 [\_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memchr、wmemchr](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcmp、wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memmove、wmemmove](../../c-runtime-library/reference/memmove-wmemmove.md)   
 [memset、wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcpy、wcscpy、\_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [strncpy\_s、\_strncpy\_s\_l、wcsncpy\_s、\_wcsncpy\_s\_l、\_mbsncpy\_s、\_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)