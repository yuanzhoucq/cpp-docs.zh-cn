---
title: "_tempnam、_wtempnam、tmpnam、_wtmpnam | Microsoft Docs"
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
  - "_wtempnam"
  - "_wtmpnam"
  - "tmpnam"
  - "_tempnam"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wtempnam"
  - "_wtmpnam"
  - "wtmpnam"
  - "tmpnam"
  - "_wtempnam"
  - "_tempnam"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tempnam 函数"
  - "_ttmpnam 函数"
  - "_wtempnam 函数"
  - "_wtmpnam 函数"
  - "文件名 [C++], 创建临时"
  - "文件名 [C++], 临时"
  - "tempnam 函数"
  - "临时文件, 创建"
  - "tmpnam 函数"
  - "ttmpnam 函数"
  - "wtempnam 函数"
  - "wtmpnam 函数"
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _tempnam、_wtempnam、tmpnam、_wtmpnam
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成可用来创建临时文件的名称。  有关这些函数的更多安全版本，请参见 [tmpnam\_s、\_wtmpnam\_s](../../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)。  
  
## 语法  
  
```  
char *_tempnam(  
   const char *dir,  
   const char *prefix   
);  
wchar_t *_wtempnam(  
   const wchar_t *dir,  
   const wchar_t *prefix   
);  
char *tmpnam(  
   char *str   
);  
wchar_t *_wtmpnam(  
   wchar_t *str   
);  
```  
  
#### 参数  
 `prefix`  
 `_tempnam`返回名称前缀的字符串。  
  
 `dir`  
 如果没有TMP 环境变量，或者，TMP是无效的目录，则在文件名中使用该路径。  
  
 `str`  
 指针保存的生成的名称等效于函数返回的名称。  这是一种保存生成的名称的简便方式。  
  
## 返回值  
 如果失败了，这些函数每个都返回指向名称生成的指针或 `NULL`。  如果尝试超过`TMP_MAX`\(请参见STDIO.H\) 的 `tmpnam` 调用，或者使用 `_tempnam`，并在TMP 环境变量和`dir` 参数中指定无效的目录名称。  
  
> [!NOTE]
>  指针由 `tmpnam` 和 `_wtmpnam` 点返回到内部静态缓冲区。  不应当调用[free](../../c-runtime-library/reference/free.md) 释放这些指针。  需要调用`free`释放被`_tempnam` 和 `_wtempnam`分配的指针。  
  
## 备注  
 这些函数中的每个表达式都返回当前不存在的文件名。  `tmpnam` 返回当前工作目录的唯一名称，通过 `_tempnam` 可生成其他目录中的唯一名称。  请注意，当文件名前面附有反斜杠且无路径信息时，如\\fname21 ，这说明名称在当前工作目录中是有效的。  
  
 对于 `tmpnam`，可以在 `str`中存储此生成的文件名。  如果 `str` 为 `NULL`，则`tmpnam`将此结果保留在内部静态缓冲区。  因此任何后续调用都会销毁此值。  `tmpnam` 生成的名称包含程序生成的文件名，在首次调用`tmpnam`后，序号文件扩展名在基 32 \(.1\-.vvu ，在 STDIO.H 的 `TMP_MAX` 为 32,767\)。  
  
 `_tempnam` 将为以下规则选择的目录生成唯一的文件名：  
  
-   如果定义 TMP 环境变量，将其设置为有效目录名称，为 TMP 指定的目录生成唯一文件名。  
  
-   如果 TMP 环境变量未定义，或者设置为不存在的目录的名称，`_tempnam` 是使用 `dir` 参数作为它将生成唯一的路径。  
  
-   如果 TMP 环境变量未定义，或者设置为不存在的目录名称，并且，如果 `dir` 为 `NULL`，或设置为不存在的目录的名称，`_tempnam` 将使用当前工作目录生成唯一的名称。  当前，如果TMP和 `dir` 指定不存在的目录名称，则调用 `_tempnam` 函数将失败。  
  
 `_tempnam` 返回的名称将为 `prefix` 和序列号的串联，这将创建一个指定目录的唯一文件名。  `_tempnam` 生成没有扩展名的文件名。  `_tempnam`使用 [malloc](../../c-runtime-library/reference/malloc.md) 为文件名分配空间；当不再需要时，程序负责释放此空间。  
  
 `_tempnam` 和 `tmpnam` 自动处理多字节字符串参数，并根据操作系统获得的 OEM 代码页识别多字节字符序列。  `_wtempnam`  是 `_tempnam`  的宽字符版本，`_wtempnam` 的参数和返回值都是宽字符字符串。  `_wtempnam` 和 `_tempnam` 具有相同的行为，但 `_wtempnam` 不处理多字节字符字符串。  `_wsetlocale_wtmpnam`  是 `tmpnam`  的宽字符版本，`_wtmpnam` 参数和 的返回值都是宽字符字符串。  `_wtmpnam` 和 `tmpnam` 具有相同的行为，但 `_wtmpnam` 不处理多字节字符字符串。  
  
 如果定义 `_DEBUG` 和 `_CRTDBG_MAP_ALLOC`，`_tempnam` 和 `_wtempnam` 被[\_tempnam\_dbg 和\_wtempnam\_dbg](../../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md)调用替换。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE & 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|-------------------------------|----------------|-------------------|  
|`_ttmpnam`|`tmpnam`|`tmpnam`|`_wtmpnam`|  
|`_ttempnam`|`_tempnam`|`_tempnam`|`_wtempnam`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_tempnam`|\<stdio.h\>|  
|`_wtempnam`, `_wtmpnam`|\<stdio.h\> 或 \<wchar.h\>|  
|`tmpnam`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_tempnam.c  
// compile with: /W3  
// This program uses tmpnam to create a unique filename in the  
// current working directory, then uses _tempnam to create   
// a unique filename with a prefix of stq.   
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{     
   char* name1 = NULL;  
   char* name2 = NULL;  
  
   // Create a temporary filename for the current working directory:   
   if( ( name1 = tmpnam( NULL ) ) != NULL ) // C4996  
   // Note: tmpnam is deprecated; consider using tmpnam_s instead  
      printf( "%s is safe to use as a temporary file.\n", name1 );  
   else  
      printf( "Cannot create a unique filename\n" );  
  
   // Create a temporary filename in temporary directory with the  
   // prefix "stq". The actual destination directory may vary  
   // depending on the state of the TMP environment variable and  
   // the global variable P_tmpdir.     
  
   if( ( name2 = _tempnam( "c:\\tmp", "stq" ) ) != NULL )  
      printf( "%s is safe to use as a temporary file.\n", name2 );   
   else  
      printf( "Cannot create a unique filename\n" );  
  
   // When name2 is no longer needed :     
   if(name2)  
     free(name2);  
  
}  
```  
  
  **\\s1gk. 用作临时文件是安全的。**  
**C:\\DOCUME~1\\user\\LOCALS~1\\Temp\\2\\stq2 用作临时文件是安全的。**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)   
 [tmpfile\_s](../../c-runtime-library/reference/tmpfile-s.md)