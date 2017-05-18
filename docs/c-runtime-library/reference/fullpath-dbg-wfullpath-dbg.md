---
title: "_fullpath_dbg、_wfullpath_dbg | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wfullpath_dbg
- _fullpath_dbg
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
- wfullpath_dbg
- _wfullpath_dbg
- _fullpath_dbg
- fullpath_dbg
dev_langs:
- C++
helpviewer_keywords:
- _fullpath_dbg function
- relative file paths
- absolute paths
- fullpath_dbg function
- _wfullpath_dbg function
- wfullpath_dbg function
ms.assetid: 81f72f85-07da-4f5c-866a-598e0fb03f6b
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 6af4d6ba5df2305b5181e47cf0a0557650aa0406
ms.contentlocale: zh-cn
ms.lasthandoff: 04/04/2017

---
# <a name="fullpathdbg-wfullpathdbg"></a>_fullpath_dbg、_wfullpath_dbg
使用 `malloc` 调试版本分配内存的 [_fullpath、_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md) 版本。  
  
## <a name="syntax"></a>语法  
  
```  
char *_fullpath_dbg(   
   char *absPath,  
   const char *relPath,  
   size_t maxLength,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
wchar_t *_wfullpath_dbg(   
   wchar_t *absPath,  
   const wchar_t *relPath,  
   size_t maxLength,  
   int blockType,  
   const char *filename,  
   int linenumber   
);  
```  
  
#### <a name="parameters"></a>参数  
 `absPath`  
 指向包含绝对路径名称或完整路径名称的缓冲区的指针或 `NULL`。  
  
 `relPath`  
 相对路径名称。  
  
 `maxLength`  
 绝对路径名称缓冲区 (`absPath`) 的最大长度。 对于 `_fullpath`，此长度以字节为单位，但是对于 `wchar_t`，此长度以宽字符 (`_wfullpath`) 为单位。  
  
 `blockType`  
 内存块的请求类型：`_CLIENT_BLOCK` 或 `_NORMAL_BLOCK`。  
  
 `filename`  
 指向已请求分配操作的源文件名的指针或 `NULL`。  
  
 `linenumber`  
 请求分配操作所在的源文件中的行数或 `NULL`。  
  
## <a name="return-value"></a>返回值  
 每个函数都会返回指向包含绝对路径名称 (`absPath`) 的缓冲区的指针。 如果存在错误（例如，如果在 `relPath` 中传递的值包含一个无效或无法找到的驱动器号，或者创建的绝对路径名称 (`absPath`) 的长度大于 `maxLength`），则该函数将返回 `NULL`。  
  
## <a name="remarks"></a>备注  
 `_fullpath_dbg`和`_wfullpath_dbg`函数相等`_fullpath`和`_wfullpath`只不过，当`_DEBUG`是定义，这些函数将使用的调试版本`malloc`，`_malloc_dbg`来分配内存，如果作为第一个参数传递 NULL。 有关 `_malloc_dbg` 调试功能的信息，请参阅 [_malloc_dbg](../../c-runtime-library/reference/malloc-dbg.md)。  
  
 在大多数情况下，无需显式调用这些函数。 可以改为定义 `_CRTDBG_MAP_ALLOC` 标志。 定义 `_CRTDBG_MAP_ALLOC` 后，对 `_fullpath` 和 `_wfullpath` 的调用将分别重新映射到 `_fullpath_dbg` 和 `_wfullpath_dbg`，同时会将 `blockType` 设置为 `_NORMAL_BLOCK`。 因此，无需显式调用这些函数，除非你希望将堆块标记为 `_CLIENT_BLOCK`。 有关详细信息，请参阅[调试堆的块类型](/visualstudio/debugger/crt-debug-heap-details)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tfullpath_dbg`|`_fullpath_dbg`|`_fullpath_dbg`|`_wfullpath_dbg`|  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_fullpath_dbg`|\<crtdbg.h>|  
|`_wfullpath_dbg`|\<crtdbg.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="see-also"></a>另请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [_fullpath、_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)
