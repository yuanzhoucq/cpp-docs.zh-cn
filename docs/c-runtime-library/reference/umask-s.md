---
title: "_umask_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_umask_s"
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
  - "unmask_s"
  - "_umask_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_umask_s 函数"
  - "文件权限 [C++]"
  - "文件 [C++], 权限设置"
  - "蒙板"
  - "蒙板, 文件权限设置"
  - "umask_s 函数"
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _umask_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

设置默认的文件权限掩码。  正如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，安全性增强 [\_umask](../../c-runtime-library/reference/umask.md) 版本。  
  
## 语法  
  
```  
errno_t _umask_s(  
   int mode,  
   int * pOldMode  
);  
```  
  
#### 参数  
 \[in\] `mode`  
 默认权限设置。  
  
 \[out\] `oldMode`  
 权限设置的前值。  
  
## 返回值  
 如果 `Mode` 未指定有效的模式或 `pOldMode` 的指针为 `NULL`，则返回一个错误代码。  
  
### 错误情况  
  
|`mode`|`pOldMode`|**返回值**|**Contents of**  `oldMode`|  
|------------|----------------|-------------|--------------------------------|  
|any|`NULL`|`EINVAL`|未修改|  
|无效模式|any|`EINVAL`|未修改|  
  
 如果以上状态之一发生，调用无效参数处理程序，正如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许继续执行， `_umask_s` 返回 `EINVAL`并设置`errno` 为 `EINVAL`。  
  
## 备注  
 `_umask_s` 函数通过`mode`*.*用于设置当前进程的文件权限屏蔽掩码文件权限掩码通过 `_creat`、`_open`或 `_sopen`创建的新文件修改权限设置。  如果在掩码中一个位是 1，文件的请求的权限值对应的位设置为 0 \(禁止\)。  如果在掩码中一个位是 0，则对应的位保持不变。  直到文件第一次关闭，才会设置新的文件权限。  
  
 整数表达式 `pmode` 包含以下 SYS \\STAT.H定义中的一个或全部清单常数：  
  
 `_S_IWRITE`  
 允许写。  
  
 `_S_IREAD`  
 允许读取。  
  
 `_S_IREAD | _S_IWRITE`  
 允许读取和写入。  
  
 当给定两个常数，则用按位或运算符联接 \(         `|`  \).  如果 `mode` 参数为 `_S_IREAD`，将不允许读 \(文件为只写\)。  如果 `mode` 参数为 `_S_IWRITE`，将不允许写 \(文件为只读\)。  例如，如果掩码中设置写位，所有新建的文件将是只读的。  请注意使用 MS\-DOS 和 Windows 操作系统上，所有文件是可读性的；生成只写权限是不可能的。  因此，使用 `_umask_s` 设置读取位对文件模式没有影响。  
  
 如果 `pmode` 不是组合的清单常数也没有并入重写项组常量，函数将会忽略这些。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_umask_s`|\<io.h\> and \<sys\/stat.h\> and \<sys\/types.h\>|  
  
 有关其他兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_umask_s.c  
/* This program uses _umask_s to set  
 * the file-permission mask so that all future  
 * files will be created as read-only files.  
 * It also displays the old mask.  
 */  
  
#include <sys/stat.h>  
#include <sys/types.h>  
#include <io.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int oldmask, err;  
  
   /* Create read-only files: */  
   err = _umask_s( _S_IWRITE, &oldmask );  
   if (err)  
   {  
      printf("Error setting the umask.\n");  
      exit(1);  
   }  
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
 [\_umask](../../c-runtime-library/reference/umask.md)