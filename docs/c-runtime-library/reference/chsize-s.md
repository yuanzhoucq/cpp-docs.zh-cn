---
title: "_chsize_s | Microsoft Docs"
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
  - "_chsize_s"
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
  - "chsize_s"
  - "_chsize_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_chsize_s 函数"
  - "chsize_s 函数"
  - "文件 [C++], 更改大小"
ms.assetid: d88d2e94-6e3b-42a5-8631-16ac4d82fa38
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _chsize_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

更改文件的大小。  [\_chsize](../../c-runtime-library/reference/chsize.md)[CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述）。  
  
## 语法  
  
```  
errno_t _chsize_s(   
   int fd,  
   __int64 size   
);  
```  
  
#### 参数  
 `fd`  
 引用开启文件的描述符。  
  
 `size`  
 文件的新长度（以字节为单位）。  
  
## 返回值  
 如果更改成功，文件大小，`_chsize_s` 返回值 0。  非零返回值指示错误：返回值为 `EACCES` ，如果指定的文件锁定访问，`EBADF` ，如果指定的文件改为只读或说明符无效，`ENOSPC` ，如果设备没有留出空间。，或 `EINVAL` ，如果大小小于零。  `errno` 设置为相同的值。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_chsize_s` 函数扩展或截断文件与 `fd` 为 `size`的指定长度。  文件绑定中打开允许写入的模式。  null 字符 \(“\\ 0 "\) 追加，如果文件是扩展。  如果文件被截断，缩短从文件的结尾的所有数据。文件的原始长度的丢失。  
  
 `_chsize_s` 大于 4 GB 一个 64 位整数作为文件的大小，并可以处理大文件大小。  `_chsize` 仅限于 32 位文件大小。  
  
 此函数验证其参数。  如果 `fd` 不是一个有效的文件说明符或范围小于零，无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_chsize_s`|\<io.h\>|\<errno.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
  
-   [System::IO::Stream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.stream.setlength.aspx)  
  
-   [System::IO::FileStream::SetLength](https://msdn.microsoft.com/en-us/library/system.io.filestream.setlength.aspx)  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_chsize](../../c-runtime-library/reference/chsize.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)