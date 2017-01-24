---
title: "tmpfile_s | Microsoft Docs"
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
  - "tmpfile_s"
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
  - "tmpfile_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "临时文件"
  - "tmpfile_s 函数"
  - "临时文件, 创建"
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tmpfile_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建一个临时文件：  [tmpfile](../../c-runtime-library/reference/tmpfile.md) 的安全增强版本，如[CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## 语法  
  
```  
errno_t tmpfile_s(  
   FILE** pFilePtr  
);  
```  
  
#### 参数  
 \[out\] `pFilePtr`  
 存储流的生成的指针地址的指针地址。  
  
## 返回值  
 如果成功，则返回零；如果失败，则返回错误代码。  
  
### 错误情况  
  
|`pFilePtr`|**返回值**|**Contents of**  `pFilePtr`|  
|----------------|-------------|---------------------------------|  
|`NULL`|`EINVAL`|不更改|  
  
 如果以上参数验证错误发生，则调用无效参数句柄，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则将 `errno` 设置为 `EINVAL`，并且返回值为`EINVAL`。  
  
## 备注  
 `tmpfile_s` 函数创建临时文件并在 `pFilePtr` 参数中放入指向该流的指针。  临时文件在根目录中创建。  若要创建目录中（非根目录）的一个临时文件，可与 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)一起使用[tmpnam\_s](../../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md)或[tempnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)。  
  
 如果文件无法打开，`tmpfile_s` 写 `NULL` 到 `pFilePtr` 参数。  该临时文件自动删除，当关闭文件，那么，当程序时通常停止，或者当调用 `_rmtmp` 后，假定，当前工作目录不更改。  临时文件在 `w+b` \(二进制\) 读\/可写模式打开。  
  
 如果尝试带有`tmpfile_s.`的`TMP_MAX_S`调用\(请参见STDIO.H），则可能失败。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`tmpfile_s`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
> [!NOTE]
>  此示例需要管理权限才能在 Windows Vista 上运行。  
  
```  
// crt_tmpfile_s.c  
// This program uses tmpfile_s to create a  
// temporary file, then deletes this file with _rmtmp.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char tempstring[] = "String to be written";  
   int  i;  
   errno_t err;  
  
   // Create temporary files.  
   for( i = 1; i <= 3; i++ )  
   {  
      err = tmpfile_s(&stream);  
      if( err )  
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