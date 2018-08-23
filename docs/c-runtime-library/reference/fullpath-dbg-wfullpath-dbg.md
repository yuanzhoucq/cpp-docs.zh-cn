---
title: _fullpath_dbg、_wfullpath_dbg | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d04f3d7b53eca27d38a38b0bce284c17b15cae02
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2018
ms.locfileid: "34450890"
---
# <a name="fullpathdbg-wfullpathdbg"></a>_fullpath_dbg、_wfullpath_dbg

版本的[_fullpath、 _wfullpath](fullpath-wfullpath.md)使用的调试版本**malloc**分配内存。

## <a name="syntax"></a>语法

```C
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

### <a name="parameters"></a>参数

*absPath*<br/>
指向包含绝对路径或完整路径名称缓冲区的指针或**NULL**。

*relPath*<br/>
相对路径名称。

*maxLength*<br/>
最大长度为绝对路径名称缓冲区 (*absPath*)。 此长度以字节为单位的是 **_fullpath**但以宽字符为单位 (**wchar_t**) 为 **_wfullpath**。

*blockType*<br/>
内存块的请求类型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
指向已请求分配操作的源文件名或**NULL**。

*linenumber*<br/>
请求分配操作所在的源文件中的行数或**NULL**。

## <a name="return-value"></a>返回值

每个函数返回指向包含绝对路径名称的缓冲区的指针 (*absPath*)。 如果没有错误 (例如，如果中传递的值*relPath*包含一个无法找到或不是有效的驱动器号或者，如果创建的绝对路径名称的长度 (*absPath*) 大于*maxLength*) 该函数将返回**NULL**。

## <a name="remarks"></a>备注

**_Fullpath_dbg**和 **_wfullpath_dbg**函数相等 **_fullpath**和 **_wfullpath**只不过，当 **_DEBUG**是定义，这些函数将使用的调试版本**malloc**， **_malloc_dbg**来分配内存，如果**NULL**传递作为第一个参数。 有关信息的调试功能的 **_malloc_dbg**，请参阅[_malloc_dbg](malloc-dbg.md)。

在大多数情况下，无需显式调用这些函数。 相反，你可以定义 **_CRTDBG_MAP_ALLOC**标志。 当 **_CRTDBG_MAP_ALLOC**定义，则调用 **_fullpath**和 **_wfullpath**重新映射到 **_fullpath_dbg**和 **_wfullpath_dbg**分别与*blockType*设置为 **_NORMAL_BLOCK**。 因此，不需要显式调用这些函数，除非你希望将堆块作为标记 **_CLIENT_BLOCK**。 有关详细信息，请参阅[调试堆的块类型](/visualstudio/debugger/crt-debug-heap-details)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfullpath_dbg**|**_fullpath_dbg**|**_fullpath_dbg**|**_wfullpath_dbg**|

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fullpath_dbg**|\<crtdbg.h>|
|**_wfullpath_dbg**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
