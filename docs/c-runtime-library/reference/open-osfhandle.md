---
title: "_open_osfhandle | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_open_osfhandle"
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
  - "_open_osfhandle"
  - "open_osfhandle"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "open_osfhandle 函数"
  - "文件处理 [C++]，正在关联"
  - "_open_osfhandle 函数"
ms.assetid: 30d94df4-7868-4667-a401-9eb67ecb7855
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# _open_osfhandle
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用现有的操作系统文件图柄关联 C 运行时文件说明符。  
  
## 语法  
  
```  
  
      int _open_osfhandle (  
   intptr_t osfhandle,  
   int flags   
);  
```  
  
#### 参数  
 `osfhandle`  
 操作系统文件句柄。  
  
 `flags`  
 允许操作的类型。  
  
## 返回值  
 如果成功，则 `_open_osfhandle`返回运行时文件说明符。  否则，返回 \-1。  
  
## 备注  
 `_open_osfhandle` 函数分配C 运行时文件 描述符,并将它关联到`osfhandle`指定的操作系统的文件句柄 。  `flags` 参数是整数表达式，由Fcntl.h中定义的一个或多个清单常数组成。  如果两个或多个清单常数可用于构成 `flags` 参数时，常量用按位或运算符合并  **&#124;** \).  
  
 Fcntl.h 定义下列清单常数。  
  
 **\_O\_APPEND**  
 在每次写入操作之前,定位文件指针到文件尾。  
  
 **\_O\_RDONLY**  
 以只读方式打开文件。  
  
 **\_O\_TEXT**  
 在文本（转换）模式下打开文件。  
  
 **\_O\_WTEXT**  
 在Unicode（转换UTF\-16）模式下打开文件。  
  
 关闭`_open_osfhandle`打开的文件，调用 `_close`。  调用`_close`也关闭基础句柄，因此，调用原始句柄的 Win32 函数 `CloseHandle` 是不必要的。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_open_osfhandle`|\<io.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 [System::IO::FileStream::Handle](https://msdn.microsoft.com/en-us/library/system.io.filestream.handle.aspx)  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)