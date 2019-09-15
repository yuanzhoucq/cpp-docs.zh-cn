---
title: _CrtMemCheckpoint
ms.date: 11/04/2016
api_name:
- _CrtMemCheckpoint
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
- CrtMemCheckpoint
- _CrtMemCheckpoint
- crtdbg/_CrtMemCheckpoint
helpviewer_keywords:
- CrtMemCheckpoint function
- _CrtMemCheckpoint function
ms.assetid: f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc
ms.openlocfilehash: edf91cd8c76fd080326e2e5eeac98f7f81ab90cf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942369"
---
# <a name="_crtmemcheckpoint"></a>_CrtMemCheckpoint

获取调试堆的当前状态并将其存储在应用程序提供的 **_CrtMemState**结构中（仅限调试版本）。

## <a name="syntax"></a>语法

```C
void _CrtMemCheckpoint(
   _CrtMemState *state
);
```

### <a name="parameters"></a>参数

State<br/>
指向 **_CrtMemState**结构的指针，该结构用内存检查点进行填充。

## <a name="remarks"></a>备注

**_CrtMemCheckpoint**函数在任意给定时刻创建调试堆的当前状态的快照。 此快照可由其他堆状态函数（如 [_CrtMemDifference](crtmemdifference.md) ）用来帮助检测内存泄漏和其他问题。 未定义[_debug](../../c-runtime-library/debug.md)时，将在预处理过程中删除对 **_CrtMemState**的调用。

应用程序必须将指针传递到 **_CrtMemState**结构（在 crtdbg.h 中定义）在*state*参数中定义的以前分配的实例。 如果 **_CrtMemCheckpoint**在检查点创建期间遇到错误，该函数将生成一个描述该问题的 **_CRT_WARN**调试报告。

有关堆状态函数和 **_CrtMemState**结构的详细信息，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的详细信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

如果*state*为**NULL**，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)设置为**EINVAL** ，并且该函数将返回。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_CrtMemCheckpoint**|\<crtdbg.h>、\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

**库**仅限 UCRT 的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_CrtMemDifference](crtmemdifference.md)<br/>
