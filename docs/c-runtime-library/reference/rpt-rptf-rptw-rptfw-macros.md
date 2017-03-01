---
title: "_RPT、_RPTF、_RPTW、_RPTFW 宏 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: d8611402652268e0a85170a36355619e5c7335ac
ms.lasthandoff: 02/24/2017

---
# <a name="rpt-rptf-rptw-rptfw-macros"></a>_RPT、_RPTF、_RPTW、_RPTFW 宏
通过生成调试报告跟踪应用程序的进程（仅限调试版本）。 请注意，*n* 指定 `args` 中的参数个数，它可以是 0、1、2、3、4 或 5。  
  
## <a name="syntax"></a>语法  
  
```  
  
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
  
#### <a name="parameters"></a>参数  
 `reportType`  
 报告类型：`_CRT_WARN`、`_CRT_ERROR` 或 `_CRT_ASSERT`。  
  
 `format`  
 用于创建用户消息的格式控件字符串。  
  
 `args`  
 由 `format` 使用的替换参数。  
  
## <a name="remarks"></a>备注  
 所有这些宏均采用 `reportType` 和 `format` 参数。 此外，它们还可能需最多四个附加参数，由追加到宏名称的数字表示。 例如，`_RPT0` 和 `_RPTF0` 不采用附加参数，`_RPT1` 和 `_RPTF1` 采用 `arg1`，`_RPT2` 和 `_RPTF2` 采用 `arg1` 和 `arg2` 等。  
  
 `_RPT` 和 `_RPTF` 宏类似于 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 函数，因为它们可用于跟踪调试过程中的应用程序的进度。 不过，这些宏比 `printf` 更为灵活，因为它们无需包含在 `#ifdef` 语句中，以防止在零售版本的应用程序中调用它们。 这种灵活性是通过使用 [_DEBUG](../../c-runtime-library/debug.md) 宏实现的；`_RPT` 和 `_RPTF` 宏仅在定义了 `_DEBUG` 标志时可用。 未定义 `_DEBUG` 时，会在预处理过程中删除对这些宏的调用。  
  
 `_RPTW` 和 `_RPTFW` 宏是这些宏的宽字符版本。 它们类似于 `wprintf` 并将宽字符字符串用作参数。  
  
 `_RPT` 宏调用 [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 函数，生成包含用户消息的调试报告。 `_RPTW` 宏调用 `_CrtDbgReportW` 函数，生成具有宽字符的同一个报告。 除了用户消息以外，`_RPTF` 和 `_RPTFW` 宏还将创建包含调用报告宏所在的源文件和行号的调试报告。 通过使用由 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 函数定义的相同规则将 `arg`[*n* 参数替换为 `format` 字符串，以创建用户消息。  
  
 `_CrtDbgReport` 或 `_CrtDbgReportW` 会基于当前报告模式以及为 `reportType` 定义的文件，生成调试报告并确定其目标。 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 和 [_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) 函数用于为每种报告类型定义目标。  
  
 如果调用 `_RPT` 宏，但不调用 `_CrtSetReportMode` 或 `_CrtSetReportFile`，则显示以下消息。  
  
|报告类型|输出目标|  
|-----------------|------------------------|  
|`_CRT_WARN`|不显示警告文本。|  
|`_CRT_ERROR`|弹出窗口。 如果指定了 `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);`，则相同。|  
|`_CRT_ASSERT`|与 `_CRT_ERROR` 相同。|  
  
 当目标是调试消息窗口且用户选择“**重试**” 按钮时，`_CrtDbgReport` 或 `_CrtDbgReportW` 返回 1，从而使这些宏启动调试器（前提是启用了实时 (JIT) 调试）。 有关将这些宏用作调试错误处理机制的详细信息，请参阅[使用宏进行验证和报告](/visualstudio/debugger/macros-for-reporting)。  
  
 另外还有其他两个生成调试报告的宏： [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏，但仅在其表达式参数计算结果为 FALSE 时生成报告； [_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏，与 `_ASSERT` 非常类似，但会在生成的报告中包含失败的表达式。  
  
## <a name="requirements"></a>要求  
  
|宏|必需的标头|  
|-----------|---------------------|  
|`_RPT` 宏|\<crtdbg.h>|  
|`_RPTF` 宏|\<crtdbg.h>|  
|`_RPTW` 宏|\<crtdbg.h>|  
|`_RPTFW` 宏|\<crtdbg.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
 虽然这些是宏并且可通过包含 Crtdbg.h 来使用，但应用程序必须链接其中的一个调试库，因为这些宏会调用其他运行时函数。  
  
## <a name="example"></a>示例  
 请参阅 [_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 主题中的示例。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)
