---
title: "调试例程 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.debug
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], using macros
- macros, debugging with
- debug routines
- debug macros
- debugging [CRT], run-time routines
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
caps.latest.revision: 11
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
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: fc61db0c2078432ab32030ce897884275d8d2084

---
# <a name="debug-routines"></a>调试例程
C 运行时库的调试版本提供了很多诊断服务，便于调试程序并允许开发人员执行以下操作：  
  
-   在调试期间直接执行运行时函数  
  
-   解决断言、错误和异常  
  
-   跟踪堆分配，并防止出现内存泄漏  
  
-   向用户报告调试消息  
  
 若要使用这些例程，必须定义 [_DEBUG](../c-runtime-library/debug.md) 标志。 所有这些例程在零售版本的应用程序中不执行任何操作。 有关如何使用新的调试例程的详细信息，请参阅 [CRT 调试技术](/visualstudio/debugger/crt-debugging-techniques)。  
  
### <a name="debug-versions-of-the-c-run-time-library-routines"></a>C 运行时库例程的调试版本  
  
|例程|使用|.NET Framework 等效项|  
|-------------|---------|-------------------------------|  
|[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|计算表达式，并在结果是 FALSE 时生成调试报告|[System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|类似于 `_ASSERT`，但包括生成报告中的失败表达式|[System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[_CrtCheckMemory](../c-runtime-library/reference/crtcheckmemory.md)|确认在调试堆上分配的内存块的完整性|[System::Diagnostics::PerformanceCounter](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)|  
|[_CrtDbgBreak](../c-runtime-library/reference/crtdbgbreak.md)|设置一个断点。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtDbgReport、_CrtDbgReportW](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)|生成具有用户消息的调试报表并将此报表发送到三个可能的目标|[System::Diagnostics::Debug::Write](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.write.aspx)、[System::Diagnostics::Debug::Writeline](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writeline.aspx)、[System::Diagnostics::Debug::WriteIf](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writeif.aspx)、[System::Diagnostics::Debug::WriteLineIf](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writelineif.aspx)|  
|[_CrtDoForAllClientObjects](../c-runtime-library/reference/crtdoforallclientobjects.md)|为堆中的所有 `_CLIENT_BLOCK` 类型调用应用程序提供的函数|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtDumpMemoryLeaks](../c-runtime-library/reference/crtdumpmemoryleaks.md)|发生了大量内存泄漏时转储调试堆上的所有内存块|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtIsMemoryBlock](../c-runtime-library/reference/crtismemoryblock.md)|确认指定的内存块位于本地堆，并且具有有效的调试堆块类型标识符|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtIsValidHeapPointer](../c-runtime-library/reference/crtisvalidheappointer.md)|验证指定的指针是否位于本地堆中|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtIsValidPointer](../c-runtime-library/reference/crtisvalidpointer.md)|验证指定的内存范围对于读取和写入是否有效|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtMemCheckpoint](../c-runtime-library/reference/crtmemcheckpoint.md)|获取调试堆的当前状态并将其存储在应用程序提供的 `_CrtMemState` 结构中|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtMemDifference](../c-runtime-library/reference/crtmemdifference.md)|比较两个内存状态的重要差异，并返回结果|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md)|在提取指定检查点之后或者在开始执行程序时转储堆上的有关对象的信息|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtMemDumpStatistics](../c-runtime-library/reference/crtmemdumpstatistics.md)|以用户可读的形式转储指定内存状态的调试标头信息|[System::Diagnostics::PerformanceCounter](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)|  
|[_CrtReportBlockType](../c-runtime-library/reference/crtreportblocktype.md)|返回与给定调试堆块指针相关联的块类型/子类型。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md)|通过挂钩到 C 运行时调试内存分配过程安装客户端定义的分配函数|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetBreakAlloc](../c-runtime-library/reference/crtsetbreakalloc.md)|在指定的对象分配序号上设置断点|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md)|检索或修改 `_crtDbgFlag` 标志的状态，以控制调试堆管理器的分配行为|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetDumpClient](../c-runtime-library/reference/crtsetdumpclient.md)|安装每次调用调试转储函数来转储 `_CLIENT_BLOCK` 类型内存块时所调用的应用程序定义的函数|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetReportFile](../c-runtime-library/reference/crtsetreportfile.md)|标识被 `_CrtDbgReport` 用作特定报表类型的目标的文件或流|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetReportHook](../c-runtime-library/reference/crtsetreporthook.md)|通过以下方式安装客户端定义的报告函数：将该函数挂钩到 C 运行时调试报告过程中|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetReportHook2、_CrtSetReportHookW2](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)|通过以下方式安装或卸载客户端定义的报告函数：将该函数挂钩到 C 运行时调试报告过程中。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_CrtSetReportMode](../c-runtime-library/reference/crtsetreportmode.md)|指定由 `_CrtDbgReport` 生成的特定报表类型的一般目标|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_RPT&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|通过调用带格式字符串和可变数量参数的 `_CrtDbgReport` 生成调试报表来跟踪应用程序的进度。 提供了无源文件和行号信息。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_RPTF&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|类似于 `_RPTn` 宏，但提供发起报表请求的源文件名和行号|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_calloc_dbg](../c-runtime-library/reference/calloc-dbg.md)|在具有额外空间的堆中为调试标头和覆盖缓冲区分配指定数量的内存块|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_expand_dbg](../c-runtime-library/reference/expand-dbg.md)|通过展开或收缩块调整堆上指定内存块的大小|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_free_dbg](../c-runtime-library/reference/free-dbg.md)|释放堆上的内存块|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_fullpath_dbg、_wfullpath_dbg](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)|创建指定相对路径名称的绝对或完整路径名称，使用 [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) 来分配内存。|[System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|  
|[_getcwd_dbg、_wgetcwd_dbg](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md)|获取当前工作目录，使用 [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) 来分配内存。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md)|在具有额外空间的堆中为调试标头和覆盖缓冲区分配内存块|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_msize_dbg](../c-runtime-library/reference/msize-dbg.md)|计算堆上的内存块大小|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_realloc_dbg](../c-runtime-library/reference/realloc-dbg.md)|通过移动和/或调整块的大小重新分配堆上的指定内存块|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_strdup_dbg、_wcsdup_dbg](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)|复制字符串，使用 [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) 来分配内存。|[System::String::Clone](https://msdn.microsoft.com/en-us/library/system.string.clone.aspx)|  
|[_tempnam_dbg、_wtempnam_dbg](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md)|生成可用于创建临时文件的名称，使用 [_malloc_dbg](../c-runtime-library/reference/malloc-dbg.md) 来分配内存。|不适用。 若要调用标准 C 函数，请使用 `PInvoke`。 有关详细信息，请参阅[平台调用示例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
  
 可以使用调试例程逐步完成调试过程中大部分其他 C 运行时例程的源代码。 但是，Microsoft 认为一些技术是专有的，因此，不会为这些例程提供源代码。 这些例程大多数属于异常处理或浮点处理组，但也包含一些其他例程。 下表列出了这些例程。  
  
### <a name="c-run-time-routines-that-are-not-available-in-source-code-form"></a>无法提供源代码形式的 C 运行时例程  
  
||||  
|-|-|-|  
|[acos、acosf、acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|[_fpclass](../c-runtime-library/reference/fpclass-fpclassf.md)|[_nextafter](../c-runtime-library/reference/nextafter-functions.md)|  
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|  
|[atan、atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[_fpreset](../c-runtime-library/reference/fpreset.md)|[printf、_printf_l、wprintf、_wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)、[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)*|  
|[_cabs](../c-runtime-library/reference/cabs.md)|[frexp](../c-runtime-library/reference/frexp.md)|[_scalb](../c-runtime-library/reference/scalb.md)|  
|[ceil](../c-runtime-library/reference/ceil-ceilf-ceill.md)|[_hypot](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|[scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)、[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)*|  
|[_chgsign、_chgsignf、_chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|[_isnan](../c-runtime-library/reference/isnan-isnan-isnanf.md)|[setjmp](../c-runtime-library/reference/setjmp.md)|  
|[_clear87、_clearfp](../c-runtime-library/reference/clear87-clearfp.md)|[_j0](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|  
|[_control87、_controlfp、\__control87_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)|[_j1](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[sinh](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|  
|[copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|[_jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|  
|[cos](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[ldexp](../c-runtime-library/reference/ldexp.md)|[_status87、_statusfp](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|  
|[cosh](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[Exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[tanh](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[_logb](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|[_y0](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|  
|[_finite](../c-runtime-library/reference/finite-finitef.md)|[longjmp](../c-runtime-library/reference/longjmp.md)|[_y1](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|  
|[floor](../c-runtime-library/reference/floor-floorf-floorl.md)|[_matherr](../c-runtime-library/reference/matherr.md)|[_yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|  
|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[modf](../c-runtime-library/reference/modf-modff-modfl.md)||  
  
 \*   尽管为大部分此例程提供源代码，它仍会对另一个不提供源代码的例程执行内部调用。  
  
 从应用程序的调试版本执行调用时，某些 C 运行时函数和 C++ 运算符存在行为差异。 （请注意，应用程序的调试版本可以通过定义 `_DEBUG` 标志或与 C 运行时库的调试版本进行链接来完成。）行为差异通常包含由例程提供的额外功能或信息，以支持调试过程。 下表列出了这些例程。  
  
### <a name="routines-that-behave-differently-in-a-debug-build-of-an-application"></a>应用程序调式版本中存在行为差异的例程  
  
|||  
|-|-|  
|C [abort](../c-runtime-library/reference/abort.md) 例程|C++ [delete](../cpp/delete-operator-cpp.md) 运算符|  
|C[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) 例程|C++ [new](../cpp/new-operator-cpp.md) 运算符|  
  
## <a name="see-also"></a>另请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)   
 [运行时错误检查](../c-runtime-library/run-time-error-checking.md)


<!--HONumber=Feb17_HO4-->


