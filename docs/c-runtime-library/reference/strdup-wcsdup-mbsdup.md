---
title: "_strdup、_wcsdup、_mbsdup | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strdup"
  - "_mbsdup"
  - "_wcsdup"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tcsdup"
  - "mbsdup"
  - "_mbsdup"
  - "_strdup"
  - "_ftcsdup"
  - "_wcsdup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "wcsdup 函数"
  - "ftcsdup 函数"
  - "_ftcsdup 函数"
  - "mbsdup 函数"
  - "strdup 函数"
  - "_strdup 函数"
  - "_wcsdup 函数"
  - "复制字符串"
  - "重复字符串"
  - "复制字符串 [c + +]"
  - "_mbsdup 函数"
  - "复制字符串 [c + +]"
  - "tcsdup 函数"
  - "_tcsdup 函数"
ms.assetid: 8604f8bb-95e9-45d3-93ef-20397ebf247a
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _strdup、_wcsdup、_mbsdup
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

复制字符串。  
  
> [!IMPORTANT]
>  `_mbsdup` 无法用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。 有关详细信息，请参阅 [\/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
char *_strdup(  
   const char *strSource   
);  
wchar_t *_wcsdup(  
   const wchar_t *strSource   
);  
unsigned char *_mbsdup(  
   const unsigned char *strSource   
);  
```  
  
#### 参数  
 `strSource`  
 null 终止的源字符串。  
  
## 返回值  
 如果无法分配存储，则其中每个函数都将返回一个指向复制字符串的存储位置的指针或 `NULL`。  
  
## 备注  
 `_strdup` 函数调用 [malloc](../../c-runtime-library/reference/malloc.md) 来为 `strSource` 的副本分配存储空间，然后将 `strSource` 复制到分配的空间。  
  
 `_wcsdup` 和 `_mbsdup` 分别是 `_strdup` 的宽字符及多字节字符版本。`_wcsdup` 的参数和返回值是宽字符字符串；而 `_mbsdup` 的则是多字节字符字符串。 否则这三个函数否则具有相同行为。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcsdup`|`_strdup`|`_mbsdup`|`_wcsdup`|  
  
 因为 `_strdup` 调用 `malloc` 来为 `strSource` 的副本分配存储空间，所以最好始终通过调用由对 `_strdup` 的调用返回的指针上的[空闲](../../c-runtime-library/reference/free.md)例程来释放此内存。  
  
 如果定义了 `_DEBUG` 和 `_CRTDBG_MAP_ALLOC`，则将由对 `_strdup_dbg` 和 `_wcsdup_dbg` 的调用来替换 `_strdup` 和 `_wcsdup`，从而允许调试内存分配。 有关详细信息，请参阅 [\_strdup\_dbg、\_wcsdup\_dbg](../../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_strdup`|\<string.h\>|  
|`_wcsdup`|\<string.h\> 或 \<wchar.h\>|  
|`_mbsdup`|\<mbstring.h\>|  
  
 有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_strdup.c  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char buffer[] = "This is the buffer text";  
   char *newstring;  
   printf( "Original: %s\n", buffer );  
   newstring = _strdup( buffer );  
   printf( "Copy:     %s\n", newstring );  
   free( newstring );  
}  
```  
  
```Output  
原始：这是缓冲区文本 副本：这是缓冲区文本  
```  
  
## .NET Framework 等效项  
 [System::String::Clone](https://msdn.microsoft.com/en-us/library/system.string.clone.aspx)  
  
## 请参阅  
 [字符串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [memset、wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcat、wcscat、\_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp、wcscmp、\_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncat、\_strncat\_l、wcsncat、\_wcsncat\_l、\_mbsncat、\_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp、wcsncmp、\_mbsncmp、\_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy、\_strncpy\_l、wcsncpy、\_wcsncpy\_l、\_mbsncpy、\_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp、\_wcsnicmp、\_mbsnicmp、\_strnicmp\_l、\_wcsnicmp\_l、\_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr、wcsrchr、\_mbsrchr、\_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)