---
title: "_umask | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _umask
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords: _umask
dev_langs: C++
helpviewer_keywords:
- masks, file-permission-setting
- _umask function
- masks
- umask function
- file permissions [C++]
- files [C++], permission settings for
ms.assetid: 5e9a13ba-5321-4536-8721-6afb6f4c8483
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d8651fd1aa1400b366c6db369eff7bfde8751507
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="umask"></a>_umask
设置默认的文件权限掩码。 此函数有一个更安全的版本；请参阅 [_umask_s](../../c-runtime-library/reference/umask-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
int _umask(  
   int pmode   
);  
```  
  
#### <a name="parameters"></a>参数  
 `pmode`  
 默认权限设置。  
  
## <a name="return-value"></a>返回值  
 `_umask` 返回 `pmode` 的前一个值。 无错误返回。  
  
## <a name="remarks"></a>备注  
 `_umask`函数将当前进程的文件权限掩码设置为所指定的模式`pmode`。 文件权限掩码修改 `_creat`、`_open` 或 `_sopen` 创建的新文件的权限设置。 如果掩码中的一位是 1，则将文件的请求权限值中相应的一位设置为 0 (不允许)。 如果掩码中的一位是 0，则相应的一位保留不变。 直至首次关闭新文件时才会设置新文件的权限设置。  
  
 整数表达式 `pmode` 包含在 SYS\STAT.H 中定义的以下清单常量的其中一个或两个：  
  
 `_S_IWRITE`  
 允许写入。  
  
 `_S_IREAD`  
 允许读取。  
  
 `_S_IREAD | _S_IWRITE`  
 允许读取和写入。  
  
 当给定这两个常量时，将使用按位 OR 运算符 (`|`) 连接它们。 如果 `pmode` 参数为 `_S_IREAD`，则不允许读取（此文件为只写）。 如果 `pmode` 参数为 `_S_IWRITE`，则不允许写入（此文件为只读）。 例如，如果掩码中设置了写入位，则任何新文件都将为只读。 请注意在 MS-DOS 和 Windows 操作系统下，所有文件均可读；不可能提供只写权限。 因此，使用 `_umask` 设置读取位不影响文件的模式。  
  
 如果 `pmode` 不是清单常量之一的组合或包含备用常量集，则此函数将会忽略这些。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_umask`|\<io.h>、\<sys/stat.h>、\<sys/types.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
Oldmask = 0x0000  
```  
  
## <a name="see-also"></a>另请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [低级别 I/O](../../c-runtime-library/low-level-i-o.md)   
 [_chmod、_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_mkdir、_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)