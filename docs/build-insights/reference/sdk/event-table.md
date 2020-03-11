---
title: C++生成见解 SDK：事件表
description: Visual Studio C++ BUILD Insights SDK 的事件引用
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2ccc8a4ef707942963b85edc6db9e21e05610b54
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856999"
---
# <a name="c-build-insights-sdk-event-table"></a>C++生成见解 SDK：事件表

::: moniker range="<=vs-2015"

C++ BUILD Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio 版本选择器控件设置为 "Visual studio 2017 或 Visual Studio 2019"。

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>编译器事件

[编译器](#compiler)\
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
[函数](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>链接器事件

[链接器](#linker)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[Pass1.log](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[LTCG](#ltcg)\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PASS2](#pass2)

## <a name="event-table"></a>事件表

| 事件 | properties | 说明 |
|--|--|--|
| <a name="back-end-pass"></a>BACK_END_PASS | 类型 | 活动 |
|  | 父项 | [编译程序](#compiler) |
|  | 子女 | [C2_DLL](#c2-dll) |
|  | 属性 | -输入源文件的绝对路径<br/>-输出对象文件的绝对路径 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[BackEndPass](cpp-event-data-types/back-end-pass.md) |
|  | 说明 | 在编译器后端的开始和结束时发生。 此传递负责优化已分析的 C/C++源代码，并将其转换为机器代码。 |
| <a name="bottom-up"></a>BOTTOM_UP | 类型 | 活动 |
|  | 父项 | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | 子女 | 无 |
|  | 属性 | 无 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[BottomUp](cpp-event-data-types/bottom-up.md) |
|  | 说明 | 在整个程序分析的 "自下而上" 阶段开始和结束时发生。 |
| <a name="c1-dll"></a>C1_DLL | 类型 | 活动 |
|  | 父项 | [FRONT_END_PASS](#front-end-pass) |
|  | 子女 | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 属性 | 无 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | 说明 | 在*c1 .dll*或*c1xx*调用的开始和结束时发生。 这些 Dll 是编译器的 C C++和前端。 它们仅由编译器驱动程序（*cl*）调用。 |
| <a name="c2-dll"></a>C2_DLL | 类型 | 活动 |
|  | 父项 | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | 子女 | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | 属性 | 无 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | 说明 | 在*c2 .dll*调用开始和结束时发生。 此 DLL 是编译器的后端。 它由编译器驱动程序（*cl*）调用。 当使用链接时间代码生成时，链接器（*link*）也会调用它。 |
| <a name="code-generation"></a>CODE_GENERATION | 类型 | 活动 |
|  | 父项 | [C2_DLL](#c2-dll) |
|  | 子女 | [FUNCTION](#function)<br/>[THREAD](#thread) |
|  | 属性 | 无 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[Microsoft.extensions.codegeneration](cpp-event-data-types/code-generation.md) |
|  | 说明 | 在后端的代码生成阶段开始和结束时发生。 |
| <a name="command-line"></a>COMMAND_LINE | 类型 | 简单事件 |
|  | 父项 | [编译程序](#compiler)<br/>[器](#linker) |
|  | 子女 | 无 |
|  | 属性 | -用于调用*cl*或*link*的命令行 |
|  | 捕获类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[行为](cpp-event-data-types/command-line.md) |
|  | 说明 | 在编译器和链接器对命令行求值后发生。 计算的命令行包括通过响应文件传递的所有*cl .exe*和*link .exe*参数。 它还包括通过环境变量（如 CL、\_CL\_、LINK 和 \_链接\_）传递的*cl .exe*和*link*参数。 |
| <a name="compiler"></a>编译程序 | 类型 | 活动 |
|  | 父项 | 无 |
|  | 子女 | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | 属性 | -编译器版本<br/>-工作目录<br/>-调用的*cl*的绝对路径 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[调用](cpp-event-data-types/invocation.md)<br/>[编译程序](cpp-event-data-types/compiler.md) |
|  | 说明 | 在*cl*调用的开始和结束时发生。 |
| <a name="environment-variable"></a>ENVIRONMENT_VARIABLE | 类型 | 简单事件 |
|  | 父项 | [编译程序](#compiler)<br/>[器](#linker) |
|  | 子女 | 无 |
|  | 属性 | -环境变量的名称<br/>-环境变量的值。 |
|  | 捕获类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[Value](cpp-event-data-types/environment-variable.md) |
|  | 说明 | 对于在调用 node.js 或*link* *时的*每个现有环境变量发生一次。 |
| <a name="executable-image-output"></a>EXECUTABLE_IMAGE_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [器](#linker) |
|  | 子女 | 无 |
|  | 属性 | -DLL 或可执行输出文件的绝对路径。 |
|  | 捕获类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md) |
|  | 说明 | 当链接器输入之一为 DLL 或可执行图像文件时发生。 |
| <a name="exp-output"></a>EXP_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [器](#linker) |
|  | 子女 | 无 |
|  | 属性 | - *.Exp*输出文件的绝对路径。 |
|  | 捕获类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExpOutput](cpp-event-data-types/exp-output.md) |
|  | 说明 | 在其中一个链接器输出为 *.exp*文件时发生。 |
| <a name="file-input"></a>FILE_INPUT | 类型 | 简单事件 |
|  | 父项 | [编译程序](#compiler)<br/>[器](#linker) |
|  | 子女 | 无 |
|  | 属性 | -输入文件的绝对路径<br/>-输入文件的类型 |
|  | 捕获类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileInput](cpp-event-data-types/file-input.md) |
|  | 说明 | 通知 node.js 或*link*输入时*出现。* |
| <a name="force-inlinee"></a>FORCE_INLINEE | 类型 | 简单事件 |
|  | 父项 | [FUNCTION](#function) |
|  | 子女 | 无 |
|  | 属性 | -强制内联函数的名称。<br/>-强制内联函数的大小，表示为中间指令计数。 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[ForceInlinee](cpp-event-data-types/force-inlinee.md) |
|  | 说明 | 当通过使用 `__forceinline` 关键字将函数强制内联到另一个函数时发生。 |
| <a name="front-end-file"></a>FRONT_END_FILE | 类型 | 活动 |
|  | 父项 | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | 子女 | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 属性 | -文件的绝对路径。 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[FrontEndFile](cpp-event-data-types/front-end-file.md) |
|  | 说明 | 在编译器前端开始和停止处理文件时发生。 此事件是递归的。 当前端正在分析包含文件时，会发生递归。 |
| <a name="front-end-pass"></a>FRONT_END_PASS | 类型 | 活动 |
|  | 父项 | [编译程序](#compiler) |
|  | 子女 | [C1_DLL](#c1-dll) |
|  | 属性 | -输入源文件的绝对路径<br/>-输出对象文件的绝对路径 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[FrontEndPass](cpp-event-data-types/front-end-pass.md) |
|  | 说明 | 在编译器前端处理开始和结束时发生。 此传递负责分析 C/C++源代码并将其转换为中间语言。 |
| <a name="function"></a>才能 | 类型 | 活动 |
|  | 父项 | [CODE_GENERATION](#code-generation)<br/>[THREAD](#thread)<br/>[TOP_DOWN](#top-down) |
|  | 子女 | [FORCE_INLINEE](#force-inlinee) |
|  | 属性 | -函数名称 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[Function](cpp-event-data-types/function.md) |
|  | 说明 | 在开始和结束生成函数的代码时发生。 |
| <a name="imp-lib-output"></a>IMP_LIB_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [器](#linker) |
|  | 子女 | 无 |
|  | 属性 | -导入库输出文件的绝对路径。 |
|  | 捕获类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ImpLibOutput](cpp-event-data-types/imp-lib-output.md) |
|  | 说明 | 链接器的某个输出为导入库时发生。 |
| <a name="lib-output"></a>LIB_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [器](#linker) |
|  | 子女 | 无 |
|  | 属性 | -静态库输出文件的绝对路径。 |
|  | 捕获类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[LibOutput](cpp-event-data-types/lib-output.md) |
|  | 说明 | 链接器的某个输出为静态库时发生。 |
| <a name="linker"></a>器 | 类型 | 活动 |
|  | 父项 | 无 |
|  | 子女 | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PASS1.LOG](#pass1)<br/>[PASS2](#pass2) |
|  | 属性 | -链接器版本<br/>-工作目录<br/>-调用的*链接*的绝对路径 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[调用](cpp-event-data-types/invocation.md)<br/>[链接器](cpp-event-data-types/linker.md) |
|  | 说明 | 在*link .exe*调用的开始和结束时发生。 |
| <a name="ltcg"></a>LTCG | 类型 | 活动 |
|  | 父项 | [PASS1.LOG](#pass1) |
|  | 子女 | [C2_DLL](#c2-dll) |
|  | 属性 | 无 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | 说明 | 在开始和停止链接时代码生成时发生。 |
| <a name="obj-output"></a>OBJ_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [编译程序](#compiler) |
|  | 子女 | 无 |
|  | 属性 | - *.Obj*输出文件的绝对路径 |
|  | 捕获类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ObjOutput](cpp-event-data-types/obj-output.md) |
|  | 说明 | 对于*cl*生成的每个 *.obj*输出发生一次。 |
| <a name="opt-icf"></a>OPT_ICF | 类型 | 活动 |
|  | 父项 | [PASS1.LOG](#pass1) |
|  | 子女 | 无 |
|  | 属性 | 无 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[OptICF](cpp-event-data-types/opt-icf.md) |
|  | 说明 | 在相同的 COMDAT 折叠（/OPT： ICF）链接器优化开始和结束时发生。 |
| <a name="opt-lbr"></a>OPT_LBR | 类型 | 活动 |
|  | 父项 | [PASS1.LOG](#pass1) |
|  | 子女 | 无 |
|  | 属性 | 无 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[OptLBR](cpp-event-data-types/opt-lbr.md) |
|  | 说明 | 在长分支（/OPT： LBR）链接器优化开始和结束时发生。 |
| <a name="opt-ref"></a>OPT_REF | 类型 | 活动 |
|  | 父项 | [PASS1.LOG](#pass1) |
|  | 子女 | 无 |
|  | 属性 | 无 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[OptRef](cpp-event-data-types/opt-ref.md) |
|  | 说明 | 在未引用的函数和数据消除（/OPT： REF）链接器优化开始和停止时发生。 |
| <a name="pass1"></a>PASS1.LOG | 类型 | 活动 |
|  | 父项 | [器](#linker) |
|  | 子女 | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | 属性 | 无 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[Pass1.log](cpp-event-data-types/pass1.md) |
|  | 说明 | 在链接器的传递1开始和结束时发生。 |
| <a name="pass2"></a>PASS2 | 类型 | 活动 |
|  | 父项 | [器](#linker) |
|  | 子女 | 无 |
|  | 属性 | 无 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[Pass2](cpp-event-data-types/pass2.md) |
|  | 说明 | 在链接器的传递2开始和结束时发生。 |
| <a name="pre-ltcg-opt-ref"></a>PRE_LTCG_OPT_REF | 类型 | 活动 |
|  | 父项 | [PASS1.LOG](#pass1) |
|  | 子女 | 无 |
|  | 属性 | 无 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | 说明 | 在取消引用函数和数据（/OPT： REF）的链接器优化传递发生时出现。 它在链接时间代码生成前完成。 |
| <a name="symbol-name"></a>SYMBOL_NAME | 类型 | 简单事件 |
|  | 父项 | [C1_DLL](#c1-dll) |
|  | 子女 | 无 |
|  | 属性 | -类型键<br/> -类型的名称 |
|  | 捕获类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[SymbolName](cpp-event-data-types/symbol-name.md) |
|  | 说明 | 在前端通过后发生：一次针对模板实例化中涉及的每个类型。 键是类型的数字标识符，而名称是其文本表示形式。 类型键在要分析的跟踪中是唯一的。 但是，来自不同编译器前端传递的不同密钥可能指向同一类型。 在不同编译器前端传递之间比较类型需要使用其名称。 在编译器前端处理结束时，将在完成所有模板实例化之后发出 SYMBOL_NAME 事件。 |
| <a name="template-instantiation"></a>TEMPLATE_INSTANTIATION | 类型 | 活动 |
|  | 父项 | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 子女 | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 属性 | -专用类型的键<br/>-主模板的类型的密钥<br/>-已实例化的模板的类型 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[TemplateInstantiation](cpp-event-data-types/template-instantiation.md) |
|  | 说明 | 在模板实例化开始和结束时发生。 主模板类型（如 `vector`）实例化，导致专用类型（如 `std::vector<int>`）。 为这两种类型提供了一个键。 使用[SYMBOL_NAME](#symbol-name)事件将键转换为类型的名称。 类型键在要分析的跟踪中是唯一的。 但是，来自不同编译器前端传递的不同密钥可能指向同一类型。 在不同编译器前端传递之间比较类型需要使用符号名称。 此事件是递归的。 在某些情况下，在前端实例化嵌套模板时，会发生递归。 |
| <a name="thread"></a>THREAD | 类型 | 活动 |
|  | 父项 | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | 子女 | [FUNCTION](#function) |
|  | 属性 | 无 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[线程](cpp-event-data-types/thread.md) |
|  | 说明 | 在编译器后端线程执行开始和结束时发生。 挂起的线程被视为已结束。 将唤醒的线程视为已启动线程。 |
| <a name="top-down"></a>TOP_DOWN | 类型 | 活动 |
|  | 父项 | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | 子女 | [FUNCTION](#function)<br/>[THREAD](#thread) |
|  | 属性 | 无 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[TopDown](cpp-event-data-types/top-down.md) |
|  | 说明 | 在整个程序分析的 "自上而下" 阶段开始和结束时发生。 |
| <a name="whole-program-analysis"></a>WHOLE_PROGRAM_ANALYSIS | 类型 | 活动 |
|  | 父项 | [C2_DLL](#c2-dll) |
|  | 子女 | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | 属性 | 无 |
|  | 捕获类 | [活动](cpp-event-data-types/activity.md)<br/>[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) |
|  | 说明 | 在链接时代码生成的整个程序分析阶段开始和结束时发生。 |

::: moniker-end
