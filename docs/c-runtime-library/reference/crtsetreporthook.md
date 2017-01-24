---
title: "_CrtSetReportHook | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtSetReportHook"
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
  - "_CrtSetReportHook"
  - "CrtSetReportHook"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "CrtSetReportHook 函数"
  - "_CrtSetReportHook 函数"
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtSetReportHook
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

通过挂接到C运行时调试申报程序（仅调试版本）来安装一个客户端自定义报告函数。  
  
## 语法  
  
```  
_CRT_REPORT_HOOK _CrtSetReportHook(   
   _CRT_REPORT_HOOK reportHook   
);  
```  
  
#### 参数  
 `reportHook`  
 新建客户端自定义报告函数挂接到C运行时调试报告程序。  
  
## 返回值  
 返回上一个客户端定义的报告函数。  
  
## 备注  
 `_CrtSetReportHook` 允许应用程序使用自身的报告函数到运行时调试库报告程序中。  结果是，每当 [\_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 被调用生成一个调试报告时，应用程序的报告函数先会被调用。  此功能使应用程序能够执行如过滤调试报告的操作，以致于专注于特定的分配类型或是通过使用 `_CrtDbgReport` 发送报告到不可达的目的地。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时，在预处理期间移除对 `_CrtSetReportHook` 的调用。  
  
 对于 `_CrtSetReportHook` 更强大的版本，请参阅 [\_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)。  
  
 `_CrtSetReportHook` 函数安装在 `reportHook` 指定的新的客户端自定义报告函数，并返回前一个客户端自定义挂钩。  下面的示例演示一个客户端自定义的报告挂钩应如何被原型化：  
  
```  
int YourReportHook( int reportType, char *message, int *returnValue );  
```  
  
 `reportType` 属于调试报告类型 \(`_CRT_WARN`， `_CRT_ERROR`， 或 `_CRT_ASSERT`\)，`message`是要包含在报告中的完全组装调试的用户信息，并且 `returnValue` 是通过 `_CrtDbgReport` 返回的客户端自定义报告函数的特定值。  对于可用报告类型的完整描述，请参阅 [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 函数。  
  
 如果客户端自定义报告函数彻底地处理了调试消息，以致于不需要进一步的报告，接着这函数应该返回 `TRUE`。  当函数返回 `FALSE`，则调用 `_CrtDbgReport` 使用当前的报告类型、模式和文件的设置生成调试报告。  此外，通过指定 `returnValue` 中的 `_CrtDbgReport` 返回值 , 该应用程序也能控制调试中断是否发生。  对于如何配制和生成调试报告的完整描述，请参阅 `_CrtSetReportMode`、[\_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) 和 `_CrtDbgReport`。  
  
 有关使用其他运行时钩子函数并编写客户定义钩子函数的更多信息，请参见[编写调试挂钩函数](../Topic/Debug%20Hook%20Function%20Writing.md)。  
  
> [!NOTE]
>  如果你的应用程序使用 `/clr` 编译，并且在该应用程序退出主函数后调用报告函数，那么报告函数调用任意的 CRT 函数，CLR将抛出异常。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_CrtSetReportHook`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_CrtGetReportHook](../../c-runtime-library/reference/crtgetreporthook.md)