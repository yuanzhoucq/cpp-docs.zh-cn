---
title: "_unlock_file | Microsoft Docs"
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
  - "_unlock_file"
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
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_unlock_file"
  - "unlock_file"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_unlock_file 函数"
  - "文件 [C++], 取消锁定"
  - "unlock_file 函数"
  - "取消锁定文件"
ms.assetid: cf380a51-6d3a-4f38-bd64-2d4fb57b4369
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _unlock_file
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取消锁定文件，并允许其他进程访问文件。  
  
## 语法  
  
```  
void _unlock_file(  
   FILE* file  
);  
```  
  
#### 参数  
 `file`  
 文件处理程序。  
  
## 备注  
 `_unlock_file` 函数解锁通过`file` 指定的文件。  取消锁定文件，并允许其他进程访问文件。  此函数，除非 `_lock_file` 之前调用了 `file` 指针，而应调用。  对没有锁定的文件 `_unlock_file` 可能会导致死锁。  有关示例，请参见[\_lock\_file](../../c-runtime-library/reference/lock-file.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_unlock_file`|\<stdio.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 [System::IO::FileStream::Lock](https://msdn.microsoft.com/en-us/library/system.io.filestream.lock.aspx)  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_lock\_file](../../c-runtime-library/reference/lock-file.md)