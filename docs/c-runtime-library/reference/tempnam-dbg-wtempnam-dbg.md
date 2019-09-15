---
title: _tempnam_dbg、_wtempnam_dbg
ms.date: 11/04/2016
api_name:
- _wtempnam_dbg
- _tempnam_dbg
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wtempnam_dbg
- tempnam_dbg
- _tempnam_dbg
- _wtempnam_dbg
helpviewer_keywords:
- file names [C++], creating temporary
- tempnam_dbg function
- temporary files, creating
- file names [C++], temporary
- wtempnam_dbg function
- _tempnam_dbg function
- _wtempnam_dbg function
ms.assetid: e3760bb4-bb01-4808-b689-2c45af56a170
ms.openlocfilehash: 73642730995ac5c0b47519fac64b30400d47767c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946252"
---
# <a name="_tempnam_dbg-_wtempnam_dbg"></a>_tempnam_dbg、_wtempnam_dbg

使用 _tempnam、 [_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)的函数版本，该版本使用**malloc**， **_malloc_dbg**的调试版本。

## <a name="syntax"></a>语法

```C
char *_tempnam_dbg(
   const char *dir,
   const char *prefix,
   int blockType,
   const char *filename,
   int linenumber
);
wchar_t *_wtempnam_dbg(
   const wchar_t *dir,
   const wchar_t *prefix,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>参数

*目录*<br/>
文件名中使用的路径（如果不存在 TMP 环境变量或 TMP 不是有效的目录）。

*prefix*<br/>
将预先挂起到 **_tempnam**返回的名称的字符串。

*blockType*<br/>
内存块的请求类型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
指向已请求分配操作的源文件名的指针或**NULL**。

*linenumber*<br/>
请求分配操作所在的源文件中的行号或**NULL**。

## <a name="return-value"></a>返回值

每个函数均返回一个指向生成的名称的指针; 如果发生失败，则返回**NULL** 。 如果在 TMP 环境变量和*dir*参数中指定的目录名称无效，则可能发生失败。

> [!NOTE]
> **免费**对于由 **_tempnam_dbg**和 **_wtempnam_dbg**分配的指针，需要调用（或**free_dbg**）。

## <a name="remarks"></a>备注

**_Tempnam_dbg**和 **_wtempnam_dbg**函数与 **_tempnam**和 **_wtempnam**相同，不同之处在于，定义 **_debug**后，这些函数将使用**malloc**和 **_malloc_dbg**的调试版本来如果将**NULL**作为第一个参数传递，则分配内存。 有关详细信息，请参阅 [_malloc_dbg](malloc-dbg.md)。

在大多数情况下，无需显式调用这些函数。 您可以改为定义标志 **_CRTDBG_MAP_ALLOC**。 定义 **_CRTDBG_MAP_ALLOC**时，对 **_tempnam**和 **_wtempnam**的调用将分别重新映射到 **_tempnam_dbg**和 **_wtempnam_dbg**，并将*blockType*设置为 **_NORMAL_BLOCK**。 因此，无需显式调用这些函数，除非你希望将堆块标记为 **_CLIENT_BLOCK**。 有关详细信息，请参阅[调试堆的块类型](/visualstudio/debugger/crt-debug-heap-details)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttempnam_dbg**|**_tempnam_dbg**|**_tempnam_dbg**|**_wtempnam_dbg**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_tempnam_dbg**、 **_wtempnam_dbg**|\<crtdbg.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
