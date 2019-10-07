---
title: _CrtSetReportHook
ms.date: 11/04/2016
api_name:
- _CrtSetReportHook
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
- _CrtSetReportHook
- CrtSetReportHook
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
ms.openlocfilehash: 77c1e499c66a76027e872783e256754ef72e465d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938515"
---
# <a name="_crtsetreporthook"></a>_CrtSetReportHook

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

**_CrtSetReportHook**允许应用程序将其自己的报告函数用于 C 运行时调试库报告过程。 因此，每当调用 [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) 生成调试报告时，首先调用应用程序的报告函数。 此功能使应用程序能够执行诸如筛选调试报表这样的操作，以便可以将精力集中在特定分配类型上，或使用 **_CrtDbgReport**将报表发送到不可用的目标。 未定义[_debug](../../c-runtime-library/debug.md)时，将在预处理过程中删除对 **_CrtSetReportHook**的调用。

有关更可靠的 **_CrtSetReportHook**版本，请参阅[_CrtSetReportHook2](crtsetreporthook2-crtsetreporthookw2.md)。

**_CrtSetReportHook**函数安装*reportHook*中指定的新的客户端定义的报告函数并返回以前的客户端定义的挂钩。 以下示例演示了客户端定义的报告挂钩应如何构建原型：

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

其中， *reportType*是调试报表类型（ **_CRT_WARN**、 **_CRT_ERROR**或 **_CRT_ASSERT**）， *message*是要包含在报表中的完全组合的调试用户消息， **returnValue**是值由客户端定义的报告函数指定，该函数应由 **_CrtDbgReport**返回。 有关可用报告类型的完整说明，请参阅 [_CrtSetReportMode](crtsetreportmode.md) 函数。

如果客户端定义的报告函数完全处理调试消息，以便不需要进一步报告，则函数应返回**TRUE**。 当函数返回**FALSE**时，将调用 **_CrtDbgReport**来生成使用报表类型、模式和文件的当前设置的调试报告。 此外，通过在**returnValue**中指定 **_CrtDbgReport**返回值，应用程序还可以控制是否发生调试中断。 有关如何配置和生成调试报表的完整说明，请参阅 **_CrtSetReportMode**、 [_CrtSetReportFile](crtsetreportfile.md)和 **_CrtDbgReport**。

有关使用其他具有挂钩功能的运行时函数和编写你自己的客户端定义挂钩函数的详细信息，请参阅[编写调试挂钩函数](/visualstudio/debugger/debug-hook-function-writing)。

> [!NOTE]
> 如果你的应用程序是使用 **/clr**编译的，并且在应用程序退出 main 后调用报表函数，则在报表函数调用任何 CRT 函数时，clr 将引发异常。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_CrtSetReportHook**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetReportHook](crtgetreporthook.md)<br/>
