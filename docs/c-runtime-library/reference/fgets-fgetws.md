---
title: "fgets、fgetws | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fgets"
  - "fgetws"
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
  - "_fgetts"
  - "fgetws"
  - "fgets"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fgetts 函数"
  - "fgets 函数"
  - "fgetts 函数"
  - "fgetws 函数"
  - "流, 获取字符串自"
  - "流, 读取自"
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fgets、fgetws
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从流获取字符串。  
  
## 语法  
  
```  
char *fgets(   
   char *str,  
   int n,  
   FILE *stream   
);  
wchar_t *fgetws(   
   wchar_t *str,  
   int n,  
   FILE *stream   
);  
```  
  
#### 参数  
 `str`  
 数据的存储位置。  
  
 `n`  
 要读取的最大字符数  
  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 这些函数都返回`str`。  `NULL` 返回指示的错误或一个文件的结尾。  使用 `feof` 或 `ferror` 来确定是否发生了错误。  如果`str` 或 `stream` 是一个 null 指针， 或者如果 `n` 小于等于零，这些函数将调用无效参数处理程序， 正如[参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回`NULL`。  
  
 有关这些内容的更多信息以及其他错误代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `fgets` 函数读取输入 `stream` 参数的字符串并将其存储到 `str`中。  `fgets` 读取从当前流位置的字符，并且包括第一个字符，到流的末尾，或直至读取字符数 \- 1 与 `n` 相等。  存储在 `str` 中追加 null 字符。  如果读取，换行字符包括在字符串中。  
  
 `fgetws` 是 `fgets`的宽字符版本。  
  
 `fgetws` 读取宽字符参数 `str`作为多字节字符字符串或宽字符字符串，并根据 `stream` 是否在文本模式或二进制模式打开， 分别复制宽字符参数。  更多关于在统一字符标准下的使用文本和二进制模式，以及多字节输入\/输出信息，请参见 [文本和二进制模式文件输入\/输出](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和 [统一字符标准下的文本及二进制模式输入\/输出](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md).  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义的 \_UNICODE & 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|-------------------------------|----------------|-------------------|  
|`_fgetts`|`fgets`|`fgets`|`fgetws`|  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fgets`|\<stdio.h\>|  
|`fgetws`|\<stdio.h\> 或 \<wchar.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fgets.c  
// This program uses fgets to display  
// a line from a file on the screen.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char line[100];  
  
   if( fopen_s( &stream, "crt_fgets.txt", "r" ) == 0 )  
   {  
      if( fgets( line, 100, stream ) == NULL)  
         printf( "fgets error\n" );  
      else  
         printf( "%s", line);  
      fclose( stream );  
   }  
}  
```  
  
## Input: crt\_fgets.txt  
  
```  
Line one.  
Line two.  
```  
  
### Output  
  
```  
Line one.  
```  
  
## .NET Framework 等效项  
  
-   [System::IO::StreamReader::ReadLine](https://msdn.microsoft.com/en-us/library/system.io.streamreader.readline.aspx).  
  
-   [System::IO::TextReader::ReadBlock](https://msdn.microsoft.com/en-us/library/system.io.textreader.readblock.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fputs、fputws](../../c-runtime-library/reference/fputs-fputws.md)   
 [gets、\_getws](../../c-runtime-library/gets-getws.md)   
 [puts、\_putws](../../c-runtime-library/reference/puts-putws.md)