---
title: "_CrtSetReportFile | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtSetReportFile"
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
  - "CrtSetReportFile"
  - "_CrtSetReportFile"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "CrtSetReportFile 函数"
  - "_CrtSetReportFile 函数"
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtSetReportFile
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在使用 [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 指定 `_CRTDBG_MODE_FILE`之后，可以指定文件句柄接收文本。   [\_CrtDbgReport、\_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 还用于`_CrtSetReportFile` 指定文本的目标 \(请只调试版本\)。  
  
## 语法  
  
```  
_HFILE _CrtSetReportFile(   
   int reportType,  
   _HFILE reportFile   
);  
```  
  
#### 参数  
 `reportType`  
 报告类型：`_CRT_WARN`、`_CRT_ERROR` 和 `_CRT_ASSERT`。  
  
 `reportFile`  
 `reportType`的新报告文件。  
  
## 返回值  
 在成功完成，`_CrtSetReportFile` 返回为报表类型定义的前一个报告文件指定在 `reportType`。  如果无效值为 `reportType`通过，此函数调用的参数无效处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，`errno`设置为`EINVAL`，并且函数返回`_CRTDBG_HFILE_ERROR`。  有关详细信息，请参阅[errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_CrtSetReportFile` 用于以 [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 函数定义目标或目标的 `_CrtDbgReport`生成的特定报告类型。  当 `_CrtSetReportMode` 调用分配报告的 `_CRTDBG_MODE_FILE` 对特定报表类型的模式时，然后应调用 `_CrtSetReportFile` 定义特定文件或流用作为目标。  当 [\_DEBUG](../../c-runtime-library/debug.md) 未定义时， `_CrtSetReportFile` 调用在预处理期间被移除。  
  
 下表列出了 `reportFile` 的可用选项以及 `_CrtDbgReport` 的结果行为：  这些选项在Crtdbg.h定义为位标志。  
  
 `file handle`  
 该文件中的句柄将会是消息的目标。  不会尝试验证处理的有效性。  必须在文件中打开和关闭句柄。  例如：  
  
```  
HANDLE hLogFile;  
hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,   
   FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,   
   FILE_ATTRIBUTE_NORMAL, NULL);  
_CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);  
_CrtSetReportFile(_CRT_WARN, hLogFile);  
  
_RPT0(_CRT_WARN,"file message\n");  
CloseHandle(hLogFile);  
```  
  
 `_CRTDBG_FILE_STDERR`  
 为 `stderr`的消息写入，可以如下所示重定向：  
  
```  
freopen( "c:\\log2.txt", "w", stderr);  
_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);  
_CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);  
  
_RPT0(_CRT_ERROR,"1st message\n");  
```  
  
 `_CRTDBG_FILE_STDOUT`  
 为 `stdout`的消息写入，你可以重定向。  
  
 `_CRTDBG_REPORT_FILE`  
 返回当前报告模式。  
  
 每个报表类型的报告文件可以单独进行控制。  例如，指定是可能的 `_CRT_ERROR` `reportType` 到 `stderr`报告，而 `_CRT_ASSERT` `reportType` 移至另一个用户定义的文件句柄或流报告。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_CrtSetReportFile`|\<crtdbg.h\>|\<errno.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关更多兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
 **库：** 只适用于调试版本 [CRT 库功能](../../c-runtime-library/crt-library-features.md) 。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)