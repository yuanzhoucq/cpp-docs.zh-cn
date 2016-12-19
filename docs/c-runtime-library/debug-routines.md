---
title: "调试例程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.debug"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "调试 [CRT], 使用宏"
  - "宏, 使用...进行调试"
  - "调试例程"
  - "调试宏"
  - "调试 [CRT]，运行时例程"
ms.assetid: cb4d2664-10f3-42f7-a516-595558075471
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 调试例程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C 运行库的调试版本提供了许多诊断服务使调试程序更容易并允许开发人员：  
  
-   在调试期间，直接单步进入的运行时函数。  
  
-   解析断言、错误和异常  
  
-   跟踪堆分配并防止内存泄漏  
  
-   报告调试消息给用户  
  
 使用这些实例， [\_DEBUG](../c-runtime-library/debug.md) 标记必须被定义。  所有任何这些实例不执行应用程序的发布版本。  想要了解更多关于新的调试的实例信息，参见 [CRT Debugging Techniques](../Topic/CRT%20Debugging%20Techniques.md)。  
  
### C 运行库实例的调试版本  
  
|例程|用途|.NET Framework 等效项|  
|--------|--------|------------------------|  
|[\_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|计算表达式并且当结果为FALSE时，生成调试报告|[\<caps:sentence id\="tgt15" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[\_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)|类似于 `_ASSERT` ，但是错误表达式包括在产生的报告里面|[\<caps:sentence id\="tgt18" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[\_CrtCheckMemory](../c-runtime-library/reference/crtcheckmemory.md)|确认在调试堆中内存块的完整性|[\<caps:sentence id\="tgt20" sentenceid\="e42975224af21ff11a761e6a6bdbd602" class\="tgtSentence"\>System::Diagnostics::PerformanceCounter\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)|  
|[\_CrtDbgBreak](../c-runtime-library/reference/crtdbgbreak.md)|设置断点。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtDbgReport、\_CrtDbgReportW](../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)|生成有用户消息的调试报表并将报告送到三个可能的目标|[System::Diagnostics::Debug::Write](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.write.aspx),[System::Diagnostics::Debug::Writeline](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writeline.aspx),[System::Diagnostics::Debug::WriteIf](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writeif.aspx),[System::Diagnostics::Debug::WriteLineIf](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.writelineif.aspx)|  
|[\_CrtDoForAllClientObjects](../c-runtime-library/reference/crtdoforallclientobjects.md)|为所有堆里的 `_CLIENT_BLOCK` 类型，调用一个应用程序提供的功能|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtDumpMemoryLeaks](../c-runtime-library/reference/crtdumpmemoryleaks.md)|当发生大量内存泄漏时，转储所有在调试堆中的内存块|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtIsMemoryBlock](../c-runtime-library/reference/crtismemoryblock.md)|验证在本地堆中的指定的内存块，它包含有效调试堆块类型的标识符|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtIsValidHeapPointer](../c-runtime-library/reference/crtisvalidheappointer.md)|验证本地堆中的特定指针|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtIsValidPointer](../c-runtime-library/reference/crtisvalidpointer.md)|验证用于读取和写入的指定的内存范围是有效的|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtMemCheckpoint](../c-runtime-library/reference/crtmemcheckpoint.md)|获取当前状态的调试堆并存储在一个由应用程序提供的 `_CrtMemState` 结构。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtMemDifference](../c-runtime-library/reference/crtmemdifference.md)|比较两个内存状态的重大不同并返回结果|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtMemDumpAllObjectsSince](../c-runtime-library/reference/crtmemdumpallobjectssince.md)|因为指定的检查点被执行或从程序执行的开始，请转储在堆中有关对象的信息|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtMemDumpStatistics](../c-runtime-library/reference/crtmemdumpstatistics.md)|为用户可读的形式中的一个指定的内存状态，转储一个调试头信息|[\<caps:sentence id\="tgt64" sentenceid\="e42975224af21ff11a761e6a6bdbd602" class\="tgtSentence"\>System::Diagnostics::PerformanceCounter\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.performancecounter.aspx)|  
|[\_CrtReportBlockType](../c-runtime-library/reference/crtreportblocktype.md)|返回与给定的调试堆块的指针相关联的块类型\/子类型。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetAllocHook](../c-runtime-library/reference/crtsetallochook.md)|通过利用连接到C运行时调试内存分配过程中安装一个客户端定义的配置功能|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetBreakAlloc](../c-runtime-library/reference/crtsetbreakalloc.md)|设置在指定的排序对象分配编号上设置断点|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md)|检索或修改 `_crtDbgFlag` 标志的状态来控制调试堆管理器的分配行为|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetDumpClient](../c-runtime-library/reference/crtsetdumpclient.md)|安装一个每次被调用的应用定义的函数，调试转存函数被调用来转存 `_CLIENT_BLOCK` 类型的内存块|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetReportFile](../c-runtime-library/reference/crtsetreportfile.md)|识别文件或流被用作于由一个特定的报告类型 `_CrtDbgReport` 的目标文件|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetReportHook](../c-runtime-library/reference/crtsetreporthook.md)|通过利用连接到C运行时调试报告程序过程中安装一个客户端定义的配置功能|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetReportHook2、\_CrtSetReportHookW2](../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)|通过挂接到C运行时调试申报程序来安装或卸载一个客户端自定义报告函数。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_CrtSetReportMode](../c-runtime-library/reference/crtsetreportmode.md)|指定常规目标文件通过 `_CrtDbgReport` 产生特定报告类型|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_RPT&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|跟踪应用程序的进程产生一个调试报告，通过调用 `_CrtDbgReport` 一个格式字符串和一个可变数目的参数。  不提供源文件和行号信息。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_RPTF&#91;0,1,2,3,4&#93;](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md)|类似于 `_RPTn` 宏，但其中提供报告发出请求的源文件名和行号|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_calloc\_dbg](../c-runtime-library/reference/calloc-dbg.md)|在具有额外的空间调试堆标头分配指定数目的内存块并覆盖缓冲区|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_expand\_dbg](../c-runtime-library/reference/expand-dbg.md)|调整指定的块在堆中的内存通过展开或收缩块|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_free\_dbg](../c-runtime-library/reference/free-dbg.md)|释放在堆上的内存块|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_fullpath\_dbg, \_wfullpath\_dbg](../c-runtime-library/reference/fullpath-dbg-wfullpath-dbg.md)|创建指定的相对路径名的绝对路径或完整路径名，使用 [\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md) 来分配内存。|[\<caps:sentence id\="tgt129" sentenceid\="57f5d14fd2f1847b8e44146f72e48f72" class\="tgtSentence"\>System::IO::File::Create\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)|  
|[\_getcwd\_dbg、\_wgetcwd\_dbg](../c-runtime-library/reference/getcwd-dbg-wgetcwd-dbg.md)|获得当前工作目录,使用 [\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md) 分配内存。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md)|在具有额外的空间调试堆标头分配内存块并覆盖缓冲区|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_msize\_dbg](../c-runtime-library/reference/msize-dbg.md)|计算堆上内存块的大小|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_realloc\_dbg](../c-runtime-library/reference/realloc-dbg.md)|通过移动和\/或调整块重新分配在堆中的内存块|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_strdup\_dbg, \_wcsdup\_dbg](../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md)|复制一个字符串，使用 [\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md) 来分配内存。|[\<caps:sentence id\="tgt151" sentenceid\="74a4ca1462af4bfed5950888b5c554e1" class\="tgtSentence"\>System::String::Clone\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.string.clone.aspx)|  
|[\_tempnam\_dbg、\_wtempnam\_dbg](../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md)|生成的名称，您可以使用它来创建临时文件，使用 [\_malloc\_dbg](../c-runtime-library/reference/malloc-dbg.md) 来分配内存。|不适用。  若要调用标准 C 函数，请使用 `PInvoke`。  有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。|  
  
 调试程序可以用于单步执行源代码，对于大多数其它的C运行时例程在调试过程中。  但是，微软考虑到一些技术的所有权，因此，对于这些实例不提供源代码。  大部分实例属于异常处理或浮点处理的组，但是其他一些也包括在其中。  下表列出了这些实例。  
  
### C 运行时实例是不可用的源代码形式的  
  
||||  
|-|-|-|  
|[acos、acosf、acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|[\_fpclass](../c-runtime-library/reference/fpclass-fpclassf.md)|[\_nextafter](../c-runtime-library/reference/nextafter-functions.md)|  
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[\_fpieee\_flt](../c-runtime-library/reference/fpieee-flt.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|  
|[atan, atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[\_fpreset](../c-runtime-library/reference/fpreset.md)|[printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md), [printf\_s、\_printf\_s\_l、wprintf\_s、\_wprintf\_s\_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)\*|  
|[\_cabs](../c-runtime-library/reference/cabs.md)|[frexp](../c-runtime-library/reference/frexp.md)|[\_scalb](../c-runtime-library/reference/scalb.md)|  
|[ceil](../c-runtime-library/reference/ceil-ceilf-ceill.md)|[\_hypot](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|[scanf、\_scanf\_l、wscanf、\_wscanf\_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md), [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)\*|  
|[\_chgsign、\_chgsignf、\_chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|[\_isnan](../c-runtime-library/reference/isnan-isnan-isnanf.md)|[setjmp](../c-runtime-library/reference/setjmp.md)|  
|[\_clear87, \_clearfp](../c-runtime-library/reference/clear87-clearfp.md)|[\_j0](../misc/bessel-functions-j0-j1-jn.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|  
|[\_control87、\_controlfp、\_\_control87\_2](../c-runtime-library/reference/control87-controlfp-control87-2.md)|[\_j1](../misc/bessel-functions-j0-j1-jn.md)|[sinh](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|  
|[copysign、copysignf、copysignl、\_copysign、\_copysignf、\_copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|[\_jn](../misc/bessel-functions-j0-j1-jn.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|  
|[cos](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[ldexp](../c-runtime-library/reference/ldexp.md)|[\_status87, \_statusfp](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|  
|[cosh](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[Exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[tanh](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[\_logb](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|[\_y0](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|  
|[\_finite](../c-runtime-library/reference/finite-finitef.md)|[longjmp](../c-runtime-library/reference/longjmp.md)|[\_y1](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|  
|[floor](../c-runtime-library/reference/floor-floorf-floorl.md)|[\_matherr](../c-runtime-library/reference/matherr.md)|[\_yn](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|  
|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[modf](../c-runtime-library/reference/modf-modff-modfl.md)||  
  
 \*虽然源代码用于大多数可用的实例，它执行内部调用到另一个未提供源代码实例。  
  
 一些 C 运行时函数和 C\+\+ 运算符的行为与应用程序的调试版本不同。（注意，应用程序的调试版本可以通过定义 `_DEBUG` 标志或通过与C运行时库的调试版本链接来完成。）性能差异通常包含额外的功能或实例提供支持的调试进程的信息。  下表列出了这些实例。  
  
### 在应用程序的调试版本不同的行为的实例  
  
|||  
|-|-|  
|C [abort](../c-runtime-library/reference/abort.md) 实例|C\+\+ [delete](../cpp/delete-operator-cpp.md) 运算符|  
|C [assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) 实例|C\+\+ [new](../cpp/new-operator-cpp.md) 运算符|  
  
## 请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)   
 [运行时错误检查](../c-runtime-library/run-time-error-checking.md)