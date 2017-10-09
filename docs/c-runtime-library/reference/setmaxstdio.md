---
title: "_setmaxstdio | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _setmaxstdio
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- setmaxstdio
- _setmaxstdio
dev_langs:
- C++
helpviewer_keywords:
- maximum open files
- _setmaxstdio function
- setmaxstdio function
- open files, maximum
ms.assetid: 9e966875-9ff5-47c4-9b5f-e79e83b70249
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 3c18b478c83c57a8a3bfd8238b367dbe4846d025
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="setmaxstdio"></a>_setmaxstdio
设置在 `stdio` 级别同时打开的最大文件数。  
  
## <a name="syntax"></a>语法  
  
```  
int _setmaxstdio(  
   int newmax   
);  
```  
  
#### <a name="parameters"></a>参数  
 `newmax`  
 在 `stdio` 级别同时打开的新的最大文件数。  
  
## <a name="return-value"></a>返回值  
 返回`newmax`如果成功; 否则为-1。  
  
 如果 `newmax` 小于 `_IOB_ENTRIES` 或大于操作系统中可用的句柄的最大数量，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回 -1 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `_setmaxstdio` 函数将更改可能在 `stdio` 级别同时打开的最大文件数。  
  
 相比早期版本，现在 C 运行时 I/O 在 Win32 平台上支持更多的打开文件。 在 [lowio 级别](../../c-runtime-library/low-level-i-o.md)最多可同时打开 2,048 个文件（即，通过 `_open`、`_read`、`_write` 等 I/O 函数系列打开和访问）。 在 [stdio 级别](../../c-runtime-library/stream-i-o.md)最多可同时打开 512 个文件（即，通过 `fopen`、`fgetc`、`fputc` 等函数系列打开和访问）。 在 `stdio` 级别 512 个打开文件的限制可通过 `_setmaxstdio` 函数增加到最多 2,048 个。  
  
 因为诸如 `fopen` 的 `stdio` 级别的函数是基于 `lowio` 函数生成的，2,048 的最大值是通过 C 运行时库访问的同时打开文件数的硬上限。  
  
> [!NOTE]
>  此上限可能会超过特定 Win32 平台和配置所支持的文件数。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_setmaxstdio`|\<stdio.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [_getmaxstdio](../../c-runtime-library/reference/getmaxstdio.md) 了解使用 `_setmaxstdio` 的示例。  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)
