---
title: "fputs、fputws | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fputs"
  - "fputws"
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
  - "fputs"
  - "fputws"
  - "_fputts"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fputts 函数"
  - "fputs 函数"
  - "fputts 函数"
  - "fputws 函数"
  - "流, 将字符串写入到"
ms.assetid: d48c82b8-aa17-4830-8c7d-30442ddbb326
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# fputs、fputws
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符串写入流。  
  
## 语法  
  
```  
int fputs(   
   const char *str,  
   FILE *stream   
);  
int fputws(   
   const wchar_t *str,  
   FILE *stream   
);  
```  
  
#### 参数  
 `str`  
 输出字符串  
  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 如果它是成功的，这些函数都返回一个非负值。  发生错误时，`fputs` 和 `fputws` 返回 `EOF`。  如果 `str` 或 `stream` 是 null 指针，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则这些函数将`errno` 设置为`EINVAL`，接着`fputs` 返回 `EOF`,  `fputws` 返回 `WEOF`。  
  
 有关这些内容的更多信息以及其他错误代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 在当前位置，这些函数中都复制`str` 到输出 `stream` 。  作为多字节字符字符串或宽字符字符串，并根据`stream` 是否在文本模式或二进制模式打开，`fputws` 分别复制宽字符参数 `str` 到 `stream`。  两个函数都不复制终止 null 字符。  
  
 如果流在 ANSI 模式中打开，这两个函数具有相同的行为。  `fputs` 当前不支持输出到 UNICODE 流。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_fputts`|`fputs`|`fputs`|`fputws`|  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fputs`|\<stdio.h\>|  
|`fputws`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_fputs.c  
// This program uses fputs to write  
// a single line to the stdout stream.  
  
#include <stdio.h>  
  
int main( void )  
{  
   fputs( "Hello world from fputs.\n", stdout );  
}  
```  
  
  **Hello world从 fputs输出。**   
## .NET Framework 等效项  
 [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fgets、fgetws](../../c-runtime-library/reference/fgets-fgetws.md)   
 [gets、\_getws](../../c-runtime-library/gets-getws.md)   
 [puts、\_putws](../../c-runtime-library/reference/puts-putws.md)