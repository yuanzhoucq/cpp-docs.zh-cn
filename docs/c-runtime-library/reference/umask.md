---
title: "_umask | Microsoft Docs"
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
  - "_umask"
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
  - "_umask"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_umask 函数"
  - "文件权限 [C++]"
  - "文件 [C++], 权限设置"
  - "蒙板"
  - "蒙板, 文件权限设置"
  - "umask 函数"
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
caps.latest.revision: 21
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _umask
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置默认的文件权限掩码。  提供该函数的一个更安全版本；请参阅 [\_umask\_s](../../c-runtime-library/reference/umask-s.md)。  
  
## 语法  
  
```  
int _umask(  
   int pmode   
);  
```  
  
#### 参数  
 `pmode`  
 默认权限设置。  
  
## 返回值  
 `_umask` 返回 `pmode` 的先前值。  无错误返回。  
  
## 备注  
 `_umask` 函数通过`pmode`*.*用于设置当前进程的文件权限屏蔽掩码文件权限掩码通过 `_creat`、`_open`或 `_sopen`创建的新文件修改权限设置。  如果在掩码中一个位是 1，文件的请求的权限值对应的位设置为 0 \(禁止\)。  如果在掩码中一个位是 0，则对应的位保持不变。  直到文件第一次关闭，才会设置新的文件权限。  
  
 整数表达式 `pmode` 包含以下 SYS \\STAT.H定义中的一个或全部清单常数：  
  
 `_S_IWRITE`  
 允许写。  
  
 `_S_IREAD`  
 允许读取。  
  
 `_S_IREAD | _S_IWRITE`  
 允许读取和写入。  
  
 当给定两个常数，则用按位或运算符联接 \(          `|`  \).  如果 `pmode` 参数为 `_S_IREAD`，将不允许读 \(文件为只写\)。  如果 `pmode` 参数为 `_S_IWRITE`，将不允许写 \(文件为只读\)。  例如，如果掩码中设置写位，所有新建的文件将是只读的。  请注意使用 MS\-DOS 和 Windows 操作系统上，所有文件是可读性的；生成只写权限是不可能的。  因此，使用 `_umask` 设置读取位对文件模式没有影响。  
  
 如果 `pmode` 不是组合的清单常数也没有并入重写项组常量，函数将会忽略这些。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_umask`|\<io.h\>, \<sys\/stat.h\>, \<sys\/types.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_umask.c  
// compile with: /W3  
// This program uses _umask to set  
// the file-permission mask so that all future  
// files will be created as read-only files.  
// It also displays the old mask.  
#include <sys/stat.h>  
#include <sys/types.h>  
#include <io.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int oldmask;  
  
   /* Create read-only files: */  
   oldmask = _umask( _S_IWRITE ); // C4996  
   // Note: _umask is deprecated; consider using _umask_s instead  
   printf( "Oldmask = 0x%.4x\n", oldmask );  
}  
```  
  
  **Oldmask \= 0x0000**   
## .NET Framework 等效项  
 [System.IO.File::GetAttributes](https://msdn.microsoft.com/en-us/library/system.io.file.setattributes.aspx)  
  
## 请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [低级别 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_chmod、\_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_mkdir、\_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)