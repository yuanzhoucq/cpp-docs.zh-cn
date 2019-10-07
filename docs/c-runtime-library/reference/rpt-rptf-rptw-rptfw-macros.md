---
title: _RPT、_RPTF、_RPTW、_RPTFW 宏
ms.date: 11/04/2016
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
- RPT3
- RPTF4
- _RPT4
- RPT1
- _RPTF0
- RPTF3
- _RPTF4
- RPTF1
- RPT4
- _RPT1
- _RPT0
- RPT0
- _RPTF2
- RPTF0
- _RPT3
- _RPT2
- _RPTF3
- RPT2
- _RPTF1
helpviewer_keywords:
- debugging [CRT], using macros
- _RPTW3 macro
- _RPT0 macro
- RPTW4 macro
- _RPTF3 macro
- _RPTW4 macro
- RPTF4 macro
- RPTFW2 macro
- RPTW macros
- RPT1 macro
- _RPTF macros
- RPTFW3 macro
- _RPTW0 macro
- _RPTF0 macro
- macros, debugging with
- _RPTW2 macro
- RPTF3 macro
- RPT3 macro
- RPT0 macro
- _RPT macros
- RPTW3 macro
- _RPTFW macros
- debug reporting macros
- RPTF macros
- RPT macros
- _RPTW macros
- RPTF2 macro
- _RPTF1 macro
- _RPT1 macro
- _RPT4 macro
- _RPTFW2 macro
- _RPTFW1 macro
- RPTF0 macro
- _RPT2 macro
- RPTFW macros
- _RPTW1 macro
- _RPTFW0 macro
- RPT4 macro
- _RPT3 macro
- _RPTFW3 macro
- _RPTF4 macro
- _RPTFW4 macro
- _RPTF2 macro
- RPTW0 macro
- RPTFW4 macro
- RPTFW0 macro
- RPTW2 macro
- RPTF1 macro
- RPT2 macro
- RPTFW1 macro
- RPTW1 macro
ms.assetid: a5bf8b30-57f7-4971-8030-e773b7a1ae13
ms.openlocfilehash: 567fe0a68f5adad6f5d90ef3da9d673a75bb83a6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949087"
---
# <a name="_rpt-_rptf-_rptw-_rptfw-macros"></a>_RPT、_RPTF、_RPTW、_RPTFW 宏

通过生成调试报告跟踪应用程序的进程（仅限调试版本）。 请注意， *n*指定*参数中的*参数数量，可以是0、1、2、3、4或5。

## <a name="syntax"></a>语法

```C
_RPT
      n
      (
   reportType,
   format,
...[args]
);
_RPTFn(
   reportType,
   format,
   [args]
);
_RPTWn(
   reportType,
   format
   [args]
);
_RPTFWn(
   reportType,
   format
   [args]
);
```

### <a name="parameters"></a>参数

*reportType*<br/>
报表类型： **_CRT_WARN**、 **_CRT_ERROR**或 **_CRT_ASSERT**。

*format*<br/>
用于创建用户消息的格式控件字符串。

*args*<br/>
*格式*使用的替换参数。

## <a name="remarks"></a>备注

所有这些宏均采用*reportType*和*格式*参数。 此外，它们还可能需最多四个附加参数，由追加到宏名称的数字表示。 例如， **_RPT0**和 **_RPTF0**不采用其他参数， **_RPT1**和 **_RPTF1**取*arg1*， **_RPT2**和 **_RPTF2**采用*arg1*和**arg2**，依此类推。

**_RPT**和 **_RPTF**宏类似于[printf](printf-printf-l-wprintf-wprintf-l.md)函数，因为它们可用于在调试过程中跟踪应用程序的进度。 不过，这些宏比**printf**更灵活，因为它们不需要包含在 **#ifdef**语句中以防止在应用程序的零售版本中调用这些宏。 这种灵活性通过使用[_debug](../../c-runtime-library/debug.md)宏来实现; **_RPT**和 **_RPTF**宏仅在定义了 **_debug**标志时才可用。 未定义 **_debug**时，将在预处理过程中删除对这些宏的调用。

**_RPTW**和 **_RPTFW**宏是这些宏的宽字符版本。 它们类似于**wprintf** ，并采用宽字符字符串作为参数。

**_RPT**宏调用[_CrtDbgReport](crtdbgreport-crtdbgreportw.md)函数来生成包含用户消息的调试报告。 **_RPTW**宏调用 **_CrtDbgReportW**函数来生成包含宽字符的同一报表。 除了用户消息， **_RPTF**和 **_RPTFW**宏还会创建一个调试报表，其中包含调用报表宏的源文件和行号。 用户消息是通过使用[printf](printf-printf-l-wprintf-wprintf-l.md)函数定义的相同规则，将**arg**[*n*] 参数替换为*格式*字符串。

**_CrtDbgReport**或 **_CrtDbgReportW**生成调试报表，并基于为*reportType*定义的当前报表模式和文件确定其目标。 [_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md) 函数用于为每种报告类型定义目标。

如果调用了 **_RPT**宏并且未调用 **_CrtSetReportMode**和 **_CrtSetReportFile** ，则消息显示如下。

|报告类型|输出目标|
|-----------------|------------------------|
|**_CRT_WARN**|不显示警告文本。|
|**_CRT_ERROR**|弹出窗口。 如果指定了 `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);`，则相同。|
|**_CRT_ASSERT**|与 **_CRT_ERROR**相同。|

当目标是调试消息窗口并且用户选择 "**重试**" 按钮时， **_CrtDbgReport**或 **_CrtDbgReportW**将返回1，导致这些宏启动调试器（前提是启用了实时（JIT）调试）。 有关将这些宏用作调试错误处理机制的详细信息，请参阅[使用宏进行验证和报告](/visualstudio/debugger/macros-for-reporting)。

另外还有其他两个生成调试报告的宏： [_ASSERT](assert-asserte-assert-expr-macros.md) 宏，但仅在其表达式参数计算结果为 FALSE 时生成报告； [_ASSERTE](assert-asserte-assert-expr-macros.md)与 **_ASSERT**完全相同，但在生成的报表中包含失败的表达式。

## <a name="requirements"></a>要求

|宏|必需的标头|
|-----------|---------------------|
|**_RPT**宏|\<crtdbg.h>|
|**_RPTF**宏|\<crtdbg.h>|
|**_RPTW**宏|\<crtdbg.h>|
|**_RPTFW**宏|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

虽然这些是宏并且可通过包含 Crtdbg.h 来使用，但应用程序必须链接其中的一个调试库，因为这些宏会调用其他运行时函数。

## <a name="example"></a>示例

请参阅 [_ASSERT](assert-asserte-assert-expr-macros.md) 主题中的示例。

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
