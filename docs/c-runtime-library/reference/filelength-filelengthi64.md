---
title: "_filelength、_filelengthi64 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_filelengthi64"
  - "_filelength"
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
  - "_filelength"
  - "_filelengthi64"
  - "filelengthi64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_filelength 函数"
  - "_filelengthi64 函数"
  - "filelength 函数"
  - "filelengthi64 函数"
  - "文件 [C++], length"
  - "长度, 文件"
ms.assetid: 3ab83d5a-543c-4079-b9d9-0abfc7da0275
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _filelength、_filelengthi64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

获取文件的长度。  
  
## 语法  
  
```  
long _filelength(   
   int fd   
);  
__int64 _filelengthi64(   
   int fd   
);  
```  
  
#### 参数  
 `fd`  
 针对文件说明符。  
  
## 返回值  
 `_filelength` 和 `_filelengthi64` 返回，与 `fd`相关的目标文件的字节长度。  如果 `fd` 是无效的文件说明符，此函数调用的无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许继续执行，这两个函数返回 \-1L指示错误，并将`errno` 设置为 `EBADF`。  
  
## 要求  
  
|功能|必需的标头|  
|--------|-----------|  
|`_filelength`|\<io.h\>|  
|`_filelengthi64`|\<io.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 请参见[\_chsize](../../c-runtime-library/reference/chsize.md)示例。  
  
## .NET Framework 等效项  
  
-   [System::IO::Stream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.stream.setlength.aspx)  
  
-   [System::IO::FileStream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.filestream.setlength.aspx)  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_chsize](../../c-runtime-library/reference/chsize.md)   
 [\_fileno](../../c-runtime-library/reference/fileno.md)   
 [\_fstat、\_fstat32、\_fstat64、\_fstati64、\_fstat32i64、\_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_fstat、\_fstat32、\_fstat64、\_fstati64、\_fstat32i64、\_fstat64i32](../../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)   
 [\_stat、\_wstat 函数](../../c-runtime-library/reference/stat-functions.md)   
 [\_stat、\_wstat 函数](../../c-runtime-library/reference/stat-functions.md)