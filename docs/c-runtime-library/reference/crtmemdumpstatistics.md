---
title: _CrtMemDumpStatistics | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtMemDumpStatistics
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
- CrtMemDumpStatistics
- _CrtMemDumpStatistics
dev_langs:
- C++
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 688cef94721ac7ea3a36ccd375185b922b23a15f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395599"
---
# <a name="crtmemdumpstatistics"></a>_CrtMemDumpStatistics

以用户可读的形式转储指定堆状态的调试标头信息（仅限调试版本）。

## <a name="syntax"></a>语法

```C
void _CrtMemDumpStatistics(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>参数

*状态*指向堆状态进行转储。

## <a name="remarks"></a>备注

**_CrtMemDumpStatistics**函数转储指定堆状态的用户可读的窗体中的调试标头信息。 应用程序可以使用转储统计信息来跟踪分配并检测内存问题。 内存状态可以包含特定的堆状态或两个状态之间的差异。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtMemDumpStatistics**在预处理过程中删除。

*状态*参数必须是指向 **_CrtMemState**由填写中的结构[_CrtMemCheckpoint](crtmemcheckpoint.md)或返回[_CrtMemDifference](crtmemdifference.md)之前 **_CrtMemDumpStatistics**调用。 如果*状态*是**NULL**，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**和不执行任何操作。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

有关堆状态函数和 **_CrtMemState**结构，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。 有关如何在基堆的调试版本中分配、初始化和管理内存块的详细信息，请参阅 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|----------------------|
|**_CrtMemDumpStatistics**|\<crtdbg.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

**库：** 仅限 [CRT 库功能](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
