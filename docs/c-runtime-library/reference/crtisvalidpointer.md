---
title: _CrtIsValidPointer
ms.date: 11/04/2016
api_name:
- _CrtIsValidPointer
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
- CrtlsValidPointer
- _CrtIsValidPointer
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
ms.openlocfilehash: 490d2dea097935dee2cd2a003aa28e32f1ced69d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938773"
---
# <a name="_crtisvalidpointer"></a>_CrtIsValidPointer

验证指针是否不为 Null。 在 Visual Studio 2010 之前的 C 运行时库版本中，验证指定的内存范围对于读取和写入是否有效（仅限调试版本）。

## <a name="syntax"></a>语法

```C
int _CrtIsValidPointer(
   const void *address,
   unsigned int size,
   int access
);
```

### <a name="parameters"></a>参数

*address*<br/>
指向内存范围的开始位置以进行有效性测试。

*size*<br/>
指定的内存范围大小（以字节为单位）。

*access*<br/>
确定对内存范围的读/写访问能力。

## <a name="return-value"></a>返回值

如果指定的指针不为 null，则 **_CrtIsValidPointer**返回 TRUE。 在 Visual Studio 2010 之前的 CRT 库版本中，如果内存范围对于指定的一个或多个操作有效，则将返回 TRUE。 否则，此函数返回 FALSE。

## <a name="remarks"></a>备注

从 Visual Studio 2010 中的 CRT 库开始，*大小*和*访问*参数将被忽略， **_CrtIsValidPointer**仅验证指定的*地址*是否不为 null。 由于可轻松自行执行此测试，因此不建议使用此函数。 在 Visual Studio 2010 之前的版本中，该函数验证从*address*开始且为*大小*字节扩展的内存范围对于指定的可访问性操作或操作是否有效。 当*access*设置为 TRUE 时，将验证内存范围的读取和写入。 当*access*为 FALSE 时，仅验证内存范围的读取。 未定义[_debug](../../c-runtime-library/debug.md)时，将在预处理过程中删除对 **_CrtIsValidPointer**的调用。

因为此函数返回 TRUE 或 FALSE，因此可将它传递到其中一个 [_ASSERT](assert-asserte-assert-expr-macros.md) 宏，以创建一种简单的调试错误处理机制。 如果内存范围对于读取和写入操作都无效，则以下示例将导致断言失败：

```C
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );
```

有关 **_CrtIsValidPointer**如何与其他调试函数和宏一起使用的详细信息，请参阅用于[报告的宏](/visualstudio/debugger/macros-for-reporting)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_CrtIsValidPointer**|\<crtdbg.h>|

**_CrtIsValidPointer**是 Microsoft 扩展。 有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

请参阅 [_CrtIsValidHeapPointer](crtisvalidheappointer.md) 主题的示例。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
