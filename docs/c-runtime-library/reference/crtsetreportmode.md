---
title: _CrtSetReportMode
ms.date: 11/04/2016
api_name:
- _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
ms.openlocfilehash: ae7e83ac009d572f8a9f6484519b0cdfb7499ce3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938465"
---
# <a name="_crtsetreportmode"></a>_CrtSetReportMode

指定 **_CrtDbgReport**生成的特定报表类型的目标或目标，以及调用[_CrtDbgReport，_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)的任何宏，如[_ASSERT、_ASSERTE、_ASSERT_EXPR 宏](assert-asserte-assert-expr-macros.md)、 [_ASSERT、_ASSERTE、_ASSERT_EXPR 宏](assert-asserte-assert-expr-macros.md)、 [_RPT、_RPTF、_RPTW、_RPTFW 宏](rpt-rptf-rptw-rptfw-macros.md)和 _RPT、_RPTF、_RPTW、_RPTFW[宏](rpt-rptf-rptw-rptfw-macros.md)（仅限调试版本）。

## <a name="syntax"></a>语法

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>参数

*reportType*<br/>
报表类型： **_CRT_WARN**、 **_CRT_ERROR**和 **_CRT_ASSERT**。

*reportMode*<br/>
*ReportType*的新报表模式或模式。

## <a name="return-value"></a>返回值

成功完成后， **_CrtSetReportMode**将返回在*reportType*中指定的报表类型的以前的报表模式或模式。 如果将无效值作为*reportType*传入或为*reportMode*指定了无效模式，则 **_CrtSetReportMode**将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数会将**errno**设置为**EINVAL** ，并返回-1。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_CrtSetReportMode**指定 **_CrtDbgReport**的输出目标。 由于宏[_ASSERT](assert-asserte-assert-expr-macros.md)、 [_ASSERTE](assert-asserte-assert-expr-macros.md)、 [_RPT](rpt-rptf-rptw-rptfw-macros.md)和[_RPTF](rpt-rptf-rptw-rptfw-macros.md)调用 **_CrtDbgReport**， **_CrtSetReportMode**指定用这些宏指定的文本的输出目标。

未定义[_debug](../../c-runtime-library/debug.md)时，将在预处理过程中删除对 **_CrtSetReportMode**的调用。

如果未调用 **_CrtSetReportMode**来定义消息的输出目标，则以下默认值有效：

- 断言失败和错误会定向到调试消息窗口。

- 警告从 Windows 应用程序发送到调试器的输出窗口。

- 不显示控制台应用程序中的警告。

下表列出了在 Crtdbg.h 中定义的报告类型。

|报告类型|描述|
|-----------------|-----------------|
|**_CRT_WARN**|不需要立即关注的警告、消息和信息。|
|**_CRT_ERROR**|错误、不可恢复的问题和需要立即关注的问题。|
|**_CRT_ASSERT**|断言失败（计算结果为**FALSE**的断言表达式）。|

**_CrtSetReportMode**函数将*reportMode*中指定的新报表模式分配到*reportType*中指定的报表类型，并返回以前为*reportType*定义的报表模式。 下表列出了*reportMode*的可用选项，以及 **_CrtDbgReport**的结果行为。 在 Crtdbg.h 中将这些选项定义为位标志。

|报告模式|_CrtDbgReport 行为|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|将消息写入调试器的输出窗口。|
|**_CRTDBG_MODE_FILE**|将消息写入用户提供的文件句柄。 应调用 [_CrtSetReportFile](crtsetreportfile.md) 来定义要用作目标的特定文件或流。|
|**_CRTDBG_MODE_WNDW**|创建一个消息框，以显示该消息以及 "[中止](abort.md)"、"**重试**" 和 "**忽略**" 按钮。|
|**_CRTDBG_REPORT_MODE**|返回指定*reportType*的*reportMode* ：<br /><br /> 1   **_CRTDBG_MODE_FILE**<br /><br /> 2 **_CRTDBG_MODE_DEBUG**<br /><br /> 4 **_CRTDBG_MODE_WNDW**|

可以使用一种、两种或三种模式，或不使用任何模式报告每种报告类型。 因此，可以为单个报告类型定义多个目标。 例如，以下代码片段将导致断言失败同时发送到调试消息窗口和**stderr**：

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

此外，可以分别控制报告模式和每个报告类型的模式。 例如，可以指定将*reportType*的 **_CRT_WARN**发送到输出调试字符串，同时使用调试消息窗口显示 **_CRT_ASSERT** ，并将其发送到**stderr**，如前文所述。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

**库**仅限[CRT 库功能](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
