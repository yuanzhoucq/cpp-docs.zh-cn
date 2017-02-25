---
title: "_mktemp_s、_wmktemp_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mktemp_s"
  - "_wmktemp_s"
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
  - "wmktemp_s"
  - "mktemp_s"
  - "_mktemp_s"
  - "_wmktemp_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mktemp_s 函数"
  - "_tmktemp_s 函数"
  - "_wmktemp_s 函数"
  - "文件 [C++], 临时"
  - "mktemp_s 函数"
  - "临时文件 [C++]"
  - "tmktemp_s 函数"
  - "wmktemp_s 函数"
ms.assetid: 92a7e269-7f3d-4c71-bad6-14bc827a451d
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _mktemp_s、_wmktemp_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建唯一的文件名。  [\_mktemp、\_wmktemp](../../c-runtime-library/reference/mktemp-wmktemp.md) 的一些版本提供安全增强功能（如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
errno_t _mktemp_s(  
   char *template,  
   size_t sizeInChars  
);  
errno_t _wmktemp_s(  
   wchar_t *template,  
   size_t sizeInChars  
);  
template <size_t size>  
errno_t _mktemp_s(  
   char (&template)[size]  
); // C++ only  
template <size_t size>  
errno_t _wmktemp_s(  
   wchar_t (&template)[size]  
); // C++ only  
```  
  
#### 参数  
 `template`  
 文件名模式。  
  
 `sizeInChars`  
 在 `_mktemp_s`单字节字符缓冲区的大小; `_wmktemp_s`中宽字符，其中包括空终结器。  
  
## 返回值  
 成功时这两个函数返回零；失败时返回错误代码。  
  
### 错误情况  
  
|`template`|`sizeInChars`|**返回值**|**模板的新值**|  
|----------------|-------------------|-------------|---------------|  
|`NULL`|any|`EINVAL`|`NULL`|  
|不正确的格式 \(参见 `Remarks` 节中正确的格式\)|any|`EINVAL`|空字符串|  
|any|\<\= X's 的数字|`EINVAL`|空字符串|  
  
 如果任一以上错误状态发生，调用无效参数句柄，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行，将 `EINVAL` 设置为 `errno`，并函数返回  `EINVAL`。  
  
## 备注  
 `_mktemp_s` 函数通过修改 `template` 参数创建唯一文件名，因此，在调用后，`template`指针指向一个包含新的文件名之后的字符串的指针。  `_mktemp_s` 自动处理合适的多字节字符串参数，通过运行时系统根据当前使用的多字节代码页识别多字节字符序列.  `_wmktemp_s` 是 `_mktemp_s` 的宽字符版本；`_wmktemp_s` 的参数是宽字符串。  `_wmktemp_s` 和 `_mktemp_s` 具有相同的行为，但 `_wmktemp_s` 不处理多字节字符字符串。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tmktemp_s`|`_mktemp_s`|`_mktemp_s`|`_wmktemp_s`|  
  
 `template` 参数包含窗体 `baseXXXXXX`，`base` 是新的文件名部分来提供，并且每个 x 为 `_mktemp_s`提供的字符的占位符。  `template` 中的每个占位符字符必须是大写 X。  `_mktemp_s` 保留 `base` 并替换字母表的第一个尾随 X。  `_mktemp_s` 用五位数值替换以下跟踪 X's;此值是一个调用进程唯一标示符，或在多线程程序中，调用线程。  
  
 对 `_mktemp_s` 的每次成功的调用修改 `template`。  在每一个后来调用的相同进程或线程的有和 `template`一样的参数，`_mktemp_s` 检查文件名匹配以前的调用 `_mktemp_s` 返回的名称。  如果给定名称的文件不存在， `_mktemp_s` 返回名称。  如果文件存在所有先前返回的名字，`_mktemp_s` 通过替换字母创建一个新名字。先前返回名字与下一个可用小写字母，按顺序，从“a”到“z”。  例如，如果 `base`：  
  
```  
fn  
```  
  
 而 `_mktemp_s` 提供五位数的值为 12345，则返回的名称为：  
  
```  
fna12345  
```  
  
 如果该名称用于创建文件 FNA12345，且此文件保存，调用从相同的进程或线程返回名字使和 `base` `template` 的是：  
  
```  
fnb12345  
```  
  
 如果 FNA12345 不存在，再一次返回下一个名字：  
  
```  
fna12345  
```  
  
 `_mktemp_s` 可以从任何给定的基本和模板特定值的所有组合创建最多 26 个唯一的文件名。  因此，FNZ12345 是最后唯一文件名 `_mktemp_s` 可为 `base` 和 `template` 在实例中创建值。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关更多信息，请参见[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_mktemp_s`|\<io.h\>|  
|`_wmktemp_s`|\<io.h\> or \<wchar.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_mktemp_s.cpp  
/* The program uses _mktemp to create  
 * five unique filenames. It opens each filename  
 * to ensure that the next name is unique.  
 */  
  
#include <io.h>  
#include <string.h>  
#include <stdio.h>  
  
char *fnTemplate = "fnXXXXXX";  
char names[5][9];  
  
int main()  
{  
   int i, err, sizeInChars;  
   FILE *fp;  
  
   for( i = 0; i < 5; i++ )  
   {  
      strcpy_s( names[i], sizeof(names[i]), fnTemplate );  
      /* Get the size of the string and add one for the null terminator.*/  
      sizeInChars = strnlen(names[i], 9) + 1;  
      /* Attempt to find a unique filename: */  
      err = _mktemp_s( names[i], sizeInChars );  
      if( err != 0 )  
         printf( "Problem creating the template" );  
      else  
      {  
         if( fopen_s( &fp, names[i], "w" ) == 0 )  
            printf( "Unique filename is %s\n", names[i] );  
         else  
            printf( "Cannot open %s\n", names[i] );  
         fclose( fp );  
      }  
   }  
  
   return 0;  
}  
```  
  
## 示例输出  
  
```  
Unique filename is fna03188  
Unique filename is fnb03188  
Unique filename is fnc03188  
Unique filename is fnd03188  
Unique filename is fne03188  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_getpid](../../c-runtime-library/reference/getpid.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [\_tempnam、\_wtempnam、tmpnam、\_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [tmpfile\_s](../../c-runtime-library/reference/tmpfile-s.md)