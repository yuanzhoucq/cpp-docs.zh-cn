---
title: "_RPT、_RPTF、_RPTW、_RPTFW 宏 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "RPT3"
  - "RPTF4"
  - "_RPT4"
  - "RPT1"
  - "_RPTF0"
  - "RPTF3"
  - "_RPTF4"
  - "RPTF1"
  - "RPT4"
  - "_RPT1"
  - "_RPT0"
  - "RPT0"
  - "_RPTF2"
  - "RPTF0"
  - "_RPT3"
  - "_RPT2"
  - "_RPTF3"
  - "RPT2"
  - "_RPTF1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "调试 [CRT], 使用宏"
  - "_RPTW3 宏"
  - "_RPT0 宏"
  - "RPTW4 宏"
  - "_RPTF3 宏"
  - "_RPTW4 宏"
  - "RPTF4 宏"
  - "RPTFW2 宏"
  - "RPTW 宏"
  - "RPT1 宏"
  - "_RPTF 宏"
  - "RPTFW3 宏"
  - "_RPTW0 宏"
  - "_RPTF0 宏"
  - "宏, 使用...进行调试"
  - "_RPTW2 宏"
  - "RPTF3 宏"
  - "RPT3 宏"
  - "RPT0 宏"
  - "_RPT 宏"
  - "RPTW3 宏"
  - "_RPTFW 宏"
  - "调试报告宏"
  - "RPTF 宏"
  - "RPT 宏"
  - "_RPTW 宏"
  - "RPTF2 宏"
  - "_RPTF1 宏"
  - "_RPT1 宏"
  - "_RPT4 宏"
  - "_RPTFW2 宏"
  - "_RPTFW1 宏"
  - "RPTF0 宏"
  - "_RPT2 宏"
  - "RPTFW 宏"
  - "_RPTW1 宏"
  - "_RPTFW0 宏"
  - "RPT4 宏"
  - "_RPT3 宏"
  - "_RPTFW3 宏"
  - "_RPTF4 宏"
  - "_RPTFW4 宏"
  - "_RPTF2 宏"
  - "RPTW0 宏"
  - "RPTFW4 宏"
  - "RPTFW0 宏"
  - "RPTW2 宏"
  - "RPTF1 宏"
  - "RPT2 宏"
  - "RPTFW1 宏"
  - "RPTW1 宏"
ms.assetid: a5bf8b30-57f7-4971-8030-e773b7a1ae13
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# _RPT、_RPTF、_RPTW、_RPTFW 宏
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过生成调试报告来跟踪应用程序的进度 \(调试仅版本\)。  注意 *n* `args` 中指定参数的数目，也可以是 0，1，2，3，4 或 5。  
  
## 语法  
  
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
  
#### 参数  
 `reportType`  
 报表类型：`_CRT_WARN`、`_CRT_ERROR`或 `_CRT_ASSERT`。  
  
 `format`  
 指针用来创建用户信息格式控制串。  
  
 `args`  
 `format`使用的替换参数。  
  
## 备注  
 所有这些宏接受 `reportType`和 `format`参数。  此外，它们还可能占用四个附加参数，由数后追加宏名。  例如，`_RPT0` 和 `_RPTF0` 都不采用附加参数，`_RPT1`，`_RPTF1` 采用 `arg1`，`_RPT2`，并且 `_RPTF2` 的接受 `arg1` 和 `arg2`，依此类推。  
  
 因为它们可用于调试过程中，跟踪应用程序的进度。`_RPT` 和 `_RPTF` 宏类似于 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 函数。  但是，在 `#ifdef` 语句，因为它们在应用程序的零售版本，不需要将这些宏调用阻止它们比 `printf` 灵活。  使用 [\_DEBUG](../../c-runtime-library/debug.md) 宏，此灵活性实现；，当 `_DEBUG` 标志后，`_RPT` 和 `_RPTF` 宏才可用。  如果未定义 `_DEBUG` 时，在预处理期间，这些宏的调用中移除。  
  
 `_RPTW` 和 `_RPTFW` 宏。这些宏宽字符版本。  它们与 `wprintf` 并采用字符串作为参数。  
  
 `_RPT` 宏调用 [\_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 函数生成的用户消息的调试报告。  `_RPTW` 宏调用 `_CrtDbgReportW` 函数生成使用宽字符相同的报告。  除了用户消息外，`_RPTF` 和 `_RPTFW` 宏创建利用报告宏调用的源文件和行号的调试报告。  用户消息通过重写 `arg`\[*n*\] 的参数创建到 `format` 字符串，可以使用 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 函数定义的规则相同。  
  
 `_CrtDbgReport` 或 `_CrtDbgReportW` 生成调试报告并确定根据当前报表模式和文件的其目标定义为 `reportType`。  [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 和 [\_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) 函数用于定义各报表类型的目标。  
  
 如果 `_RPT` 宏调用，并且 `_CrtSetReportMode` 和 `_CrtSetReportFile` 没有调用，如下消息显示。  
  
|报告类型|输出目标|  
|----------|----------|  
|`_CRT_WARN`|警告文本不会显示。|  
|`_CRT_ERROR`|弹出消息随即显示。  同样，就如同 `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` 指定。|  
|`_CRT_ASSERT`|与 `_CRT_ERROR` 相同。|  
  
 当目标为调试消息窗口时，并且用户选择 **重试** 按钮，则返回 `_CrtDbgReport` 或 `_CrtDbgReportW`，1 会导致这些宏，启动调试器，然后调试实时 \(JIT\) 启用条件下。  有关使用这些宏的更多信息作为调试错误处理机制，请参见 [使用验证或报告的宏](../Topic/Macros%20for%20Reporting.md)。  
  
 生成调试报告的其他两宏存在。  只有在表达式参数的计算结果为 false 时，[\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏，但是，生成报告。  [\_ASSERTE](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 是完全相同，`_ASSERT`，但包括不合格的表达式在生成的报告。  
  
## 要求  
  
|宏|必需的标头|  
|-------|-----------|  
|`_RPT` 宏|\<CRTDBG.H\>|  
|`_RPTF` 宏|\<CRTDBG.H\>|  
|`_RPTW` 宏|\<CRTDBG.H\>|  
|`_RPTFW` 宏|\<CRTDBG.H\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
 虽然是宏并包括 Crtdbg.h 获取，应用程序必须与调试库链接之一，因为这些宏调用其他运行时函数。  
  
## 示例  
 参见 [\_ASSERT](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 主题中的示例。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)