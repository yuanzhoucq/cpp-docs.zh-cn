---
title: C++ Build Insights SDK：事件表
description: Visual Studio C++ Build Insights SDK 的事件参考
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Events
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6b1cf6871329fcce3166495e173360a88ac38ee0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224209"
---
# <a name="c-build-insights-sdk-event-table"></a>C++ Build Insights SDK：事件表

::: moniker range="<=vs-2015"

C++ Build Insights SDK 与 Visual Studio 2017 及更高版本兼容。 若要查看这些版本的文档，请将本文的 Visual Studio“版本”选择器控件设置为 Visual Studio 2017 或 Visual Studio 2019。 它位于此页面上目录表的顶部。

::: moniker-end
::: moniker range=">=vs-2017"

## <a name="compiler-events"></a>编译器事件

[COMPILER](#compiler)\
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
[THREAD](#thread)\
[FUNCTION](#function)\
[FORCE_INLINEE](#force-inlinee)

## <a name="linker-events"></a>链接器事件

[LINKER](#linker)\
[COMMAND_LINE](#command-line)\
[ENVIRONMENT_VARIABLE](#environment-variable)\
[FILE_INPUT](#file-input)\
[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)\
[EXP_OUTPUT](#exp-output)\
[IMP_LIB_OUTPUT](#imp-lib-output)\
[LIB_OUTPUT](#lib-output)\
[PASS1](#pass1)\
[PRE_LTCG_OPT_REF](#pre-ltcg-opt-ref)\
[LTCG](#ltcg)\
[OPT_REF](#opt-ref)\
[OPT_ICF](#opt-icf)\
[OPT_LBR](#opt-lbr)\
[PASS2](#pass2)

## <a name="event-table"></a>事件表

| 事件 | 属性 | 说明 |
|--|--|--|
| <a name="back-end-pass"></a> BACK_END_PASS | 类型 | 活动 |
|  | 父项 | [COMPILER](#compiler) |
|  | 子女 | [C2_DLL](#c2-dll) |
|  | 属性 | - 输入源文件的绝对路径<br/>- 输出对象文件的绝对路径 |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[BackEndPass](cpp-event-data-types/back-end-pass.md) |
|  | 描述 | 在编译器后端传递开始和结束时发生。 此传递负责优化已分析的 C/C++ 源代码，并将它转换为计算机代码。 |
| <a name="bottom-up"></a> BOTTOM_UP | 类型 | 活动 |
|  | 父项 | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | 子女 | None |
|  | 属性 | None |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[BottomUp](cpp-event-data-types/bottom-up.md) |
|  | 描述 | 在整个程序分析的由下而上传递开始和结束时发生。 |
| <a name="c1-dll"></a> C1_DLL | 类型 | 活动 |
|  | 父项 | [FRONT_END_PASS](#front-end-pass) |
|  | 子女 | [FRONT_END_FILE](#front-end-file)<br/>[SYMBOL_NAME](#symbol-name)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 属性 | None |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[C1DLL](cpp-event-data-types/c1-dll.md) |
|  | 描述 | 在 c1.dll 或 c1xx.dll 调用开始和结束时发生。 这些 DLL 是编译器的 C 和 C++ 前端。 它们仅由编译器驱动程序 (cl.exe) 调用。 |
| <a name="c2-dll"></a> C2_DLL | 类型 | 活动 |
|  | 父项 | [BACK_END_PASS](#back-end-pass)<br/>[LTCG](#ltcg) |
|  | 子女 | [CODE_GENERATION](#code-generation)<br/>[WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | 属性 | None |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[C2DLL](cpp-event-data-types/c2-dll.md) |
|  | 描述 | 在 c2.dll 调用开始和结束时发生。 此 DLL 是编译器的后端。 它由编译器驱动程序 (cl.exe) 调用。 当使用链接时间代码生成时，链接器 (link.exe) 也会调用它。 |
| <a name="code-generation"></a> CODE_GENERATION | 类型 | 活动 |
|  | 父项 | [C2_DLL](#c2-dll) |
|  | 子女 | [FUNCTION](#function)<br/>[THREAD](#thread) |
|  | 属性 | None |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[CodeGeneration](cpp-event-data-types/code-generation.md) |
|  | 描述 | 在后端的代码生成阶段开始和结束时发生。 |
| <a name="command-line"></a> COMMAND_LINE | 类型 | 简单事件 |
|  | 父项 | [COMPILER](#compiler)<br/>[LINKER](#linker) |
|  | 子女 | None |
|  | 属性 | - 用于调用 cl.exe 或 link.exe 的命令行 |
|  | Capture 类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[CommandLine](cpp-event-data-types/command-line.md) |
|  | 描述 | 在编译器和链接器对命令行求值完成后发生。 已求值的命令行包括所有通过响应文件传递的 cl.exe 和 link.exe 参数。 它还包括通过环境变量（如 CL、\_CL\_、LINK 和 \_LINK\_）传递的 cl.exe 和 link.exe 参数。 |
| <a name="compiler"></a> COMPILER | 类型 | 活动 |
|  | 父项 | None |
|  | 子女 | [BACK_END_PASS](#back-end-pass)<br/>[COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[FILE_INPUT](#file-input)<br/>[OBJ_OUTPUT](#obj-output)<br/>[FRONT_END_PASS](#front-end-pass) |
|  | 属性 | - 编译器版本<br/>- 工作目录<br/>- 已调用的 cl.exe 的绝对路径 |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[调用](cpp-event-data-types/invocation.md)<br/>[Compiler](cpp-event-data-types/compiler.md) |
|  | 描述 | 在 cl.exe 调用开始和结束时发生。 |
| <a name="environment-variable"></a> ENVIRONMENT_VARIABLE | 类型 | 简单事件 |
|  | 父项 | [COMPILER](#compiler)<br/>[LINKER](#linker) |
|  | 子女 | None |
|  | 属性 | - 环境变量的名称<br/>- 环境变量的值。 |
|  | Capture 类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[EnvironmentVariable](cpp-event-data-types/environment-variable.md) |
|  | 描述 | 在调用 cl.exe 或 link.exe 时，对每个现有环境变量发生一次。 |
| <a name="executable-image-output"></a> EXECUTABLE_IMAGE_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [LINKER](#linker) |
|  | 子女 | None |
|  | 属性 | - DLL 或可执行输出文件的绝对路径。 |
|  | Capture 类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExecutableImageOutput](cpp-event-data-types/executable-image-output.md) |
|  | 描述 | 当链接器输入之一为 DLL 或可执行图像文件时发生。 |
| <a name="exp-output"></a> EXP_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [LINKER](#linker) |
|  | 子女 | None |
|  | 属性 | - .exp 输出文件的绝对路径。 |
|  | Capture 类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ExpOutput](cpp-event-data-types/exp-output.md) |
|  | 描述 | 当链接器输出之一是 .exp 文件时发生。 |
| <a name="file-input"></a> FILE_INPUT | 类型 | 简单事件 |
|  | 父项 | [COMPILER](#compiler)<br/>[LINKER](#linker) |
|  | 子女 | None |
|  | 属性 | - 输入文件的绝对路径<br/>- 输入文件的类型 |
|  | Capture 类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileInput](cpp-event-data-types/file-input.md) |
|  | 描述 | 为了公布 cl.exe 或 link.exe 输入而发生。 |
| <a name="force-inlinee"></a> FORCE_INLINEE | 类型 | 简单事件 |
|  | 父项 | [FUNCTION](#function) |
|  | 子女 | None |
|  | 属性 | - 强制内联函数的名称。<br/>- 强制内联函数的大小，表示为中间指令计数。 |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[ForceInlinee](cpp-event-data-types/force-inlinee.md) |
|  | 描述 | 当使用 `__forceinline` 关键字将一个函数强制内联到另一个函数时发生。 |
| <a name="front-end-file"></a> FRONT_END_FILE | 类型 | 活动 |
|  | 父项 | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file) |
|  | 子女 | [FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 属性 | - 文件的绝对路径。 |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[FrontEndFile](cpp-event-data-types/front-end-file.md) |
|  | 描述 | 在编译器前端开始和结束处理文件时发生。 此事件是递归的。 当前端正在分析包含的文件时发生递归。 |
| <a name="front-end-pass"></a> FRONT_END_PASS | 类型 | 活动 |
|  | 父项 | [COMPILER](#compiler) |
|  | 子女 | [C1_DLL](#c1-dll) |
|  | 属性 | - 输入源文件的绝对路径<br/>- 输出对象文件的绝对路径 |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[CompilerPass](cpp-event-data-types/compiler-pass.md)<br/>[FrontEndPass](cpp-event-data-types/front-end-pass.md) |
|  | 描述 | 在编译器前端传递开始和结束时发生。 此传递负责分析 C/C++ 源代码，并将它转换为中间语言。 |
| <a name="function"></a> FUNCTION | 类型 | 活动 |
|  | 父项 | [CODE_GENERATION](#code-generation)<br/>[THREAD](#thread)<br/>[TOP_DOWN](#top-down) |
|  | 子女 | [FORCE_INLINEE](#force-inlinee) |
|  | 属性 | - 函数名称 |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[Function](cpp-event-data-types/function.md) |
|  | 描述 | 在开始和结束生成函数代码时发生。 |
| <a name="imp-lib-output"></a> IMP_LIB_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [LINKER](#linker) |
|  | 子女 | None |
|  | 属性 | - 导入库输出文件的绝对路径。 |
|  | Capture 类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ImpLibOutput](cpp-event-data-types/imp-lib-output.md) |
|  | 描述 | 当链接器输出之一是导入库时发生。 |
| <a name="lib-output"></a> LIB_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [LINKER](#linker) |
|  | 子女 | None |
|  | 属性 | - 静态库输出文件的绝对路径。 |
|  | Capture 类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[LibOutput](cpp-event-data-types/lib-output.md) |
|  | 描述 | 当链接器输出之一是静态库时发生。 |
| <a name="linker"></a> LINKER | 类型 | 活动 |
|  | 父项 | None |
|  | 子女 | [COMMAND_LINE](#command-line)<br/>[ENVIRONMENT_VARIABLE](#environment-variable)<br/>[EXECUTABLE_IMAGE_OUTPUT](#executable-image-output)<br/>[EXP_OUTPUT](#exp-output)<br/>[FILE_INPUT](#file-input)<br/>[IMP_LIB_OUTPUT](#imp-lib-output)<br/>[LIB_OUTPUT](#lib-output)<br/>[PASS1](#pass1)<br/>[PASS2](#pass2) |
|  | 属性 | - 链接器版本<br/>- 工作目录<br/>- 已调用 link.exe 的绝对路径 |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[调用](cpp-event-data-types/invocation.md)<br/>[链接器](cpp-event-data-types/linker.md) |
|  | 描述 | 在 link.exe 调用开始和结束时发生。 |
| <a name="ltcg"></a> LTCG | 类型 | 活动 |
|  | 父项 | [PASS1](#pass1) |
|  | 子女 | [C2_DLL](#c2-dll) |
|  | 属性 | None |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[LTCG](cpp-event-data-types/ltcg.md) |
|  | 描述 | 在链接时间代码生成开始和结束时发生。 |
| <a name="obj-output"></a> OBJ_OUTPUT | 类型 | 简单事件 |
|  | 父项 | [COMPILER](#compiler) |
|  | 子女 | None |
|  | 属性 | - .obj 输出文件的绝对路径 |
|  | Capture 类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[FileOutput](cpp-event-data-types/file-output.md)<br/>[ObjOutput](cpp-event-data-types/obj-output.md) |
|  | 描述 | 对由 cl.exe 生成的每个 .obj 输出发生一次。 |
| <a name="opt-icf"></a> OPT_ICF | 类型 | 活动 |
|  | 父项 | [PASS1](#pass1) |
|  | 子女 | None |
|  | 属性 | None |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[OptICF](cpp-event-data-types/opt-icf.md) |
|  | 描述 | 在完全相同的 COMDAT 折叠 (/OPT:ICF) 链接器优化开始和结束时发生。 |
| <a name="opt-lbr"></a> OPT_LBR | 类型 | 活动 |
|  | 父项 | [PASS1](#pass1) |
|  | 子女 | None |
|  | 属性 | None |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[OptLBR](cpp-event-data-types/opt-lbr.md) |
|  | 描述 | 在长分支 (/OPT:LBR) 链接器优化开始和结束时发生。 |
| <a name="opt-ref"></a> OPT_REF | 类型 | 活动 |
|  | 父项 | [PASS1](#pass1) |
|  | 子女 | None |
|  | 属性 | None |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[OptRef](cpp-event-data-types/opt-ref.md) |
|  | 描述 | 在消除未引用的函数和数据 (/OPT:REF) 的链接器优化开始和结束时发生。 |
| <a name="pass1"></a> PASS1 | 类型 | 活动 |
|  | 父项 | [LINKER](#linker) |
|  | 子女 | [LTCG](#ltcg)<br/>[OPT_ICF](#opt-icf)<br/>[OPT_LBR](#opt-lbr)<br/>[OPT_REF](#opt-ref) |
|  | 属性 | None |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[Pass1](cpp-event-data-types/pass1.md) |
|  | 描述 | 在链接器的传递 1 开始和结束时发生。 |
| <a name="pass2"></a> PASS2 | 类型 | 活动 |
|  | 父项 | [LINKER](#linker) |
|  | 子女 | None |
|  | 属性 | None |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[Pass2](cpp-event-data-types/pass2.md) |
|  | 描述 | 在链接器的传递 2 开始和结束时发生。 |
| <a name="pre-ltcg-opt-ref"></a> PRE_LTCG_OPT_REF | 类型 | 活动 |
|  | 父项 | [PASS1](#pass1) |
|  | 子女 | None |
|  | 属性 | None |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[PreLTCGOptRef](cpp-event-data-types/pre-ltcg-opt-ref.md) |
|  | 描述 | 在消除未引用的函数和数据 (/OPT:REF) 的链接器优化传递开始和结束时发生。 它在链接时间代码生成前完成。 |
| <a name="symbol-name"></a> SYMBOL_NAME | 类型 | 简单事件 |
|  | 父项 | [C1_DLL](#c1-dll) |
|  | 子女 | None |
|  | 属性 | - 类型键<br/> - 类型的名称 |
|  | Capture 类 | [SimpleEvent](cpp-event-data-types/simple-event.md)<br/>[SymbolName](cpp-event-data-types/symbol-name.md) |
|  | 描述 | 在前端传递结束时发生：对模板实例化中涉及的每个类型发生一次。 键是类型的数字标识符，而名称是它的文本表示。 类型键在要分析的跟踪中是唯一的。 不过，来自不同编译器前端传递的不同键可能指向相同的类型。 在不同的编译器前端传递之间比较类型需要使用它们的名称。 SYMBOL_NAME 事件在编译器前端传递结束时发出（在所有模板实例化发生后）。 |
| <a name="template-instantiation"></a> TEMPLATE_INSTANTIATION | 类型 | 活动 |
|  | 父项 | [C1_DLL](#c1-dll)<br/>[FRONT_END_FILE](#front-end-file)<br/>[TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 子女 | [TEMPLATE_INSTANTIATION](#template-instantiation) |
|  | 属性 | - 特殊化类型的键<br/>- 主模板的类型的键<br/>- 已实例化的模板的类型 |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[TemplateInstantiation](cpp-event-data-types/template-instantiation.md) |
|  | 描述 | 在模板实例化开始和结束时发生。 主模板类型（如 `vector`）被实例化，从而生成特殊化类型（如 `std::vector<int>`）。 为这两种类型提供了键。 使用 [SYMBOL_NAME](#symbol-name) 事件将键转换为类型的名称。 类型键在要分析的跟踪中是唯一的。 不过，来自不同编译器前端传递的不同键可能指向相同的类型。 在不同的编译器前端传递之间比较类型需要使用符号名称。 此事件是递归的。 在某些情况下，当前端正在实例化嵌套模板时，会发生递归。 |
| <a name="thread"></a> THREAD | 类型 | 活动 |
|  | 父项 | [CODE_GENERATION](#code-generation)<br/>[TOP_DOWN](#top-down) |
|  | 子女 | [FUNCTION](#function) |
|  | 属性 | None |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[线程](cpp-event-data-types/thread.md) |
|  | 描述 | 在编译器后端线程执行开始和结束时发生。 挂起的线程被视为已结束。 唤醒的线程被视为已启动。 |
| <a name="top-down"></a> TOP_DOWN | 类型 | 活动 |
|  | 父项 | [WHOLE_PROGRAM_ANALYSIS](#whole-program-analysis) |
|  | 子女 | [FUNCTION](#function)<br/>[THREAD](#thread) |
|  | 属性 | None |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[TopDown](cpp-event-data-types/top-down.md) |
|  | 描述 | 在整个程序分析的由上而下传递开始和结束时发生。 |
| <a name="whole-program-analysis"></a> WHOLE_PROGRAM_ANALYSIS | 类型 | 活动 |
|  | 父项 | [C2_DLL](#c2-dll) |
|  | 子女 | [BOTTOM_UP](#bottom-up)<br/>[TOP_DOWN](#top-down) |
|  | 属性 | None |
|  | Capture 类 | [活动](cpp-event-data-types/activity.md)<br/>[WholeProgramAnalysis](cpp-event-data-types/whole-program-analysis.md) |
|  | 描述 | 在链接时间代码生成的整个程序分析阶段开始和结束时发生。 |

::: moniker-end
