---
title: "tmpnam_s、_wtmpnam_s | Microsoft Docs"
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
  - "tmpnam_s"
  - "_wtmpnam_s"
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
  - "tmpnam_s"
  - "_wtmpnam_s"
  - "L_tmpnam_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_wtmpnam_s 函数"
  - "文件名 [C++], 创建临时"
  - "文件名 [C++], 临时"
  - "L_tmpnam_s 常量"
  - "临时文件, 创建"
  - "tmpnam_s 函数"
  - "wtmpnam_s 函数"
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tmpnam_s、_wtmpnam_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

生成可用来创建临时文件的名称。  [](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md "_tempnam, _wtempnam, tmpnam, _wtmpnam")[CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
errno_t tmpnam_s(  
   char * str,  
   size_t sizeInChars   
);  
errno_t _wtmpnam_s(  
   wchar_t *str,  
   size_t sizeInChars   
);  
template <size_t size>  
errno_t tmpnam_s(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _wtmpnam_s(  
   wchar_t (&str)[size]  
); // C++ only  
```  
  
#### 参数  
 \[out\] `str`  
 将保存生成的名称上。  
  
 \[in\] `sizeInChars`  
 缓冲区的大小（以字节为单位）。  
  
## 返回值  
 这两个函数返回 0，则在成功或失败的错误号。  
  
### 错误情况  
  
|||||  
|-|-|-|-|  
|`str`|`sizeInChars`|**返回值**|**Contents of**  `str`|  
|`NULL`|any|`EINVAL`|未修改|  
|不是 `NULL` \(指向有效的内存\)|太短|`ERANGE`|未修改|  
  
 如果 `str` 是 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许继续执行，则这些函数将 `errno` 设置为 `EINVAL`，并返回`EINVAL`。  
  
## 备注  
 这些函数中的每个表达式都返回当前不存在的文件名。  `tmpnam_s` 返回名称唯一在当前工作目录。  请注意，当文件名前面附有反斜杠且无路径信息时，如\\fname21 ，这说明名称在当前工作目录中是有效的。  
  
 对于 `tmpnam_s`，可以在 `str`中存储此生成的文件名。  `tmpnam_s` 返回的字符串的最大长度为 `L_tmpnam_s`，并定义在 STDIO.H。  如果 `str` 为 `NULL`，则`tmpnam_s`将此结果保留在内部静态缓冲区。  因此任何后续调用都会销毁此值。  `tmpnam_s` 生成的名称包含程序生成的文件名，在首次调用`tmpnam_s`后，序号文件扩展名在基 32 \(.1\-.1vvvvvu，在 STDIO.H 的 `TMP_MAX_S` 为 32,767\)。  
  
 `tmpnam_s` 和自动处理多字节字符串参数，并根据操作系统获得的 OEM 代码页识别多字节字符序列。  `_wsetlocale_wtmpnam_s`  是 `tmpnam_s`  的宽字符版本，`_wtmpnam_s` 参数和 的返回值都是宽字符字符串。  `_wtmpnam_s` 和 `tmpnam_s` 具有相同的行为，但 `_wtmpnam_s` 不处理多字节字符字符串。  
  
 在 C\+\+ 中，使用这些函数是由重载模板简化；该重载可以自动推断缓冲区长度，而无需指定范围参数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|\_UNICODE & \_MBCS not defined|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|------------------------------------|----------------|-------------------|  
|`_ttmpnam_s`|`tmpnam_s`|`tmpnam_s`|`_wtmpnam_s`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`tmpnam_s`|\<stdio.h\>|  
|`_wtmpnam_s`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_tmpnam_s.c  
// This program uses tmpnam_s to create a unique filename in the  
// current working directory.   
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{     
   char name1[L_tmpnam_s];  
   errno_t err;  
   int i;  
  
   for (i = 0; i < 15; i++)  
   {  
      err = tmpnam_s( name1, L_tmpnam_s );  
      if (err)  
      {  
         printf("Error occurred creating unique filename.\n");  
         exit(1);  
      }  
      else  
      {  
         printf( "%s is safe to use as a temporary file.\n", name1 );  
      }  
   }    
}  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile\_s](../../c-runtime-library/reference/tmpfile-s.md)