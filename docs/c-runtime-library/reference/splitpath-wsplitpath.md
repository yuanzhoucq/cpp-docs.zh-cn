---
title: "_splitpath、_wsplitpath | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wsplitpath
- _splitpath
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
- wsplitpath
- _splitpath
- splitpath
- _wsplitpath
- _tsplitpath
dev_langs: C++
helpviewer_keywords:
- _splitpath function
- pathnames
- wsplitpath function
- splitpath function
- _wsplitpath function
- tsplitpath function
- path names
- _tsplitpath function
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ad76dd59e0119e46030eb19223d678927b3fd077
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="splitpath-wsplitpath"></a>_splitpath、_wsplitpath
将路径名称分解成组件。 提供这些函数的更多安全版本；请参阅 [_splitpath_s、_wsplitpath_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
void _splitpath(  
   const char *path,  
   char *drive,  
   char *dir,  
   char *fname,  
   char *ext   
);  
void _wsplitpath(  
   const wchar_t *path,  
   wchar_t *drive,  
   wchar_t *dir,  
   wchar_t *fname,  
   wchar_t *ext   
);  
```  
  
#### <a name="parameters"></a>参数  
 `path`  
 完整路径。  
  
 `drive`  
 后跟一个冒号 (`:`) 的驱动器号。 如果不需要驱动器号，则可为此参数传递 `NULL`。  
  
 `dir`  
 目录路径，包括尾部反斜杠。 正斜杠 ( `/` )、反斜杠 ( `\` )，或两者均使用。 如果不需要目录路径，则可为此参数传递 `NULL`。  
  
 `fname`  
 基文件名（无扩展名）。 如果不需要文件名，则可为此参数传递 `NULL`。  
  
 `ext`  
 文件扩展名，包括前导句点 (`.`)。 如果不需要文件扩展名，则可为此参数传递 `NULL`。  
  
## <a name="remarks"></a>备注  
 `_splitpath` 函数将路径分解成其的四个组件。 `_splitpath` 将根据情况自动处理多字节字符串参数，根据当前正在使用的多字节代码页识别多字节字符序列。 `_wsplitpath` 是 `_splitpath` 的宽字符版本；`_wsplitpath` 的参数是宽字符串。 否则这些函数具有相同行为。  
  
 **安全说明**这些函数会引发由缓冲区溢出问题带来的潜在威胁。 缓冲区溢出问题是常见的系统攻击方法，使权限的提升不能确保。 有关详细信息，请参阅 [避免缓冲区溢出](http://msdn.microsoft.com/library/windows/desktop/ms717795)。 提供这些函数的更多安全版本；请参阅 [_splitpath_s、_wsplitpath_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tsplitpath`|`_splitpath`|`_splitpath`|`_wsplitpath`|  
  
 完整路径的每个组件均存储在单独的缓冲区中；清单常量 `_MAX_DRIVE`、`_MAX_DIR`、`_MAX_FNAME` 和 `_MAX_EXT`（在 STDLIB.H 中定义）指定每个文件组件的最大大小。 文件组件大于相应清单常量会导致堆损坏。  
  
 每个缓冲区必须与其相应的清单常量一样大，以避免潜在的缓冲区溢出。  
  
 下表列出了清单常量的值。  
  
|name|“值”|  
|----------|-----------|  
|_MAX_DRIVE|3|  
|_MAX_DIR|256|  
|_MAX_FNAME|256|  
|_MAX_EXT|256|  
  
 如果完整路径不包含组件（例如，文件名），则 `_splitpath` 会将空字符串分配给相应的缓冲区。  
  
 可以为除不需要的 `path` 以外的任何参数将 `NULL` 传递到 `_splitpath`。  
  
 如果 `path` 为 `NULL`，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 `EINVAL`。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_splitpath`|\<stdlib.h>|  
|`_wsplitpath`|\<stdlib.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
 请参阅 [_makepath](../../c-runtime-library/reference/makepath-wmakepath.md) 的示例。  
  
## <a name="see-also"></a>请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [_fullpath、_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_makepath、_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [_splitpath_s、_wsplitpath_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)