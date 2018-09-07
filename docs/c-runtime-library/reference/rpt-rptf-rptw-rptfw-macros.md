---
title: _RPT、_RPTF、_RPTW、_RPTFW 宏 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69347ab698661346b8d598dda1bb007d071a21f8
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44104142"
---
# <a name="rpt-rptf-rptw-rptfw-macros"></a>_RPT、_RPTF、_RPTW、_RPTFW 宏

通过生成调试报告跟踪应用程序的进程（仅限调试版本）。 请注意， *n*指定的参数中的数目*args*可以是 0、 1、 2、 3、 4 或 5。

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
报告类型： **_CRT_WARN**， **_CRT_ERROR**，或 **_CRT_ASSERT**。

*format*<br/>
用于创建用户消息的格式控件字符串。

*参数*<br/>
通过使用的替换参数*格式*。

## <a name="remarks"></a>备注

所有这些宏均采用*reportType*并*格式*参数。 此外，它们还可能需最多四个附加参数，由追加到宏名称的数字表示。 例如， **_RPT0**并 **_RPTF0**不采用附加参数， **_RPT1**并 **_RPTF1**采取*arg1*， **_RPT2**并 **_RPTF2**采取*arg1*并**arg2**，依次类推。

**_RPT**并 **_RPTF**宏是类似于[printf](printf-printf-l-wprintf-wprintf-l.md)函数，因为它们可用于在调试过程中跟踪应用程序的进度。 但是，这些宏会比更灵活**printf**因为它们不需要括起来 **#ifdef**语句，以防止其在零售版本的应用程序中调用。 通过使用实现这种灵活性[_DEBUG](../../c-runtime-library/debug.md)宏; **_RPT**并 **_RPTF**宏才可用 **_DEBUG**标志定义。 当 **_DEBUG**是未定义，对这些宏调用删除在预处理期间。

**_RPTW**并 **_RPTFW**宏是这些宏的宽字符版本。 这些槽位就像**wprintf**和将宽字符字符串用作参数。

**_RPT**宏调用[_CrtDbgReport](crtdbgreport-crtdbgreportw.md)函数以生成调试报告具有用户消息。 **_RPTW**宏调用 **_CrtDbgReportW**函数以生成具有宽字符的同一个报表。 **_RPTF**并 **_RPTFW**宏创建具有在其中报告宏调用，除了用户消息的源文件和行号的调试报告。 通过替换来创建用户消息**arg**[*n*] 参数置于*格式*字符串，使用相同的规则定义的[printf](printf-printf-l-wprintf-wprintf-l.md)函数。

**_CrtDbgReport**或 **_CrtDbgReportW**生成调试报告并确定其目标基于当前报告模式和为定义文件*reportType*。 [_CrtSetReportMode](crtsetreportmode.md) 和 [_CrtSetReportFile](crtsetreportfile.md) 函数用于为每种报告类型定义目标。

如果 **_RPT**宏调用均未 **_CrtSetReportMode**也不 **_CrtSetReportFile**已被调用，显示消息，如下所示。

|报告类型|输出目标|
|-----------------|------------------------|
|**_CRT_WARN**|不显示警告文本。|
|**_CRT_ERROR**|弹出窗口。 如果指定了 `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);`，则相同。|
|**_CRT_ASSERT**|与相同 **_CRT_ERROR**。|

当目标是调试消息窗口并且用户选择**重试**按钮， **_CrtDbgReport**或 **_CrtDbgReportW**返回 1，从而使这些宏启动调试程序，前提是启用在实时 (JIT) 调试。 有关将这些宏用作调试错误处理机制的详细信息，请参阅[使用宏进行验证和报告](/visualstudio/debugger/macros-for-reporting)。

另外还有其他两个生成调试报告的宏： [_ASSERT](assert-asserte-assert-expr-macros.md) 宏，但仅在其表达式参数计算结果为 FALSE 时生成报告； [_ASSERTE](assert-asserte-assert-expr-macros.md)非常类似 **_ASSERT**，但生成的报告中包括失败的表达式。

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
