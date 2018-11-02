---
title: _tempnam_dbg、_wtempnam_dbg
ms.date: 11/04/2016
apiname:
- _wtempnam_dbg
- _tempnam_dbg
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
ms.openlocfilehash: 804c8ad1f17c6ee1df563cafc69ee7aef494d1cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50596451"
---
# <a name="tempnamdbg-wtempnamdbg"></a>_tempnam_dbg、_wtempnam_dbg

函数的版本[_tempnam、 _wtempnam、 tmpnam、 _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)使用的调试版本**malloc**， **_malloc_dbg**。

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

*dir*<br/>
文件名中使用的路径（如果不存在 TMP 环境变量或 TMP 不是有效的目录）。

*prefix*<br/>
将前悬移到返回的名称的字符串 **_tempnam**。

*blockType*<br/>
内存块的请求类型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
指向已请求分配操作的源文件名或**NULL**。

*linenumber*<br/>
请求分配操作所在的源文件中的行数或**NULL**。

## <a name="return-value"></a>返回值

每个函数返回一个指向生成的名称或**NULL**故障时。 如果在 TMP 环境变量并在指定了无效的目录名称，则可能发生故障*dir*参数。

> [!NOTE]
> **免费**(或**free_dbg**) 确实需要通过分配的指针调用 **_tempnam_dbg**并 **_wtempnam_dbg**。

## <a name="remarks"></a>备注

**_Tempnam_dbg**并 **_wtempnam_dbg**函数是相同 **_tempnam**并 **_wtempnam**只不过，当 **_DEBUG**是定义，这些函数将使用的调试版本**malloc**并 **_malloc_dbg**来分配内存，如果**NULL**是作为第一个参数传递。 有关详细信息，请参阅 [_malloc_dbg](malloc-dbg.md)。

在大多数情况下，无需显式调用这些函数。 相反，可以定义标志 **_CRTDBG_MAP_ALLOC**。 当 **_CRTDBG_MAP_ALLOC**定义，则调用 **_tempnam**并 **_wtempnam**重新映射到 **_tempnam_dbg**和 **_wtempnam_dbg**，分别与*blockType*设置为 **_NORMAL_BLOCK**。 因此，不需要显式调用这些函数，除非你想要将标记作为堆块 **_CLIENT_BLOCK**。 有关详细信息，请参阅[调试堆的块类型](/visualstudio/debugger/crt-debug-heap-details)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttempnam_dbg**|**_tempnam_dbg**|**_tempnam_dbg**|**_wtempnam_dbg**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_tempnam_dbg**， **_wtempnam_dbg**|\<crtdbg.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[堆分配函数的调试版本](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)<br/>
