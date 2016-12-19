---
title: "tmpfile | Microsoft Docs"
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
  - "tmpfile"
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
  - "tmpfile"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "临时文件"
  - "tmpfile 函数"
  - "临时文件, 创建"
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tmpfile
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建一个临时文件：  因为更安全版本可用，此函数已弃用；请参阅 [tmpfile\_s](../../c-runtime-library/reference/tmpfile-s.md)。  
  
## 语法  
  
```  
FILE *tmpfile( void );  
```  
  
## 返回值  
 如果成功，则返回 `tmpfile` 流指针。  否则，它返回 `NULL`（ 引用）。  
  
## 备注  
 `tmpfile` 函数创建临时文件并返回指向该流。  临时文件在根目录中创建。  若要创建目录中的一个临时文件，可与 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)[tmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) [tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) 或一起使用。  
  
 如果文件无法打开，`tmpfile` 会返回一个 `NULL` 指针。  该临时文件自动删除，当关闭文件，那么，当程序时通常停止，或者当调用 `_rmtmp` 后，假定，当前工作目录不更改。  临时文件在 `w+b` \(二进制\) 读\/可写模式打开。  
  
 如果你尝试更多TMP\_MAX \(请参见STDIO.H） 的 `tmpfile`调用则可能失败。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`tmpfile`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
> [!NOTE]
>  此示例需要管理权限才能在 Windows Vista 上运行。  
  
```  
// crt_tmpfile.c  
// compile with: /W3  
// This program uses tmpfile to create a  
// temporary file, then deletes this file with _rmtmp.  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   int  i;  
  
   // Create temporary files.  
   for( i = 1; i <= 3; i++ )  
   {  
      if( (stream = tmpfile()) == NULL ) // C4996  
      // Note: tmpfile is deprecated; consider using tmpfile_s instead  
         perror( "Could not open new temporary file\n" );  
      else  
         printf( "Temporary file %d was created\n", i );  
   }  
  
   // Remove temporary files.  
   printf( "%d temporary files deleted\n", _rmtmp() );  
}  
```  
  
  **临时文件 1 创建**  
**临时文件 2 创建**  
**临时文件 3 创建**  
**3 删除的临时文件**   
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_rmtmp](../../c-runtime-library/reference/rmtmp.md)   
 [\_tempnam、\_wtempnam、tmpnam、\_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)