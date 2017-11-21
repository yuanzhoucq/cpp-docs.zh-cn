---
title: "_getdcwd_dbg、_wgetdcwd_dbg | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getdcwd_dbg
- _wgetdcwd_dbg
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
apitype: DLLExport
f1_keywords:
- _getdcwd_dbg
- getdcwd_dbg
- _wgetdcwd_dbg
- wgetdcwd_dbg
dev_langs: C++
helpviewer_keywords:
- working directory
- _getdcwd_dbg function
- wgetdcwd_dbg function
- current working directory
- getdcwd_dbg function
- _wgetdcwd_dbg function
- directories [C++], current working
ms.assetid: 266bf6f0-0417-497f-963d-2e0f306d9385
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8afa6156185ac1d375834bdc22df35f2a94638fd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="getdcwddbg-wgetdcwddbg"></a>_getdcwd_dbg、_wgetdcwd_dbg
[_getdcwd、_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md) 函数的调试版本（仅在调试过程中可用）。  
  
## <a name="syntax"></a>语法  
  
```  
char *_getdcwd_dbg(  
   int drive,  
   char *buffer,  
   int maxlen,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
wchar_t *_wgetdcwd_dbg(  
   int drive,  
   wchar_t *buffer,  
   int maxlen,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>参数  
 `drive`  
 磁盘驱动器的名称。  
  
 `buffer`  
 路径的存储位置。  
  
 `maxlen`  
 路径的最大长度（以字符为单位）：`char` 的 `_getdcwd_dbg` 和 `wchar_t` 的 `_wgetdcwd_dbg`。  
  
 `blockType`  
 内存块的请求类型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 指向已请求分配操作的源文件名的指针或 `NULL`。  
  
 `linenumber`  
 请求分配操作所在的源文件中的行数或 `NULL`。  
  
## <a name="return-value"></a>返回值  
 返回指向 `buffer`的指针。 `NULL` 返回值指示错误，并将 `errno` 设置为 `ENOMEM`，指示内存不足，无法分配 `maxlen` 个字节（当将 `NULL` 参数给定为 `buffer`时），或设置为 `ERANGE`，指示该路径长于 `maxlen` 个字符。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `_getdcwd_dbg` 和 `_wgetdcwd_dbg` 函数与 `_getdcwd` 和 `_wgetdcwd` 完全相同，只是当定义 `_DEBUG` 时，如果将 `malloc` 作为 `_malloc_dbg` 参数进行传递，则这些函数将使用 `NULL` 的调试版本和 `buffer` 来分配内存。 有关详细信息，请参阅 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 在大多数情况下，无需显式调用这些函数。 可以改为定义 `_CRTDBG_MAP_ALLOC` 标志。 定义 `_CRTDBG_MAP_ALLOC` 后，对 `_getdcwd` 和 `_wgetdcwd` 的调用将分别重新映射到 `_getdcwd_dbg` 和 `_wgetdcwd_dbg`，同时会将 `blockType` 设置为 `_NORMAL_BLOCK`。 因此，无需显式调用这些函数，除非你希望将堆块标记为 `_CLIENT_BLOCK`。 有关详细信息，请参阅[调试堆的块类型](/visualstudio/debugger/crt-debug-heap-details)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tgetdcwd_dbg`|`_getdcwd_dbg`|`_getdcwd_dbg`|`_wgetdcwd_dbg`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_getdcwd_dbg`|\<crtdbg.h>|  
|`_wgetdcwd_dbg`|\<crtdbg.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>另请参阅  
 [_getdcwd、_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)   
 [目录控制](../../c-runtime-library/directory-control.md)   
 [堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)