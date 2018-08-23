---
title: _CrtGetReportHook | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtGetReportHook
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
- CrtGetReportHook
- _CrtGetReportHook
dev_langs:
- C++
helpviewer_keywords:
- CrtGetReportHook function
- _CrtGetReportHook function
ms.assetid: 922758ed-7edd-4359-9c92-0535192dc11a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d78c176d5d4de54f4ae5eea84b0483b9e6bc3bec
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395005"
---
# <a name="crtgetreporthook"></a>_CrtGetReportHook

检索客户端定义的报告函数，以挂钩到 C 运行时调试报告进程（仅限调试版本）。

## <a name="syntax"></a>语法

```C
_CRT_REPORT_HOOK _CrtGetReportHook( void );
```

## <a name="return-value"></a>返回值

返回当前的客户端定义的报告函数。

## <a name="remarks"></a>备注

**_CrtGetReportHook**允许应用程序在检索报告过程的 C 运行时调试库的当前报告功能。

有关使用其他具有挂钩功能的运行时函数和编写你自己的客户端定义挂钩函数的详细信息，请参阅[编写调试挂钩函数](/visualstudio/debugger/debug-hook-function-writing)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_CrtGetReportHook**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

有关如何使用的示例 **_CrtSetReportHook**，请参阅[报表](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/report)。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportHook](crtsetreporthook.md)<br/>
