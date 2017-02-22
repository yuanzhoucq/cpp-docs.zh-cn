---
title: "rewind | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "rewind"
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
  - "rewind"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "文件指针 [C++]"
  - "文件指针 [C++], 重定位"
  - "重定位文件指针"
  - "rewind 函数"
ms.assetid: 1a460ce1-28d8-4b5e-83a6-633dca29c28a
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# rewind
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重新定位文件指针到文件开头。  
  
## 语法  
  
```  
  
      void rewind(  
   FILE *stream   
);  
```  
  
#### 参数  
 `stream`  
 指向 **FILE** 结构的指针。  
  
## 备注  
 **倒带** 函数重新定位文件指针与 `stream` 语句添加到文件开头。  对 **倒带** 的一个调用相似。  
  
 **\(void\) fseek\(** `stream`**, 0L,** `SEEK_SET` **\);**  
  
 但是，与 `fseek`不同的是，**倒带** 的错误指示器和清除流文件尾指示符。  此外，与 `fseek`不同的是，**倒带** 不返回值指明指针是否成功移动。  
  
 清除键盘缓冲区，用 `stdin`的流使用与键盘默认情况下，**倒带**  
  
 如果 `NULL`是指针，无效参数处理器程序，将按   [参数验证](../../c-runtime-library/parameter-validation.md)中所述进行调用。  如果允许执行继续，则这些函数将返回并将`errno`设置为 `EINVAL`。  
  
 有关这些属性和其他错误代码的信息，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|**rewind**|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_rewind.c  
/* This program first opens a file named  
 * crt_rewind.out for input and output and writes two  
 * integers to the file. Next, it uses rewind to  
 * reposition the file pointer to the beginning of  
 * the file and reads the data back in.  
 */  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   int data1, data2;  
  
   data1 = 1;  
   data2 = -37;  
  
   fopen_s( &stream, "crt_rewind.out", "w+" );  
   if( stream != NULL )  
   {  
      fprintf( stream, "%d %d", data1, data2 );  
      printf( "The values written are: %d and %d\n", data1, data2 );  
      rewind( stream );  
      fscanf_s( stream, "%d %d", &data1, &data2 );  
      printf( "The values read are: %d and %d\n", data1, data2 );  
      fclose( stream );  
   }  
}  
```  
  
## Output  
  
```  
The values written are: 1 and -37  
The values read are: 1 and -37  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)