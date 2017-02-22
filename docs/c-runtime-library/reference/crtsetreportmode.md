---
title: "_CrtSetReportMode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtSetReportMode"
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
  - "_CrtSetReportMode"
  - "CrtSetReportMode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CrtSetReportMode 函数"
  - "CrtSetReportMode 函数"
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# _CrtSetReportMode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定目的地或是由 `_CrtDbgReport` 生成的特定报告类型的目的地和任意调用 [\_CrtDbgReport、\_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 的宏命令，例如 [\_ASSERT、\_ASSERTE、\_ASSERT\_EXPR 宏](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)、[\_ASSERT、\_ASSERTE、\_ASSERT\_EXPR 宏](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)、[\_RPT、\_RPTF、\_RPTW、\_RPTFW 宏](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) 和 [\_RPT、\_RPTF、\_RPTW、\_RPTFW 宏](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) （只限缺陷版本）。  
  
## 语法  
  
```  
int _CrtSetReportMode(   
   int reportType,  
   int reportMode   
);  
```  
  
#### 参数  
 `reportType`  
 报告类型：`_CRT_WARN`、`_CRT_ERROR` 和 `_CRT_ASSERT`。  
  
 `reportMode`  
 新报表模式或 `reportType`模式。  
  
## 返回值  
 成功完成后，`_CrtSetReportMode` 返回之前报告模式或是 `reportType` 指定的报告模式。  如果作为 `reportType` 的无效值传递，或是被指定为`reportMode` 的无效模式，将如 [参数验证](../../c-runtime-library/parameter-validation.md) 描述`_CrtSetReportMode` 调用无效参数处理程序。  如果继续执行，这个函数设置`errno`为`EINVAL` 并返回\-1。  有关详细信息，请参阅[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_CrtSetReportMode` 指定 `_CrtDbgReport` 的输出目的地。  因为宏命令 `_ASSERT`、`_ASSERTE`, `_RPT` 和 `_RPTF` 调用 `_CrtDbgReport`、`_CrtSetReportMode` 指定特定的宏指令文本的输出目的地。  
  
 当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时， `_CrtSetReportMode` 调用在预处理期间被移除。  
  
 如果没有调用 `_CrtSetReportMode` 定义消息的输出目的地，那么以下的默认情况有效：  
  
-   断言失败和错误订向到调试消息窗口。  
  
-   来自 Windows 应用程序的警告被发送到调试器的输出窗口中。  
  
-   不会显示来自控制台应用程序的警告。  
  
 下表列出了在 Crtdbg.h 定义的报表类型。  
  
|报告类型|描述|  
|----------|--------|  
|`_CRT_WARN`|无需立即关注警告、消息和信息。|  
|`_CRT_ERROR`|需要立即关注错误、不可恢复的问题和议题。|  
|`_CRT_ASSERT`|断言失败（断言表达式值为 `FALSE`）。|  
  
 `_CrtSetReportMode` 函数分配 `reportMode` 中指定的新报告模式到 `reportType` 指定的报告类型中，并且返回之前 `reportType` 定义的报告模式。  下表列出了 `reportMode` 的可用选项以及 `_CrtDbgReport` 的结果行为：  这些选项在Crtdbg.h定义为位标志。  
  
|报告模式|\_CrtDbgReport 行为|  
|----------|-----------------------|  
|`_CRTDBG_MODE_DEBUG`|消息写入到调试器的输出窗口中。|  
|`_CRTDBG_MODE_FILE`|写入消息到一个用户提供的文件处理程序中。  应调用 [\_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) 定义指定的文件或作为目的地使用的流。|  
|`_CRTDBG_MODE_WNDW`|创建消息框连同`Abort`、`Retry` 和 `Ignore` 按钮显示该信息。|  
|`_CRTDBG_REPORT_MODE`|返回指定的 `reportType` 的 `reportMode`：<br /><br /> 1   `_CRTDBG_MODE_FILE`<br /><br /> 2   `_CRTDBG_MODE_DEBUG`<br /><br /> 4   `_CRTDBG_MODE_WNDW`|  
  
 可以使用一个，两个或三个模式或无模式报告每个报表类型。  因此，对单个报表类型定义多个目的地是有可能的。  例如，以下的代码片段引起的断言失败被发送到缺陷消息窗口和 `stderr`：  
  
```  
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );  
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );  
```  
  
 此外，可以单独控制报告模式或模式每个报告类型。  例如，有可能指定 `_CRT_WARN` 的一个 `reportType` 发送到输出缺陷字符串，而如之前所解释的，使用缺陷消息窗口显示 `_CRT_ASSERT` 和发送到 `stderr` 。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_CrtSetReportMode`|\<crtdbg.h\>|\<errno.h\>|  
  
 有关兼容性的详细信息，请参阅简介中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
 **库：** 只适用于调试版本 [CRT 库功能](../../c-runtime-library/crt-library-features.md) 。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)