---
title: _CrtIsValidPointer | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtIsValidPointer
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
- CrtlsValidPointer
- _CrtIsValidPointer
dev_langs:
- C++
helpviewer_keywords:
- CrtIsValidPointer function
- _CrtIsValidPointer function
ms.assetid: 91c35590-ea5e-450f-a15d-ad8d62ade1fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb78f8dee494fd213df6db16e2800cb9090bdf3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32397259"
---
# <a name="crtisvalidpointer"></a>_CrtIsValidPointer

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

**_CrtIsValidPointer**如果指定的指针不为 null，则返回 TRUE。 在 Visual Studio 2010 之前的 CRT 库版本中，如果内存范围对于指定的一个或多个操作有效，则将返回 TRUE。 否则，此函数返回 FALSE。

## <a name="remarks"></a>备注

从在 Visual Studio 2010 中，CRT 库开始*大小*和*访问*参数将被忽略，和 **_CrtIsValidPointer**仅验证指定的*地址*不为 null。 由于可轻松自行执行此测试，因此不建议使用此函数。 在 Visual Studio 2010 之前的版本中，该函数验证开始的内存范围*地址*并扩展了*大小*字节可用于指定可访问性操作或操作。 当*访问*是设置为 TRUE，内存范围进行验证，读取和写入。 当*访问*为 FALSE 时，内存范围仅对于读取有效。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtIsValidPointer**在预处理过程中删除。

因为此函数返回 TRUE 或 FALSE，因此可将它传递到其中一个 [_ASSERT](assert-asserte-assert-expr-macros.md) 宏，以创建一种简单的调试错误处理机制。 如果内存范围对于读取和写入操作都无效，则以下示例将导致断言失败：

```C
_ASSERTE( _CrtIsValidPointer( address, size, TRUE ) );
```

详细了解如何 **_CrtIsValidPointer**可与其他调试函数和宏，请参阅[用于报告的宏](/visualstudio/debugger/macros-for-reporting)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_CrtIsValidPointer**|\<crtdbg.h>|

**_CrtIsValidPointer**是 Microsoft 扩展。 有关兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

请参阅 [_CrtIsValidHeapPointer](crtisvalidheappointer.md) 主题的示例。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
