---
title: _CrtDbgReport、_CrtDbgReportW
ms.date: 11/04/2016
api_name:
- _CrtDbgReport
- _CrtDbgReportW
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
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
ms.openlocfilehash: 986777f755a749e858f7e51b5aa19f10090db13a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938842"
---
# <a name="_crtdbgreport-_crtdbgreportw"></a>_CrtDbgReport、_CrtDbgReportW

生成具有调试消息的报告并将该报告发送到三个可能的目标（仅限调试版本）。

## <a name="syntax"></a>语法

```C
int _CrtDbgReport(
   int reportType,
   const char *filename,
   int linenumber,
   const char *moduleName,
   const char *format [,
   argument] ...
);
int _CrtDbgReportW(
   int reportType,
   const wchar_t *filename,
   int linenumber,
   const wchar_t *moduleName,
   const wchar_t *format [,
   argument] ...
);
```

### <a name="parameters"></a>参数

*reportType*<br/>
报表类型： **_CRT_WARN**、 **_CRT_ERROR**和 **_CRT_ASSERT**。

*filename*<br/>
指向发生断言/报表的源文件名的指针或**NULL**。

*linenumber*<br/>
发生断言/报表的源文件中的行号或**NULL**。

*moduleName*<br/>
指向声明或报告所出现位置的模块名称（.exe 或 .dll）的指针。

*format*<br/>
指向用于创建用户消息的格式控件字符串的指针。

*实际*<br/>
*格式*使用的可选替换参数。

## <a name="return-value"></a>返回值

对于所有报表目标，如果发生错误， **_CrtDbgReport**和 **_CrtDbgReportW**将返回-1; 如果未遇到任何错误，则返回0。 但是，当报告目标是调试消息窗口且用户单击了“**重试**”按钮时，这些函数将返回 1。 如果用户在“调试消息”窗口中单击了“**中止**”按钮，这些函数将立即中止且不会返回值。

[_RPT、_RPTF](rpt-rptf-rptw-rptfw-macros.md)调试宏调用 **_CrtDbgReport**以生成其调试报告。 这些宏以及[_ASSERT、_ASSERTE](assert-asserte-assert-expr-macros.md)、 [_RPTW](rpt-rptf-rptw-rptfw-macros.md)和[_RPTFW](rpt-rptf-rptw-rptfw-macros.md)的宽字符版本使用 **_CrtDbgReportW**生成其调试报告。 当 **_CrtDbgReport**或 **_CrtDbgReportW**返回1时，这些宏将启动调试程序，前提是实时（JIT）调试处于启用状态。

## <a name="remarks"></a>备注

**_CrtDbgReport**和 **_CrtDbgReportW**可将调试报告发送到三个不同的目标：调试报告文件、调试监视器（Visual Studio 调试器）或调试消息窗口。 两个配置函数 [_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md) 可用于为每种报告类型指定一个或多个目标。 这些函数允许对每种报告类型的一个或多个报告目标进行单独控制。 例如，可以指定 **_CRT_WARN**的*reportType*只发送到调试监视器，而将 **_CRT_ASSERT**的*reportType*发送到调试消息窗口和用户定义的报告文件。

**_CrtDbgReportW**是 **_CrtDbgReport**的宽字符版本。 它的所有输出和字符串参数都采用宽字符字符串；否则它会与单字节字符版本完全相同。

**_CrtDbgReport**和 **_CrtDbgReportW**为调试报告创建用户消息，方法是将*参数*[**n**] 参数替换为*格式*字符串，使用**printf**定义的相同规则，或**wprintf**函数。 然后，这些函数基于当前报表模式和为*reportType*定义的文件，生成调试报告并确定目标。 将报表发送到 "调试消息" 窗口时，"*文件名*"、" **lineNumber**" 和 " *moduleName* " 将包含在该窗口中显示的信息中。

下表列出了报表模式或模式和文件的可用选项，以及 **_CrtDbgReport**和 **_CrtDbgReportW**的结果行为。 在 \<crtdbg.h> 中将这些选项定义为位标志。

|报告模式|报告文件|**_CrtDbgReport**， **_CrtDbgReportW**行为|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|不适用|使用 Windows [OutputDebugString](/windows/win32/api/debugapi/nf-debugapi-outputdebugstringw) API 写入消息。|
|**_CRTDBG_MODE_WNDW**|不适用|调用 Windows [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox) API 创建消息框，以显示该消息以及“ **中止**”、“**重试**”和“**忽略**”按钮。 如果用户单击 "**中止**"，则 **_CrtDbgReport**或 **_CrtDbgReport**会立即中止。 如果用户单击“**重试**”，它将返回 1。 如果用户单击 "**忽略**"，则执行将继续， **_CrtDbgReport**和 **_CrtDbgReportW**返回0。 请注意，在存在错误条件时单击“**忽略**”通常会导致“未定义的行为”。|
|**_CRTDBG_MODE_FILE**|**__HFILE**|使用 Windows [WriteFile](/windows/win32/api/fileapi/nf-fileapi-writefile) API 将消息写入用户提供的**句柄**，但不验证文件句柄的有效性;应用程序负责打开报告文件并传递有效的文件句柄。|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|向**stderr**写入消息。|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|将消息写入**stdout**。|

可将报告发送至一个、两个或三个目标，或不发送至任何目标。 有关指定一种或多种报告模式和报告文件的详细信息，请参阅 [_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md) 函数。 有关使用调试宏和报告函数的详细信息，请参阅[用于报告的宏](/visualstudio/debugger/macros-for-reporting)。

如果你的应用程序需要比 **_CrtDbgReport**和 **_CrtDbgReportW**提供的更大的灵活性，你可以编写自己的报告函数并使用[_CrtSetReportHook](crtsetreporthook.md)将其挂接到 C 运行时库报告机制中。才能.

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_CrtDbgReport**|\<crtdbg.h>|
|**_CrtDbgReportW**|\<crtdbg.h>|

**_CrtDbgReport**和 **_CrtDbgReportW**是 Microsoft 扩展。 有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

```C
// crt_crtdbgreport.c
#include <crtdbg.h>

int main(int argc, char *argv[]) {
#ifdef _DEBUG
   _CrtDbgReport(_CRT_ASSERT, __FILE__, __LINE__, argv[0], NULL);
#endif
}
```

有关如何更改报告函数的示例，请参阅 [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportMode](crtsetreportmode.md)<br/>
[_CrtSetReportFile](crtsetreportfile.md)<br/>
[printf、_printf_l、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
