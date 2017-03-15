---
title: "_CrtSetReportFile | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtSetReportFile
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
- CrtSetReportFile
- _CrtSetReportFile
dev_langs:
- C++
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
caps.latest.revision: 16
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
ms.openlocfilehash: 2e97bccf3c9fec12b0856e48aaed53f5c8d84b6a
ms.lasthandoff: 02/24/2017

---
# <a name="crtsetreportfile"></a>_CrtSetReportFile
使用 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 指定 `_CRTDBG_MODE_FILE` 后，可以指定接收消息文本的文件句柄。 `_CrtSetReportFile` 也可由 [_CrtDbgReport、_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 用于指定文本的目标（仅限调试版本）。  
  
## <a name="syntax"></a>语法  
  
```  
_HFILE _CrtSetReportFile(   
   int reportType,  
   _HFILE reportFile   
);  
```  
  
#### <a name="parameters"></a>参数  
 `reportType`  
 报告类型：`_CRT_WARN`、`_CRT_ERROR` 和 `_CRT_ASSERT`。  
  
 `reportFile`  
 `reportType` 的新报告文件。  
  
## <a name="return-value"></a>返回值  
 成功完成后，`_CrtSetReportFile` 返回为在 `reportType` 中指定的报告类型定义的上一个报告文件。 如果为 `reportType` 传入的值无效，则此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 `_CRTDBG_HFILE_ERROR`。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `_CrtSetReportFile` 与 [ _CrtSetReportMode ](../../c-runtime-library/reference/crtsetreportmode.md) 函数一起使用，以定义 `_CrtDbgReport` 生成的特定报告类型的目标。 调用 `_CrtSetReportMode` 为特定报告类型分配 `_CRTDBG_MODE_FILE` 报告模式时，应调用 `_CrtSetReportFile` 来定义要用作目标的特定文件或流。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，会在预处理过程中删除对 `_CrtSetReportFile` 的调用。  
  
 下表显示了 `reportFile` 的可用选项和 `_CrtDbgReport` 的结果行为的列表。 在 Crtdbg.h 中将这些选项定义为位标志。  
  
 `file handle`  
 将作为消息目标的文件的句柄。 不会尝试验证该句柄的有效性。 必须打开并关闭该文件的句柄。 例如：  
  
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
 将消息写入可进行如下重定向的 `stderr`：  
  
```  
freopen( "c:\\log2.txt", "w", stderr);  
_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);  
_CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);  
  
_RPT0(_CRT_ERROR,"1st message\n");  
```  
  
 `_CRTDBG_FILE_STDOUT`  
 将消息写入可进行重定向的 `stdout` 。  
  
 `_CRTDBG_REPORT_FILE`  
 返回当前报告模式。  
  
 可以单独控制每种报告类型所使用的报表文件。 例如，可以指定将 `_CRT_ERROR` 的 `reportType` 报告给 `stderr`，而将 `_CRT_ASSERT` 的 `reportType` 报告给用户定义的文件句柄或流。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_CrtSetReportFile`|\<crtdbg.h>|\<errno.h>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。 与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用中使用它们。 有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
 **库：**仅限 [CRT 库功能](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)
