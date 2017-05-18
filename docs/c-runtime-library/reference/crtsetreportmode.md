---
title: "_CrtSetReportMode | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
caps.latest.revision: 15
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: b7e3cb7562fb63467ef0e0ee28861936fb820fa3
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="crtsetreportmode"></a>_CrtSetReportMode
指定由 `_CrtDbgReport` 生成的特定报告类型以及调用 [_CrtDbgReport、_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 的任何宏（例如 [_ASSERT、_ASSERTE、_ASSERT_EXPR 宏](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)，[_ASSERT、_ASSERTE、_ASSERT_EXPR 宏](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)，[_RPT、_RPTF、_RPTW、_RPTFW 宏](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)和 [_RPT、_RPTF、_RPTW、_RPTFW 宏](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)）的目标（仅限调试版本）。  
  
## <a name="syntax"></a>语法  
  
```  
int _CrtSetReportMode(   
   int reportType,  
   int reportMode   
);  
```  
  
#### <a name="parameters"></a>参数  
 `reportType`  
 报告类型：`_CRT_WARN`、`_CRT_ERROR` 和 `_CRT_ASSERT`。  
  
 `reportMode`  
 新报告模式或 `reportType` 的模式。  
  
## <a name="return-value"></a>返回值  
 成功完成后，`_CrtSetReportMode` 会返回上一个报告模式或在 `reportType` 中指定的报告类型的模式。 如果传入的 `reportType` 值无效或者为 `reportMode` 指定的模式无效，`_CrtSetReportMode` 将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则该函数将 `errno` 设置为 `EINVAL` 并返回 -1。 有关详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `_CrtSetReportMode` 指定 `_CrtDbgReport` 的输出目标。 由于 `_ASSERT`、`_ASSERTE`、`_RPT` 和 `_RPTF` 宏调用 `_CrtDbgReport`，因此，`_CrtSetReportMode` 指定由这些宏指定的文本的输出目标。  
  
 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，会在预处理过程中删除对 `_CrtSetReportMode` 的调用。  
  
 如果不调用 `_CrtSetReportMode` 来定义消息的输出目标，则以下默认值有效：  
  
-   断言失败和错误会定向到调试消息窗口。  
  
-   警告从 Windows 应用程序发送到调试器的输出窗口。  
  
-   不显示控制台应用程序中的警告。  
  
 下表列出了在 Crtdbg.h 中定义的报告类型。  
  
|报告类型|描述|  
|-----------------|-----------------|  
|`_CRT_WARN`|不需要立即关注的警告、消息和信息。|  
|`_CRT_ERROR`|错误、不可恢复的问题和需要立即关注的问题。|  
|`_CRT_ASSERT`|断言失败（求值为 `FALSE` 的断言表达式）。|  
  
 `_CrtSetReportMode` 函数将 `reportMode` 中指定的新报告模式分配给 `reportType` 中指定的报告类型，并返回之前为 `reportType`定义的报告模式。 下表列出了 `reportMode` 的可用选项和 `_CrtDbgReport` 的结果行为。 在 Crtdbg.h 中将这些选项定义为位标志。  
  
|报告模式|_CrtDbgReport 行为|  
|-----------------|-----------------------------|  
|`_CRTDBG_MODE_DEBUG`|将消息写入调试器的输出窗口。|  
|`_CRTDBG_MODE_FILE`|将消息写入用户提供的文件句柄。 应调用 [_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) 来定义要用作目标的特定文件或流。|  
|`_CRTDBG_MODE_WNDW`|创建消息框以与 `Abort`、`Retry` 和 `Ignore` 按钮一起显示消息。|  
|`_CRTDBG_REPORT_MODE`|为指定的 `reportType` 返回 `reportMode`：<br /><br /> 1   `_CRTDBG_MODE_FILE`<br /><br /> 2   `_CRTDBG_MODE_DEBUG`<br /><br /> 4   `_CRTDBG_MODE_WNDW`|  
  
 可以使用一种、两种或三种模式，或不使用任何模式报告每种报告类型。 因此，可以为单个报告类型定义多个目标。 例如，以下代码段导致将断言失败发送到调试消息窗口和 `stderr`：  
  
```  
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );  
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );  
```  
  
 此外，可以分别控制报告模式和每个报告类型的模式。 例如，可以指定将 `_CRT_WARN` 的 `reportType` 发送到输出调试字符串，而使用调试消息窗口显示 `_CRT_ASSERT`，并将其发送到 `stderr`，如前所述。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_CrtSetReportMode`|\<crtdbg.h>|\<errno.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
 **库：**仅限 [CRT 库功能](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)
