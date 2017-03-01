---
title: "_CrtSetReportHook | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtSetReportHook
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
- _CrtSetReportHook
- CrtSetReportHook
dev_langs:
- C++
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
caps.latest.revision: 13
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
ms.openlocfilehash: 0815dc124612d4f7d3acd3df147bbfb4e3a5fda0
ms.lasthandoff: 02/24/2017

---
# <a name="crtsetreporthook"></a>_CrtSetReportHook
通过以下方式安装客户端定义的报告函数：将该函数挂钩到 C 运行时调试报告进程（仅限调试版本）中。  
  
## <a name="syntax"></a>语法  
  
```  
_CRT_REPORT_HOOK _CrtSetReportHook(   
   _CRT_REPORT_HOOK reportHook   
);  
```  
  
#### <a name="parameters"></a>参数  
 `reportHook`  
 将新的客户端定义的报告函数挂钩到 C 运行时调试报告进程。  
  
## <a name="return-value"></a>返回值  
 返回之前的客户端定义的报告函数。  
  
## <a name="remarks"></a>备注  
 `_CrtSetReportHook` 允许应用程序将自己的报告函数用于 C 运行时调试库报告进程。 因此，每当调用 [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 生成调试报告时，首先调用应用程序的报告函数。 此功能使应用程序能够执行筛选调试报告等操作，这样它就可以使用 `_CrtDbgReport` 关注特定分配类型或将报告发送到不可用的目标。 未定义 [_DEBUG](../../c-runtime-library/debug.md) 时，会在预处理过程中删除对 `_CrtSetReportHook` 的调用。  
  
 有关 `_CrtSetReportHook` 的更可靠版本，请参阅 [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)。  
  
 `_CrtSetReportHook` 函数安装在 `reportHook` 中指定的新的客户端定义的报告函数，并返回上一个客户端定义的挂钩。 以下示例演示了客户端定义的报告挂钩应如何构建原型：  
  
```  
int YourReportHook( int reportType, char *message, int *returnValue );  
```  
  
 其中 `reportType` 是调试报告类型（`_CRT_WARN`、`_CRT_ERROR` 或 `_CRT_ASSERT`），`message` 是要包含在报告中的已完全装配的调试用户消息，`returnValue` 是由客户端定义的报告函数指定的值，该值由 `_CrtDbgReport` 返回。 有关可用报告类型的完整说明，请参阅 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 函数。  
  
 如果客户端定义的报告函数可完全处理调试消息，从而不需要进一步报告，则该函数应返回 `TRUE`。 当该函数返回 `FALSE` 时，调用 `_CrtDbgReport` 以使用报告类型、模式和文件的当前设置生成调试报告。 此外，通过在 `returnValue` 中指定 `_CrtDbgReport` 返回值，应用程序还可以控制是否发生调试中断。 有关如何配置和生成调试报告的完整说明，请参阅 `_CrtSetReportMode`[_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md) 和 `_CrtDbgReport`。  
  
 有关使用其他具有挂钩功能的运行时函数和编写你自己的客户端定义挂钩函数的详细信息，请参阅[编写调试挂钩函数](/visualstudio/debugger/debug-hook-function-writing)。  
  
> [!NOTE]
>  假设应用程序使用 `/clr` 编译，并且在应用程序退出 main 后调用报告函数，则在报告函数调用任何 CRT 函数时 CLR 将引发异常。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`_CrtSetReportHook`|\<crtdbg.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 等效项  
 不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [_CrtGetReportHook](../../c-runtime-library/reference/crtgetreporthook.md)
