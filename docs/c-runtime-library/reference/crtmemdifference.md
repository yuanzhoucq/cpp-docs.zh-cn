---
title: _CrtMemDifference | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _CrtMemDifference
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
- _CrtMemDifference
- CrtMemDifference
dev_langs:
- C++
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27fb436c438daac7415ba3c0e7581611414c9c4a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="crtmemdifference"></a>_CrtMemDifference

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
指向 **_CrtMemState**结构，它用于存储这两个内存状态 （返回） 之间的差异。

*oldState*<br/>
指向较早内存状态 (**_CrtMemState**结构)。

*newState*<br/>
指向更高版本的内存状态 (**_CrtMemState**结构)。

## <a name="return-value"></a>返回值

如果内存状态大不相同， **_CrtMemDifference** ，则返回 TRUE。 否则，此函数返回 FALSE。

## <a name="remarks"></a>备注

**_CrtMemDifference**函数对比*oldState*和*newState* ，并将存储在它们之间的差异*stateDiff*，后者可以然后用于应用程序检测内存泄漏和其他内存问题。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtMemDifference**在预处理过程中删除。

*newState*和*oldState*都必须指向有效指针 **_CrtMemState**中由填写在 crtdbg.h 所定义的结构[_CrtMemCheckpoint](crtmemcheckpoint.md)之前调用 **_CrtMemDifference**。 *stateDiff*必须是指向以前分配的实例 **_CrtMemState**结构。 如果*stateDiff*， *newState*，或*oldState*是**NULL**，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)设置为**EINVAL**和此函数返回 FALSE。

**_CrtMemDifference**比较 **_CrtMemState**字段值中的块*oldState*中*newState*并存储在结果*stateDiff*。 当这两个内存状态的已分配块类型数目或各类型的已分配块数不同时，将这两个状态称为大不相同。 分配一次两个状态以及总分配之间的差异的两个状态也存储在的最大数之间的差异*stateDiff*。

默认情况下，内部 C 运行时块 (**_CRT_BLOCK**) 不包括在内存状态操作。 [_CrtSetDbgFlag](crtsetdbgflag.md)函数可用来打开 **_CRTDBG_CHECK_CRT_DF**位的 **_crtDbgFlag**以将这些块包含在泄漏检测和其他内存状态操作。 已释放的内存块 (**_FREE_BLOCK**) 不会导致 **_CrtMemDifference**返回 TRUE。

有关堆状态函数和 **_CrtMemState**结构，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

**库：**仅限 [CRT 库功能](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
