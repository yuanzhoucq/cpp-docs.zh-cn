---
title: _CrtIsMemoryBlock
ms.date: 11/04/2016
api_name:
- _CrtIsMemoryBlock
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
- CrtlsMemoryBlock
- _CrtIsMemoryBlock
helpviewer_keywords:
- _CrtIsMemoryBlock function
- CrtIsMemoryBlock function
ms.assetid: f7cbbc60-3690-4da0-a07b-68fd7f250273
ms.openlocfilehash: f29745acd06f6f5b3fa96367444e800bdc3e8e3a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938739"
---
# <a name="_crtismemoryblock"></a>_CrtIsMemoryBlock

确认指定的内存块位于本地堆，并且具有有效的调试堆块类型标识符（仅限调试版本）。

## <a name="syntax"></a>语法

```C
int _CrtIsMemoryBlock(
   const void *userData,
   unsigned int size,
   long *requestNumber,
   char **filename,
   int *linenumber
);
```

### <a name="parameters"></a>参数

*userData*<br/>
指向要验证的内存块开头的指针。

*size*<br/>
指定块的大小（以字节为单位）。

*requestNumber*<br/>
指向块分配编号的指针或**NULL**。

*filename*<br/>
指向请求该块的源文件名的指针或**NULL**。

*linenumber*<br/>
指向源文件中行号的指针或**NULL**。

## <a name="return-value"></a>返回值

如果指定的内存块位于本地堆中并且具有有效的调试堆块类型标识符，则 **_CrtIsMemoryBlock**返回**TRUE** ;否则，该函数返回**FALSE**。

## <a name="remarks"></a>备注

**_CrtIsMemoryBlock**函数验证指定的内存块是否位于应用程序的本地堆中，以及它是否具有有效的块类型标识符。 此函数还可用于获取最初请求内存块分配的对象分配序号和源文件名/行号。 如果为*requestNumber*、 *filename*或*linenumber*参数传递非**NULL**值，则会导致 **_CrtIsMemoryBlock**将这些参数设置为内存块调试标头中的值（如果它在本地堆。 未定义[_debug](../../c-runtime-library/debug.md)时，将在预处理过程中删除对 **_CrtIsMemoryBlock**的调用。

如果 **_CrtIsMemoryBlock**失败，则返回**FALSE** ，并将输出参数初始化为默认值： *requestNumber* ， **lineNumber**设置为0， *filename*设置为**NULL**。

因为此函数返回 **TRUE** 或 **FALSE**，因此可将它传递到其中一个 [_ASSERT](assert-asserte-assert-expr-macros.md) 宏，以创建一种简单的调试错误处理机制。 如果本地堆中没有指定的地址，则以下示例将导致断言失败：

```C
_ASSERTE( _CrtIsMemoryBlock( userData, size, &requestNumber,
          &filename, &linenumber ) );
```

有关 **_CrtIsMemoryBlock**如何与其他调试函数和宏一起使用的详细信息，请参阅用于[报告的宏](/visualstudio/debugger/macros-for-reporting)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_CrtIsMemoryBlock**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

请参阅 [_CrtIsValidHeapPointer](crtisvalidheappointer.md) 主题的示例。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
