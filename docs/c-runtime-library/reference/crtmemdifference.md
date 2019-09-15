---
title: _CrtMemDifference
ms.date: 11/04/2016
api_name:
- _CrtMemDifference
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
- _CrtMemDifference
- CrtMemDifference
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
ms.openlocfilehash: 51bfa014d54f55843fcb112f318f143774abf8f3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938714"
---
# <a name="_crtmemdifference"></a>_CrtMemDifference

比较两个内存状态，并返回它们的差异（仅限调试版本）。

## <a name="syntax"></a>语法

```C
int _CrtMemDifference(
   _CrtMemState *stateDiff,
   const _CrtMemState *oldState,
   const _CrtMemState *newState
);
```

### <a name="parameters"></a>参数

*stateDiff*<br/>
指向 **_CrtMemState**结构的指针，该结构用于存储两个内存状态（已返回）之间的差异。

*oldState*<br/>
指向较早内存状态（ **_CrtMemState**结构）的指针。

*newState*<br/>
指向更高内存状态（ **_CrtMemState**结构）的指针。

## <a name="return-value"></a>返回值

如果内存状态明显不同，则 **_CrtMemDifference**将返回 TRUE。 否则，此函数返回 FALSE。

## <a name="remarks"></a>备注

**_CrtMemDifference**函数对*oldState*和*newState*进行了比较，并在*stateDiff*中存储它们之间的差异，应用程序随后可以使用这些函数来检测内存泄漏和其他内存问题。 未定义[_debug](../../c-runtime-library/debug.md)时，将在预处理过程中删除对 **_CrtMemDifference**的调用。

*newState*和*oldState*必须是指向 **_CrtMemState**结构的有效指针，该结构在 Crtdbg.h 中定义，在调用 **_CrtMemCheckpoint**之前已由[_CrtMemDifference](crtmemcheckpoint.md)填充。 *stateDiff*必须是指向以前分配的 **_CrtMemState**结构实例的指针。 如果*stateDiff*、 *newState*或*oldState*为**NULL**，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)设置为**EINVAL** ，并且该函数将返回 FALSE。

**_CrtMemDifference**将*oldState*中块的 **_CrtMemState**字段值与*newState*中的块字段值进行比较，并将结果存储在*stateDiff*中。 当这两个内存状态的已分配块类型数目或各类型的已分配块数不同时，将这两个状态称为大不相同。 同时为两个状态分配的最大数量与这两个状态的总分配数之间的差异也存储在*stateDiff*中。

默认情况下，内存状态操作中不包含内部 C 运行时块（ **_CRT_BLOCK**）。 [_CrtSetDbgFlag](crtsetdbgflag.md)函数可用于启用 **_crtDbgFlag**的 **_CRTDBG_CHECK_CRT_DF**位，以将这些块包含在泄漏检测和其他内存状态操作中。 已释放的内存块（ **_FREE_BLOCK**）不会导致 **_CrtMemDifference**返回 TRUE。

有关堆状态函数和 **_CrtMemState**结构的详细信息，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

**库**仅限[CRT 库功能](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_CRTDBG_CHECK_CRT_DF](../../c-runtime-library/crtdbgflag.md)<br/>
