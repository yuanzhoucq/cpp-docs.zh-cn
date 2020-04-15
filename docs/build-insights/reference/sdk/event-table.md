---
title: C++生成见解 SDK：事件表
description: 可视化工作室C++构建见解 SDK 的事件参考
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 932b78347e05d313e7962da2fdff8c3454dec963
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81324148"
---
# <a name="c-build-insights-sdk-event-table"></a>C++生成见解 SDK：事件表

::: moniker range="<=vs-2015"

C++构建见解 SDK 与 Visual Studio 2017 及以上版本兼容。 要查看这些版本的文档，请将本文的 Visual Studio**版本**选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面的目录顶部。

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>编译器事件

[编译 器](#compiler)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[OBJ_OUTPUT](#obj-output)\
[FRONT_END_PASS](#front-end-pass)\
[BACK_END_PASS](#back-end-pass)

## <a name="compiler-front-end-events"></a>编译器前端事件

[C1_DLL](#c1-dll)\
[FRONT_END_FILE](#front-end-file)\
[TEMPLATE_INSTANTIATION](#template-instantiation)\
[SYMBOL_NAME](#symbol-name)

## <a name="compiler-back-end-events"></a>编译器后端事件

[C2_DLL](#c2-dll)\
[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis)\
[TOP_DOWN](#top-down)\
[BOTTOM_UP](#bottom-up)\
[CODE_GENERATION](#code-generation)\
[线程](#thread)\
[功能](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>链接器事件

[连接](#linker)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[通过1](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[LTCG](#ltcg)\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PASS2](#pass2)

## <a name="event-table"></a>事件表

| 事件 | Property | 说明 |
|--|--|--|
| <a name="back-end-pass"></a>BACK_END_PASS | 类型 | 活动 |
|  | 父项 | [编译 器](#compiler) |
|  | 子女 | [C2_DLL](#c2-dll) |
|  | 属性 | - 输入源文件的绝对路径<br/>- 输出对象文件的绝对路径 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[编译器通行证](cpp-event-data-types/compiler-pass.md)<br/>[后端通行证](cpp-event-data-types/back-end-pass.md) |
|  | 说明 | 发生在编译器后端传递的开始和结束处。 此通道负责优化解析的 C/C++源代码并将其转换为机器代码。 |
| <a name="bottom-up"></a>BOTTOM_UP | 类型 | 活动 |
|  | 父项 | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | 子女 | None |
|  | 属性 | None |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[自下而上](cpp-event-data-types/bottom-up.md) |
|  | 说明 | 发生在整个程序分析自下而上的开始和结束。 |
| <a name="c1-dll"></a>C1_DLL | 类型 | 活动 |
|  | 父项 | [FRONT_END_PASS](#front-end-pass) |
|  | 子女 | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 属性 | None |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | 说明 | 发生在*c1.dll 或 c1xx.dll*调用的开始和结束处。 *c1xx.dll* 这些 DLL 是编译器的 C 和C++前端。 它们仅由编译器驱动程序 *（cl.exe）* 调用。 |
| <a name="c2-dll"></a>C2_DLL | 类型 | 活动 |
|  | 父项 | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | 子女 | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | 属性 | None |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | 说明 | 发生在*c2.dll*调用的开始和停止处。 此 DLL 是编译器的后端。 它由编译器驱动程序 *（cl.exe）* 调用。 使用链接时间代码生成时，链接器 *（link.exe）* 也会调用它。 |
| <a name="code-generation"></a>CODE_GENERATION | 类型 | 活动 |
|  | 父项 | [C2_DLL](#c2-dll) |
|  | 子女 | [功能](#function)<br/>[线程](#thread) |
|  | 属性 | None |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[代码生成](cpp-event-data-types/code-generation.md) |
|  | 说明 | 发生在后端代码生成阶段的开始和停止处。 |
| <a name="command-line"></a>COMMAND_LINE | 类型 | 简单事件 |
|  | 父项 | [编译 器](#compiler)<br/>[连接](#linker) |
|  | 子女 | None |
|  | 属性 | - 用于调用*cl.exe*或*link.exe*的命令行 |
|  | 捕获类 | [简单事件](cpp-event-data-types/simple-event.md)<br/>[命令行](cpp-event-data-types/command-line.md) |
|  | 说明 | 当编译器和链接器完成计算命令行时发生。 评估的命令行包括通过响应文件传递的所有*cl.exe*和*link.exe*参数。 它还包括通过环境变量（如 CL、CL、LINK\_\_和 LINK \_\_）传递的到*cl.exe*和*link.exe*的参数。 |
| <a name="compiler"></a>编译 器 | 类型 | 活动 |
|  | 父项 | None |
|  | 子女 | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | 属性 | - 编译器版本<br/>- 工作目录<br/>- 被调用*的 cl.exe*的绝对路径 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[调用](cpp-event-data-types/invocation.md)<br/>[编译器](cpp-event-data-types/compiler.md) |
|  | 说明 | 发生在*cl.exe*调用的开头和停止处。 |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | 类型 | 简单事件 |
|  | 父项 | [编译 器](#compiler)<br/>[连接](#linker) |
|  | 子女 | None |
|  | 属性 | - 环境变量的名称<br/>- 环境变量的值。 |
|  | 捕获类 | [简单事件](cpp-event-data-types/simple-event.md)<br/>[EnvironmentVariable](cpp-event-data-types/environment-variable.md) |
|  | 说明 | 在调用*cl.exe*或*link.exe*时，每个现有环境变量发生一次。 |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [连接](#linker) |
|  | 子女 | None |
|  | 属性 | - DLL 或可执行输出文件的绝对路径。 |
|  | 捕获类 | [简单事件](cpp-event-data-types/simple-event.md)<br/>[文件输出](cpp-event-data-types/file-output.md)<br/>[可执行图像输出](cpp-event-data-types/executable-image-output.md) |
|  | 说明 | 当其中一个链接器输入是 DLL 或可执行映像文件时发生。 |
| <a name="exp-output"></a>EXP_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [连接](#linker) |
|  | 子女 | None |
|  | 属性 | - *.exp*输出文件的绝对路径。 |
|  | 捕获类 | [简单事件](cpp-event-data-types/simple-event.md)<br/>[文件输出](cpp-event-data-types/file-output.md)<br/>[Exp输出](cpp-event-data-types/exp-output.md) |
|  | 说明 | 当其中一个链接器输出是 *.exp*文件时发生。 |
| <a name="file-input"></a>FILE_INPUT | 类型 | 简单事件 |
|  | 父项 | [编译 器](#compiler)<br/>[连接](#linker) |
|  | 子女 | None |
|  | 属性 | - 输入文件的绝对路径<br/>- 输入文件的类型 |
|  | 捕获类 | [简单事件](cpp-event-data-types/simple-event.md)<br/>[文件输入](cpp-event-data-types/file-input.md) |
|  | 说明 | 发生以宣布*cl.exe*或*link.exe*输入的情况。 |
| <a name="force-inlinee"></a>FORCE_INLINEE | 类型 | 简单事件 |
|  | 父项 | [功能](#function) |
|  | 子女 | None |
|  | 属性 | - 力内联函数的名称。<br/>- 力内联函数的大小，表示为中间指令计数。 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[力因内](cpp-event-data-types/force-inlinee.md) |
|  | 说明 | 当函数通过关键字强制内联到另一个函数中时发生`__forceinline`。 |
| <a name="front-end-file"></a>FRONT_END_FILE | 类型 | 活动 |
|  | 父项 | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | 子女 | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 属性 | - 文件的绝对路径。 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[前端文件](cpp-event-data-types/front-end-file.md) |
|  | 说明 | 当编译器前端启动并停止处理文件时发生。 此事件是递归的。 当前端正在分析包含的文件时，就会发生递归。 |
| <a name="front-end-pass"></a>FRONT_END_PASS | 类型 | 活动 |
|  | 父项 | [编译 器](#compiler) |
|  | 子女 | [C1_DLL](#c1-dll) |
|  | 属性 | - 输入源文件的绝对路径<br/>- 输出对象文件的绝对路径 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[编译器通行证](cpp-event-data-types/compiler-pass.md)<br/>[前端通票](cpp-event-data-types/front-end-pass.md) |
|  | 说明 | 发生在编译器前端传递的开始和结束处。 此传递负责分析 C/C++源代码并将其转换为中间语言。 |
| <a name="function"></a>功能 | 类型 | 活动 |
|  | 父项 | [CODE_GENERATION](#code-generation)<br/>[线程](#thread)<br/>[TOP_DOWN](#top-down) |
|  | 子女 | [FORCE_INLINEE](#force-inlinee) |
|  | 属性 | - 函数的名称 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[函数](cpp-event-data-types/function.md) |
|  | 说明 | 在启动和结束生成函数的代码时发生。 |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [连接](#linker) |
|  | 子女 | None |
|  | 属性 | - 导入库输出文件的绝对路径。 |
|  | 捕获类 | [简单事件](cpp-event-data-types/simple-event.md)<br/>[文件输出](cpp-event-data-types/file-output.md)<br/>[ImpLib输出](cpp-event-data-types/imp-lib-output.md) |
|  | 说明 | 当链接器的一个输出是导入库时，就会发生。 |
| <a name="lib-output"></a>LIB_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [连接](#linker) |
|  | 子女 | None |
|  | 属性 | - 静态库输出文件的绝对路径。 |
|  | 捕获类 | [简单事件](cpp-event-data-types/simple-event.md)<br/>[文件输出](cpp-event-data-types/file-output.md)<br/>[Lib输出](cpp-event-data-types/lib-output.md) |
|  | 说明 | 当链接器的一个输出是静态库时发生。 |
| <a name="linker"></a>连接 | 类型 | 活动 |
|  | 父项 | None |
|  | 子女 | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[通过1](#pass1)<br/>[PASS2](#pass2) |
|  | 属性 | - 链接器版本<br/>- 工作目录<br/>- 调用*的链接的绝对路径. exe* |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[调用](cpp-event-data-types/invocation.md)<br/>[链接器](cpp-event-data-types/linker.md) |
|  | 说明 | 在*链接*的开头和停止时发生。 |
| <a name="ltcg"></a>LTCG | 类型 | 活动 |
|  | 父项 | [通过1](#pass1) |
|  | 子女 | [C2_DLL](#c2-dll) |
|  | 属性 | None |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | 说明 | 在链接时间代码生成的开始和停止处发生。 |
| <a name="obj-output"></a>OBJ_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [编译 器](#compiler) |
|  | 子女 | None |
|  | 属性 | - *.obj*输出文件的绝对路径 |
|  | 捕获类 | [简单事件](cpp-event-data-types/simple-event.md)<br/>[文件输出](cpp-event-data-types/file-output.md)<br/>[Obj输出](cpp-event-data-types/obj-output.md) |
|  | 说明 | 对于*cl.exe*生成的每个 *.obj*输出发生一次。 |
| <a name="opt-icf"></a>OPT_ICF | 类型 | 活动 |
|  | 父项 | [通过1](#pass1) |
|  | 子女 | None |
|  | 属性 | None |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[OptICF](cpp-event-data-types/opt-icf.md) |
|  | 说明 | 在相同的 COMDAT 折叠 （/OPT：ICF） 链接器优化的开始和结束处发生。 |
| <a name="opt-lbr"></a>OPT_LBR | 类型 | 活动 |
|  | 父项 | [通过1](#pass1) |
|  | 子女 | None |
|  | 属性 | None |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[OptLBR](cpp-event-data-types/opt-lbr.md) |
|  | 说明 | 在长分支 （/OPT：LBR） 链接器优化的开始和结束处发生。 |
| <a name="opt-ref"></a>OPT_REF | 类型 | 活动 |
|  | 父项 | [通过1](#pass1) |
|  | 子女 | None |
|  | 属性 | None |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[OptRef](cpp-event-data-types/opt-ref.md) |
|  | 说明 | 在未引用函数和数据消除 （/OPT：REF） 链接器优化的开始和停止处发生。 |
| <a name="pass1"></a>通过1 | 类型 | 活动 |
|  | 父项 | [连接](#linker) |
|  | 子女 | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | 属性 | None |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[通行证1](cpp-event-data-types/pass1.md) |
|  | 说明 | 发生在链接器通过 1 的开始和结束处。 |
| <a name="pass2"></a>PASS2 | 类型 | 活动 |
|  | 父项 | [连接](#linker) |
|  | 子女 | None |
|  | 属性 | None |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[通行证2](cpp-event-data-types/pass2.md) |
|  | 说明 | 发生在链接器通过 2 的开始和结束处。 |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | 类型 | 活动 |
|  | 父项 | [通过1](#pass1) |
|  | 子女 | None |
|  | 属性 | None |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[前LTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | 说明 | 在链接器优化传递的开始和停止处发生，该传递消除了未引用的函数和数据 （/OPT：REF）。 它在链接时间代码生成之前完成。 |
| <a name="symbol-name"></a>SYMBOL_NAME | 类型 | 简单事件 |
|  | 父项 | [C1_DLL](#c1-dll) |
|  | 子女 | None |
|  | 属性 | - 类型键<br/> - 类型的名称 |
|  | 捕获类 | [简单事件](cpp-event-data-types/simple-event.md)<br/>[符号名称](cpp-event-data-types/symbol-name.md) |
|  | 说明 | 发生在前端传递的末尾：模板实例化中涉及的每一种类型一次。 键是类型的数字标识符，而名称是其文本表示形式。 类型键在要分析的跟踪中是唯一的。 但是，来自不同编译器前端传递的不同键可能指向同一类型。 比较不同编译器前端传递之间的类型需要使用它们的名称。 在进行所有模板实例化后，SYMBOL_NAME在编译器前端传递结束时发出事件。 |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | 类型 | 活动 |
|  | 父项 | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 子女 | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 属性 | - 专用类型的键<br/>- 主模板类型的键<br/>- 实例化的模板类型 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[模板即时性](cpp-event-data-types/template-instantiation.md) |
|  | 说明 | 发生在模板实例化的开始和结束。 将实例化主模板类型（`vector`如 ），从而生成专用类型（如`std::vector<int>`）。 为这两种类型指定一个键。 使用[SYMBOL_NAME](#symbol-name)事件将密钥转换为类型的名称。 类型键在要分析的跟踪中是唯一的。 但是，来自不同编译器前端传递的不同键可能指向同一类型。 比较不同编译器前端传递之间的类型需要使用符号名称。 此事件是递归的。 在某些情况下，当前端实例化嵌套模板时，会发生递归。 |
| <a name="thread"></a>线程 | 类型 | 活动 |
|  | 父项 | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | 子女 | [功能](#function) |
|  | 属性 | None |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[线程](cpp-event-data-types/thread.md) |
|  | 说明 | 发生在编译器后端线程执行的开始和结束。 挂起的线程被视为已结束。 正在唤醒的线程被视为已启动。 |
| <a name="top-down"></a>TOP_DOWN | 类型 | 活动 |
|  | 父项 | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | 子女 | [功能](#function)<br/>[线程](#thread) |
|  | 属性 | None |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[自上而下](cpp-event-data-types/top-down.md) |
|  | 说明 | 发生在整个程序分析的自上而下传递的开始和停止。 |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | 类型 | 活动 |
|  | 父项 | [C2_DLL](#c2-dll) |
|  | 子女 | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | 属性 | None |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[整个程序分析](cpp-event-data-types/whole-program-analysis.md) |
|  | 说明 | 在链接时间代码生成的整个程序分析阶段的开始和结束时发生。 |

::: moniker-end
