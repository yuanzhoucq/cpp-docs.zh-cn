---
title: "_umask_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _umask_s
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
f1_keywords:
- unmask_s
- _umask_s
dev_langs: C++
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 71279b111e50c40bb974d9a5da68b575aecc1ebc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="umasks"></a>_umask_s
设置默认的文件权限掩码。 这是 [_umask](../../c-runtime-library/reference/umask.md) 版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增强功能。  
  
## <a name="syntax"></a>语法  
  
```  
errno_t _umask_s(  
   int mode,  
   int * pOldMode  
);  
```  
  
#### <a name="parameters"></a>参数  
 [in] `mode`  
 默认权限设置。  
  
 [out] `oldMode`  
 权限设置的上一个值。  
  
## <a name="return-value"></a>返回值  
 如果 `Mode` 未指定有效的模式或 `pOldMode` 指针是 `NULL`，则返回错误代码。  
  
### <a name="error-conditions"></a>错误条件  
  
|`mode`|`pOldMode`|**返回值**|`oldMode` **的内容**|  
|------------|----------------|----------------------|--------------------------------|  
|任何|`NULL`|`EINVAL`|未修改|  
|无效模式|任何|`EINVAL`|未修改|  
  
 发生上述情况中的任何一个，都会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则 `_umask_s` 返回 `EINVAL`，并将 `errno` 设置为 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `_umask_s`函数将当前进程的文件权限掩码设置为所指定的模式`mode`。 文件权限掩码修改 `_creat`、`_open` 或 `_sopen` 创建的新文件的权限设置。 如果掩码中的一位是 1，则将文件的请求权限值中相应的一位设置为 0 (不允许)。 如果掩码中的一位是 0，则相应的一位保留不变。 直至首次关闭新文件时才会设置新文件的权限设置。  
  
 整数表达式 `pmode` 包含在 SYS\STAT.H 中定义的以下清单常量的其中一个或两个：  
  
 `_S_IWRITE`  
 允许写入。  
  
 `_S_IREAD`  
 允许读取。  
  
 `_S_IREAD | _S_IWRITE`  
 允许读取和写入。  
  
 当给定这两个常量时，将使用按位 OR 运算符 (`|`) 连接它们。 如果 `mode` 参数为 `_S_IREAD`，则不允许读取（此文件为只写）。 如果 `mode` 参数为 `_S_IWRITE`，则不允许写入（此文件为只读）。 例如，如果掩码中设置了写入位，则任何新文件都将为只读。 请注意在 MS-DOS 和 Windows 操作系统下，所有文件均可读；不可能提供只写权限。 因此，使用 `_umask_s` 设置读取位不影响文件的模式。  
  
 如果 `pmode` 不是清单常量之一的组合或包含备用常量集，则此函数将会忽略这些。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_umask_s`|\<io.h> 和 \<sys/stat.h> 和 \<sys/types.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
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
  
```Output  
Oldmask = 0x0000  
```  
  
## <a name="see-also"></a>请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [低级别 I/O](../../c-runtime-library/low-level-i-o.md)   
 [_chmod、_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_mkdir、_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_umask](../../c-runtime-library/reference/umask.md)