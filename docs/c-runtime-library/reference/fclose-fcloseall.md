---
title: "fclose、_fcloseall | Microsoft Docs"
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
  - "fclose"
  - "_fcloseall"
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
  - "fclose"
  - "_fcloseall"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fclose 函数"
  - "流，正在关闭"
  - "_fcloseall 函数"
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fclose、_fcloseall
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

关闭了流 \(`fclose`\) 或任何打开关闭流 \(`_fcloseall`\)。  
  
## 语法  
  
```  
int fclose(   
   FILE *stream   
);  
int _fcloseall( void );  
```  
  
#### 参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 则流成功关闭，则`fclose` 返回 0。  `_fcloseall` 返回关闭流的总数。  指示两函数错误的返回 `EOF`。  
  
## 备注  
 `fclose` 函数的 `stream`。  如果 `stream` 是 `NULL`，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述。  如果允许执行继续，则将`fclose`设置`errno` t为`EINVAL` 并返回 `EOF`。  建议 `stream` 指针在调用此函数之前始终检查。  
  
 有关这些内容的更多信息以及其他错误代码，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `_fcloseall` 关闭所有多余函数 `stderr` \( `stdin`，`stdout`，此外，在 MS\-DOS，`_stdaux` 和 `_stdprn`\) 的流打开。  还可以关闭并删除所有 `tmpfile`创建的临时文件。  在两种函数中，所有缓存与流在关闭之前刷新。  当关闭了流时，系统分配的缓冲区被释放。  具有 `setbuf` 和 `setvbuf` 的用户分配缓冲区不自动释放。  
  
 **注意：**，则这些函数用于关闭流时，基础文件说明符和操作系统句柄 \(或文件\)，以及套接字关闭流。  因此，如果文件初会打开为文件句柄或文件描述符和关闭使用 `fclose`，也不要调用 `_close` 关闭文件说明符；请勿调用 Win32 函数 `CloseHandle` 关闭文件的句柄。  
  
 `fclose` 并防止代码的 `_fcloseall` 应用程序受到其他线程的干扰。  有关非固定版本`fclose`，请参见 `_fclose_nolock`。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`fclose`|\<stdio.h\>|  
|`_fcloseall`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见[\_fopen](../../c-runtime-library/reference/fopen-wfopen.md)示例。  
  
## .NET Framework 等效项  
  
-   [System::IO::BinaryReader::Close](https://msdn.microsoft.com/en-us/library/system.io.binaryreader.close.aspx)  
  
-   [System::IO::BinaryWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.binarywriter.close.aspx)  
  
-   [System::IO::StringReader::Close](https://msdn.microsoft.com/en-us/library/system.io.stringreader.close.aspx)  
  
-   [System::IO::StringWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.stringwriter.close.aspx)  
  
-   [System::IO::Stream::Close](https://msdn.microsoft.com/en-us/library/system.io.stream.close.aspx)  
  
-   [System::IO::StreamReader::Close](https://msdn.microsoft.com/en-us/library/system.io.streamreader.close.aspx)  
  
-   [System::IO::StreamWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.close.aspx)  
  
-   [System::IO::TextReader::Close](https://msdn.microsoft.com/en-us/library/system.io.textreader.close.aspx)  
  
-   [System::IO::TextWriter::Close](https://msdn.microsoft.com/en-us/library/system.io.textwriter.close.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_fdopen、\_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen、\_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)