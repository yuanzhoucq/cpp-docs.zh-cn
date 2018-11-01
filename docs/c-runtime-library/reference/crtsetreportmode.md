---
title: _CrtSetReportMode
ms.date: 11/04/2016
apiname:
- _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
ms.openlocfilehash: 2096d39a8ba316fc76c97517a16e34231940e7f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50595528"
---
# <a name="crtsetreportmode"></a>_CrtSetReportMode

指定的目标或目标的生成的特定报表类型 **_CrtDbgReport**和调用任何宏[_CrtDbgReport、 _CrtDbgReportW](crtdbgreport-crtdbgreportw.md)，如[_ASSERT、 _ASSERTE、_ASSERT_EXPR 宏](assert-asserte-assert-expr-macros.md)， [_ASSERT、 _ASSERTE、 _ASSERT_EXPR 宏](assert-asserte-assert-expr-macros.md)， [_RPT、 _RPTF、 _RPTW、 _RPTFW 宏](rpt-rptf-rptw-rptfw-macros.md)，并[_RPT、 _RPTF、 _RPTW、 _RPTFW 宏](rpt-rptf-rptw-rptfw-macros.md)（仅限在调试版本中）。

## <a name="syntax"></a>语法

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>参数

*reportType*<br/>
报告类型： **_CRT_WARN**， **_CRT_ERROR**，并 **_CRT_ASSERT**。

*reportMode*<br/>
新报告模式或模式*reportType*。

## <a name="return-value"></a>返回值

成功完成后， **_CrtSetReportMode**返回上一个报告模式中指定的报告类型*reportType*。 如果为传入的值无效*reportType*或为指定无效模式*reportMode*， **_CrtSetReportMode**调用无效参数处理程序作为中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数可设置**errno**到**EINVAL**并返回-1。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_CrtSetReportMode**指定的输出目标 **_CrtDbgReport**。 因为宏[_ASSERT](assert-asserte-assert-expr-macros.md)， [_ASSERTE](assert-asserte-assert-expr-macros.md)， [_RPT](rpt-rptf-rptw-rptfw-macros.md)，以及[_RPTF](rpt-rptf-rptw-rptfw-macros.md)调用 **_CrtDbgReport**， **_CrtSetReportMode**指定这些宏指定的文本的输出目标。

当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtSetReportMode**在预处理过程中删除。

如果不调用 **_CrtSetReportMode**若要定义输出目标的消息，然后以下默认值是在起作用：

- 断言失败和错误会定向到调试消息窗口。

- 警告从 Windows 应用程序发送到调试器的输出窗口。

- 不显示控制台应用程序中的警告。

下表列出了在 Crtdbg.h 中定义的报告类型。

|报告类型|描述|
|-----------------|-----------------|
|**_CRT_WARN**|不需要立即关注的警告、消息和信息。|
|**_CRT_ERROR**|错误、不可恢复的问题和需要立即关注的问题。|
|**_CRT_ASSERT**|断言失败 (断言表达式的计算结果为**FALSE**)。|

**_CrtSetReportMode**函数将分配中指定的新报告模式*reportMode*中指定的报表类型为*reportType* ，并返回之前定义有关报表模式*reportType*。 下表列出了可用选项*reportMode*和产生的行为 **_CrtDbgReport**。 在 Crtdbg.h 中将这些选项定义为位标志。

|报告模式|_CrtDbgReport 行为|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|将消息写入调试器的输出窗口。|
|**_CRTDBG_MODE_FILE**|将消息写入用户提供的文件句柄。 应调用 [_CrtSetReportFile](crtsetreportfile.md) 来定义要用作目标的特定文件或流。|
|**_CRTDBG_MODE_WNDW**|创建一个消息框显示消息以及[中止](abort.md)，**重试**，并**忽略**按钮。|
|**_CRTDBG_REPORT_MODE**|返回*reportMode*指定*reportType*:<br /><br /> 1 **_CRTDBG_MODE_FILE**<br /><br /> 2 **_CRTDBG_MODE_DEBUG**<br /><br /> 4 **_CRTDBG_MODE_WNDW**|

可以使用一种、两种或三种模式，或不使用任何模式报告每种报告类型。 因此，可以为单个报告类型定义多个目标。 例如，下面的代码段导致将断言失败发送到这两个调试消息窗口和**stderr**:

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

此外，可以分别控制报告模式和每个报告类型的模式。 例如，它是可以指定*reportType*的 **_CRT_WARN**会发送到输出调试字符串，而 **_CRT_ASSERT**是使用调试消息窗口显示并发送到**stderr**，如前面所示。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

**库：** 仅限 [CRT 库功能](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
