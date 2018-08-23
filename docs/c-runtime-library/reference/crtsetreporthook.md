---
title: _CrtSetReportHook | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtSetReportHook
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
- _CrtSetReportHook
- CrtSetReportHook
dev_langs:
- C++
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ef76fe0b7befb99b5bf0e8bb69fa1a1229782de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398784"
---
# <a name="crtsetreporthook"></a>_CrtSetReportHook

通过以下方式安装客户端定义的报告函数：将该函数挂钩到 C 运行时调试报告进程（仅限调试版本）中。

## <a name="syntax"></a>语法

```C
_CRT_REPORT_HOOK _CrtSetReportHook(
   _CRT_REPORT_HOOK reportHook
);
```

### <a name="parameters"></a>参数

*reportHook*<br/>
将新的客户端定义的报告函数挂钩到 C 运行时调试报告进程。

## <a name="return-value"></a>返回值

返回之前的客户端定义的报告函数。

## <a name="remarks"></a>备注

**_CrtSetReportHook**允许应用程序使用其自己的报告函数连接到 C 运行时调试库报告过程。 因此，每当调用 [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) 生成调试报告时，首先调用应用程序的报告函数。 此功能可让应用程序执行操作，例如筛选调试报告，以便它可以专注于特定分配类型或将报表发送到目标不可用，通过使用 **_CrtDbgReport**。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtSetReportHook**在预处理过程中删除。

有关更可靠的版本 **_CrtSetReportHook**，请参阅[_CrtSetReportHook2](crtsetreporthook2-crtsetreporthookw2.md)。

**_CrtSetReportHook**函数安装新客户端定义报告函数中指定*reportHook*并返回以前的客户端定义挂钩。 以下示例演示了客户端定义的报告挂钩应如何构建原型：

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

其中*reportType*是调试报表类型 (**_CRT_WARN**， **_CRT_ERROR**，或 **_CRT_ASSERT**)，*消息*要包含在报表中，完全装配的调试用户消息和**returnValue**由客户端定义指定的值报告应当返回的函数 **_CrtDbgReport**。 有关可用报告类型的完整说明，请参阅 [_CrtSetReportMode](crtsetreportmode.md) 函数。

如果客户端定义报告函数完全处理的调试消息，以便是必需的任何进一步的报告，则该函数应返回**TRUE**。 当函数返回**FALSE**， **_CrtDbgReport**调用以生成调试报告使用报告类型、 模式和文件的当前的设置。 此外，通过指定 **_CrtDbgReport**在中返回值**returnValue**，应用程序还可以控制是否发生了一个调试中断。 有关如何配置和生成调试报告的完整说明，请参阅 **_CrtSetReportMode**， [_CrtSetReportFile](crtsetreportfile.md)，和 **_CrtDbgReport**。

有关使用其他具有挂钩功能的运行时函数和编写你自己的客户端定义挂钩函数的详细信息，请参阅[编写调试挂钩函数](/visualstudio/debugger/debug-hook-function-writing)。

> [!NOTE]
> 如果你的应用程序进行编译的 **/clr**和报告的函数调用后已退出应用程序主，CLR 将引发异常，如果报告的函数调用任何 CRT 函数。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_CrtSetReportHook**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetReportHook](crtgetreporthook.md)<br/>
