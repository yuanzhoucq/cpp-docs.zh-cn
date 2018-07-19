---
title: _CrtDbgReport、_CrtDbgReportW | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtDbgReport
- _CrtDbgReportW
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
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
dev_langs:
- C++
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 57290d2985036ea3df2863e175d742c819a3fe03
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32405049"
---
# <a name="crtdbgreport-crtdbgreportw"></a>_CrtDbgReport、_CrtDbgReportW

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
报告类型： **_CRT_WARN**， **_CRT_ERROR**，和 **_CRT_ASSERT**。

*filename*<br/>
指向声明/报告所出现位置的源文件名的指针或**NULL**。

*linenumber*<br/>
断言/报告所出现位置的源文件中的行数或**NULL**。

*moduleName*<br/>
指向声明或报告所出现位置的模块名称（.exe 或 .dll）的指针。

*format*<br/>
指向用于创建用户消息的格式控件字符串的指针。

*自变量*<br/>
通过使用的可选替换自变量*格式*。

## <a name="return-value"></a>返回值

对于所有报告目标， **_CrtDbgReport**和 **_CrtDbgReportW**返回发生错误时为-1 和 0，如果未不遇到任何错误。 但是，当报告目标是调试消息窗口且用户单击了“**重试**”按钮时，这些函数将返回 1。 如果用户在“调试消息”窗口中单击了“**中止**”按钮，这些函数将立即中止且不会返回值。

[_RPT、 _RPTF](rpt-rptf-rptw-rptfw-macros.md)调试宏调用 **_CrtDbgReport**生成其调试报告。 这些宏的宽字符版本，以及[_ASSERT、 _ASSERTE](assert-asserte-assert-expr-macros.md)， [_RPTW](rpt-rptf-rptw-rptfw-macros.md)和[_RPTFW](rpt-rptf-rptw-rptfw-macros.md)，使用 **_CrtDbgReportW**到生成其调试报告。 当 **_CrtDbgReport**或 **_CrtDbgReportW**返回 1 时，这些宏启动调试器，前提是启用了实时 (JIT) 调试。

## <a name="remarks"></a>备注

**_CrtDbgReport**和 **_CrtDbgReportW**可将调试报告发送到三个不同的目标： 调试报告文件、 调试监视器 (Visual Studio 调试器中） 或调试消息窗口。 两个配置函数 [_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md) 可用于为每种报告类型指定一个或多个目标。 这些函数允许对每种报告类型的一个或多个报告目标进行单独控制。 例如，很可能指定*reportType*的 **_CRT_WARN**只能是发送到调试监视器，而*reportType*的 **_CRT_ASSERT**发送到调试消息窗口和用户定义的报告文件。

**_CrtDbgReportW**是宽字符版本的 **_CrtDbgReport**。 它的所有输出和字符串参数都采用宽字符字符串；否则它会与单字节字符版本完全相同。

**_CrtDbgReport**和 **_CrtDbgReportW**通过用替换来创建用户消息为调试报告*参数*[**n**] 参数插入*格式*字符串，并使用定义的相同规则**printf**或**wprintf**函数。 这些函数，然后生成调试报告并确定目标或目标，基于当前报告模式以及文件为*reportType*。 如果将报表发送到调试消息窗口中， *filename*， **lineNumber**，和*moduleName*显示在窗口中的信息中包含。

下表列出了报表模式或模式和文件和产生的行为的可用选项 **_CrtDbgReport**和 **_CrtDbgReportW**。 在 \<crtdbg.h> 中将这些选项定义为位标志。

|报告模式|报告文件|**_CrtDbgReport**， **_CrtDbgReportW**行为|
|-----------------|-----------------|------------------------------------------------|
|**_CRTDBG_MODE_DEBUG**|不适用|使用 Windows [OutputDebugString](http://msdn.microsoft.com/library/windows/desktop/aa363362.aspx) API 写入消息。|
|**_CRTDBG_MODE_WNDW**|不适用|调用 Windows [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) API 创建消息框，以显示该消息以及“ **中止**”、“**重试**”和“**忽略**”按钮。 如果用户单击**中止**， **_CrtDbgReport**或 **_CrtDbgReport**立即中止。 如果用户单击“**重试**”，它将返回 1。 如果用户单击**忽略**，继续执行和 **_CrtDbgReport**和 **_CrtDbgReportW**返回 0。 请注意，在存在错误条件时单击“**忽略**”通常会导致“未定义的行为”。|
|**_CRTDBG_MODE_FILE**|**__HFILE**|将消息写入用户提供**处理**，使用 Windows [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747.aspx) API 而不会验证有效性的文件句柄; 应用程序负责打开报表文件并将传递有效的文件句柄。|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDERR**|将消息写入**stderr**。|
|**_CRTDBG_MODE_FILE**|**_CRTDBG_FILE_STDOUT**|将消息写入**stdout**。|

可将报告发送至一个、两个或三个目标，或不发送至任何目标。 有关指定一种或多种报告模式和报告文件的详细信息，请参阅 [_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md) 函数。 有关使用调试宏和报告函数的详细信息，请参阅[用于报告的宏](/visualstudio/debugger/macros-for-reporting)。

如果你的应用程序需要更多的灵活性，所提供的相比 **_CrtDbgReport**和 **_CrtDbgReportW**，你可以编写自己的报告的函数并将它挂接到 C 运行时库报告通过使用机制[_CrtSetReportHook](crtsetreporthook.md)函数。

## <a name="requirements"></a>要求

|例程|必需的标头|
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
