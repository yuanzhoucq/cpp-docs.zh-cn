---
title: C/C++项目属性 (Visual Studio)
ms.date: 7/18/2019
ms.topic: article
ms.assetid: 16375038-4917-4bd0-9a2a-26343c1708b7
ms.openlocfilehash: 91edf30ef0e5f38088727c0280d2edf07cdebfa5
ms.sourcegitcommit: 7b039b5f32f6c59be6c6bb1cffafd69c3bfadd35
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/26/2019
ms.locfileid: "68537566"
---
# <a name="cc-property-pages"></a>C/C++属性页

以下属性页位于**项目** > **属性** > "**配置属性** > " "**C/C++** :

## <a name="cc-general-properties"></a>C/C++常规属性

### <a name="additional-include-directories"></a>附加包含目录

指定一个或多个要添加到包含路径中的目录；存在多个目录时，请用分号分隔。 设置[/i (附加包含目录)](i-additional-include-directories.md)。

### <a name="additional-using-directories"></a>其他 #using 目录

指定要搜索的一个或多个目录 (用分号分隔的目录名称) 来解析传递给 #using 指令的名称。 设置[/AI](ai-specify-metadata-directories.md)。

### <a name="debug-information-format"></a>调试信息格式

指定编译器生成的调试信息的类型。  这需要兼容的链接器设置。 设置[/Z7、/zi、/zi (调试信息格式)](z7-zi-zi-debug-information-format.md)。

**方案**

- 无 - 没有生成调试信息，因此编译可能会更快。
- **C7 兼容**-选择为程序创建的调试信息的类型, 以及是将此信息保存在对象 (.obj) 文件中, 还是保存在程序数据库 (PDB) 中。
- **程序数据库**-生成一个程序数据库 (PDB), 其中包含用于调试器的类型信息和符号调试信息。 符号化调试信息包含变量的名称和类型以及函数和行号。
- **用于 "编辑并继续" 的程序数据库**-以支持 "[编辑并继续](/visualstudio/debugger/edit-and-continue)" 功能的格式生成程序数据库 (如上所述)。

### <a name="support-just-my-code-debugging"></a>支持仅我的代码调试

添加支持代码, 以便在此编译单元中启用[仅我的代码](/visualstudio/debugger/just-my-code)调试。 设置[/JMC](jmc.md)。

### <a name="common-language-runtime-support"></a>公共语言运行时支持

使用 .NET 运行时服务。  此开关与其他某些开关不兼容;有关详细信息, 请参阅[/clr](clr-common-language-runtime-compilation.md)系列交换机上的文档。

**方案**

- **无公共语言运行时支持**-无公共语言运行时支持
- **公共语言运行时支持**-为您的应用程序创建可供其他 clr 应用程序使用的元数据, 并允许您的应用程序使用其他 clr 组件的元数据中的类型和数据。
- **纯 Msil 公共语言运行时支持**-生成仅包含[msil](/dotnet/standard/managed-code)的输出文件 (没有本机可执行代码), 尽管该文件可以包含编译为 MSIL 的本机类型。
- **安全 Msil 公共语言运行时支持**-生成仅限 MSIL (没有本机可执行代码) 和可验证输出文件。

### <a name="consume-windows-runtime-extension"></a>使用 Windows 运行时扩展

使用 Windows 运行时语言扩展。 设置[/ZW](zw-windows-runtime-compilation.md)。

### <a name="suppress-startup-banner"></a>取消显示启动版权标志

当编译器启动时取消显示登录版权标志, 并在编译期间显示信息性消息。

### <a name="warning-level"></a>警告级别

选择编译器对代码错误的严格程度。 设置[/W0-/W4](compiler-option-warning-level.md)。

**方案**

- **关闭所有警告**-级别0禁用所有警告。
- 级别1级别1显示严重警告。 级别1是命令行中的默认警告等级。
- 级别**2-级别**2 显示所有等级1警告和严重程度低于等级1的警告。
- 级别**3-级别**3 显示所有等级2警告以及出于生产目的而建议的所有其他警告。
- **Level4**级别4显示所有等级3警告以及信息性警告, 在大多数情况下可以放心地忽略这些警告。
- 启用所有警告 - 启用所有警告，包括默认情况下禁用的那些警告。

### <a name="treat-warnings-as-errors"></a>将警告视为错误

将所有编译器警告视为错误。 对于新项目, 最好在所有编译中使用[/wx](wx-treat-linker-warnings-as-errors.md) ;解决所有警告将确保尽可能少的难以发现的代码缺陷。

### <a name="warning-version"></a>警告版本

隐藏编译器的特定版本后引入的警告。 设置[\[/Wv:\[.zzzzz。\]\]](wx-treat-linker-warnings-as-errors.md)

### <a name="diagnostics-format"></a>诊断格式

启用丰富的诊断, 并在诊断消息中包含列信息和源上下文。

**方案**

- **脱字号**-在诊断消息中提供列信息, 并输出源代码的相关行, 其中包含表示有问题的列的插入符号。
- **列信息**-此外还提供发出诊断的行中的列号 (如果适用)。
- **经典**-保留以前的简洁诊断消息和行号。

### <a name="sdl-checks"></a>SDL 检查

其他安全性开发生命周期 (SDL) 建议的检查;包括启用其他安全代码生成功能, 并将额外的安全相关警告作为错误启用。 设置[/sdl,/sdl-](sdl-enable-additional-security-checks.md)。

### <a name="multi-processor-compilation"></a>多处理器编译

多处理器编译。

## <a name="cc-optimization-properties"></a>C/C++优化属性

### <a name="optimization"></a>优化

选择代码优化选项;选择 "自定义" 可使用特定的优化选项。 设置[/od](od-disable-debug.md)、 [/O1、/O2](o-options-optimize-code.md)。

**方案**

- 自定义 - 自定义优化。
- 禁用 - 禁用优化。
- **最大优化 (优选大小)** -等效于/Og/Os/Oy/OB2/Gs/gf/gy
- **最大优化 (优选速度)** -等效于/Og/Oi/Ot/Oy/OB2/Gs/gf/gy
- **优化 (优选速度)** -等效于/Og/Oi/Ot/oy/Ob2

### <a name="inline-function-expansion"></a>内联函数展开

选择生成的[内联函数](../../cpp/inline-functions-cpp.md)扩展级别。 设置[/Ob1,/Ob2](ob-inline-function-expansion.md)。

**方案**

- **默认**
- **Disabled** -禁用默认情况下打开的内联展开。
- **仅限 __inline** -仅展开在类声明中定义的C++成员函数中标记为 inline、__inline、__forceinline 或 __inline 的函数。
- **任何适用于**标记为 inline 或 __inline 的任何合适的函数以及编译器选择的任何其他函数 (在编译器自行进行扩展, 通常称为自动内联)。

### <a name="enable-intrinsic-functions"></a>启用内部函数

启用内部函数。  使用内部函数生成的速度更快, 但代码可能更大。 设置[/Oi](oi-generate-intrinsic-functions.md)。

### <a name="favor-size-or-speed"></a>优选大小或速度

是否优选代码大小或代码速度;必须启用 "全局优化"。 设置[/ot,/os](os-ot-favor-small-code-favor-fast-code.md)。

**方案**

- **优选小型代码**, 代码优先于小代码。 通过指示编译器的大小优于速度来最大程度地降低 Exe 和 Dll 的大小。
- **代码**编写速度更快代码。 通过指示编译器优选速度, 使 Exe 和 Dll 的速度最大化。 (这是默认值。)
- 无 **-无**大小和速度优化。

### <a name="omit-frame-pointers"></a>省略帧指针

禁止在调用堆栈上创建帧指针。

### <a name="enable-fiber-safe-optimizations"></a>启用纤程安全优化

使用纤程和线程本地存储区访问时启用内存空间优化。 设置[/GT](gt-support-fiber-safe-thread-local-storage.md)。

### <a name="whole-program-optimization"></a>全程序优化

通过将代码生成延迟到链接时间来启用跨模块优化;要求打开链接器选项 "链接时间代码生成"。 设置[/gl](gl-whole-program-optimization.md)。

## <a name="cc-preprocessor-properties"></a>C/C++预处理器属性

### <a name="preprocessor-definitions"></a>预处理器定义

定义源文件的预处理符号。

### <a name="undefine-preprocessor-definitions"></a>取消定义预处理器定义

指定取消定义一个或多个预处理器。 设置[/u](u-u-undefine-symbols.md)。

### <a name="undefine-all-preprocessor-definitions"></a>取消所有预处理器定义

取消以前定义的所有预处理器值。 设置[/u](u-u-undefine-symbols.md)。

### <a name="ignore-standard-include-paths"></a>忽略标准包含路径

阻止编译器在 INCLUDE 环境变量中指定的目录中搜索包含文件。

### <a name="preprocess-to-a-file"></a>预处理到文件

预处理 C 和C++源文件, 并将预处理的输出写入文件。 此选项取消编译, 因此不生成 .obj 文件。

### <a name="preprocess-suppress-line-numbers"></a>预处理取消显示行号

无 #line 指令的预处理。

### <a name="keep-comments"></a>保留注释

禁止显示源代码中的注释条;要求设置 "预处理" 选项之一。 设置[/c](c-preserve-comments-during-preprocessing.md)。

## <a name="cc-code-generation-properties"></a>C/C++代码生成属性

### <a name="enable-string-pooling"></a>启用字符串池

允许编译器在执行过程中, 在程序映像和内存中创建相同字符串的一个只读副本, 从而导致较小的程序 (称为字符串池的优化)。 [/O1、/O2](o-options-optimize-code.md)和[/zi](z7-zi-zi-debug-information-format.md)会自动设置[/gf](gf-eliminate-duplicate-strings.md)选项。

### <a name="enable-minimal-rebuild"></a>启用最小重新生成

此选项启用最小重新生成，它确定是否需要重新编译包含已更改的 C++ 类定义的 C++ 源文件，该定义存储在头 (.h) 文件中。

### <a name="enable-c-exceptions"></a>启用 C++ 异常

指定将由编译器使用的异常处理模型。

**方案**

- **是, 但有 SEH 异常**-捕获异步 (结构化) 和同步 (C++) 异常的异常处理模型。 设置[/eha](eh-exception-handling-model.md)。
- **是**-仅捕获C++异常的异常处理模型, 并通知编译器假定 extern C 函数永远不会引发C++异常。 设置[/ehsc](eh-exception-handling-model.md)。
- **是, 使用 Extern c 函数**-仅捕获C++异常的异常处理模型, 并通知编译器假定 Extern C 函数确实会引发异常。 设置[/ehs](eh-exception-handling-model.md)。
- **否**-无异常处理。

### <a name="smaller-type-check"></a>较小类型检查

启用到较小类型的转换检查, 与除调试以外的任何优化类型都不兼容。 设置[/RTCc](rtc-run-time-error-checks.md)。

### <a name="basic-runtime-checks"></a>基本运行时检查

执行基本运行时错误检查, 与除调试以外的任何优化类型都不兼容。 设置[/RTCs、/RTCu、/RTC1](rtc-run-time-error-checks.md)。

**方案**

- **堆栈帧**-启用堆栈帧运行时错误检查。
- **未初始化的变量**-在未初始化的情况下使用变量进行报告。
- **两者 (/RTC1, http-equiv)** -等效于/rtcsu。
- **默认**值-默认运行时检查。

### <a name="runtime-library"></a>运行库

指定运行时库以进行链接。 设置[/mt,/MTd,/md,/MDd](md-mt-ld-use-run-time-library.md)。

**方案**

- **多线程**-使应用程序使用多线程的静态运行时库版本。
- **多线程调试**-定义 _DEBUG 和 _MT。 此选项还会让编译器将库名称 LIBCMTD.lib 放置到 .obj 文件中，以便链接器将使用 LIBCMTD.lib 来解析外部符号。
- **多线程 DLL** -使应用程序使用多线程和 DLL 特定版本的运行时库。 定义 _MT 和 _DLL，并使编译器将库名 MSVCRT.lib 放入 .obj 文件中。
- **多线程调试 DLL** -定义 _DEBUG、_MT 和 _DLL, 并使应用程序使用调试多线程和 DLL 特定版本的运行时库。 它还会让编译器将库名称 MSVCRTD.lib 放入 .obj 文件中。

### <a name="struct-member-alignment"></a>结构成员对齐

为结构成员对齐指定1、2、4或8字节边界。 设置[/Zp](zp-struct-member-alignment.md)。

**方案**

- **1**字节边界上1个字节包结构。 与/Zp. 相同
- **2 字节**-在2字节边界上包结构。
- 4字节边界上**4 个字节**包的结构。
- **8 字节**-在8字节边界上打包结构 (默认值)。
- **16 字节**-在16字节边界上包结构。
- **默认**值-默认对齐方式设置。

### <a name="security-check"></a>安全检查

安全检查有助于检查堆栈缓冲区是否超负荷运行，它是一种常见的尝试攻击程序安全的命令。 

**方案**

- 禁用安全检查 - 禁用安全检查。 设置[/GS-](gs-buffer-security-check.md)。
- 启用安全检查 - 启用安全检查。 设置[/gs](gs-buffer-security-check.md)。

### <a name="control-flow-guard"></a>控制流防护

防护安全检查可帮助检测到尝试调度到非法代码块。 

**方案**

- **是**-使用 Guard 集[/Guard: Cf](guard-enable-control-flow-guard.md)启用安全检查。
- **否**

### <a name="enable-function-level-linking"></a>启用函数级别链接

允许编译器以打包函数 (COMDAT) 形式对各个函数进行打包。 需进行此操作后才能编辑并继续工作。 设置[/gy](gy-enable-function-level-linking.md)。

### <a name="enable-parallel-code-generation"></a>启用并行代码生成

启用优化时, 允许编译器为使用 #pragma loop (hint_parallel\[(n)]) 标识的循环生成并行代码。

### <a name="enable-enhanced-instruction-set"></a>启用增强指令集

允许使用在支持增强指令集的处理器上找到的指令, 如 SSE、SSE2、AVX 和 AVX2 增强到 IA-32;AVX 和 AVX2 到 x64。 目前 **/arch: SSE**和 **/arch: SSE2**仅在为 x86 体系结构生成时可用。 如果未指定任何选项, 则编译器将使用在支持 SSE2 的处理器上找到的指令。 可以通过/arch: IA32 禁用增强说明的使用。 有关详细信息, 请参阅[/arch (x86)](arch-x86.md)、 [/arch (x64)](arch-x64.md)和[/arch (ARM)](arch-arm.md) 。

**方案**

- **流式处理 Simd 扩展**-流式处理 simd 扩展。 设置 **/arch: SSE**
- **流式处理 Simd 扩展 2** -流式处理 simd 扩展2。 设置 **/arch: SSE2**
- **高级矢量扩展**-高级矢量扩展。 设置 **/arch: AVX**
- **高级矢量扩展 2** -高级矢量扩展2。 设置 **/arch: AVX2**
- **无增强说明**-无增强说明。 设置 **/arch: IA32**
- **未设置**-未设置。

### <a name="floating-point-model"></a>浮点模型

设置浮点模型。 集[/fp: 精确、/fp: strict、/fp: fast](fp-specify-floating-point-behavior.md)。

**方案**

- **精确**-默认值。 提高了相等性和不相等性的浮点测试的一致性。
- **严格**-最严格的浮点模型。 /fp: strict 导致 fp_contract 为 OFF, fenv_access 为 ON。 /fp: except 是隐含的, 可以通过显式指定/fp: except-来禁用。 与/fp: except、/fp: strict 一起使用时, 将强制实施严格的浮点语义, 但不考虑异常事件。
- **Fast** -在大多数情况下创建最快的代码。

### <a name="enable-floating-point-exceptions"></a>启用浮点异常

可靠的浮点异常模型。 异常将在触发后立即引发。  设置[/fp: except](fp-specify-floating-point-behavior.md)。

### <a name="create-hotpatchable-image"></a>创建可热修补映像

当热修补处于开启状态时, 编译器确保每个函数的第一个指令为两个字节, 这是热修补所必需的。  设置[/hotpatch](hotpatch-create-hotpatchable-image.md)。

### <a name="spectre-mitigation"></a>Spectre 缓解

适用于 CVE 2017-5753 的 Spectre 缓解措施。 设置[/Qspectre](qspectre.md)。

**方案**

- **已启用**-启用 CVE 2017-5753 的 Spectre 缓解功能
- **已禁用**-未设置。

## <a name="cc-language-properties"></a>C/C++ Language 属性

### <a name="disable-language-extensions"></a>禁用语言扩展

取消或启用语言扩展。 设置[/za](za-ze-disable-language-extensions.md)。

### <a name="conformance-mode"></a>一致性模式

启用或取消一致性模式。 设置[/permissive-](permissive-standards-conformance.md)。

### <a name="treat-wchart-as-built-in-type"></a>将 WChar_t 视为内置类型

指定时, 类型 wchar_t 会成为一种映射到 __wchar_t 的本机类型, 其方式与短映射到 __int16 的方式相同。 [/Zc:](zc-wchar-t-wchar-t-is-native-type.md)默认情况下, wchar_t 为 on。

### <a name="force-conformance-in-for-loop-scope"></a>强制 For 循环范围中的一致性

用于通过 Microsoft 扩展C++为 for 语句循环实现标准行为。 设置[/za,/ze (禁用语言扩展](za-ze-disable-language-extensions.md)。 默认情况下，[/Zc:forScope](zc-forscope-force-conformance-in-for-loop-scope.md) 处于打开状态。

### <a name="remove-unreferenced-code-and-data"></a>删除未引用的代码和数据

当指定时, 编译器不再为未引用的代码和数据生成符号信息。

### <a name="enforce-type-conversion-rules"></a>强制实施类型转换规则

用于根据 c + + 11 标准将右值引用类型标识为转换操作的结果。

### <a name="enable-run-time-type-information"></a>启用运行时类型信息

添加在运行时检查 C++ 对象类型（运行时类型信息）的代码。 设置[/GR,/GR-](gr-enable-run-time-type-information.md)。

### <a name="open-mp-support"></a>开放式 MP 支持

启用 OpenMP 2.0 语言扩展。 设置[/openmp](openmp-enable-openmp-2-0-support.md)。

### <a name="c-language-standard"></a>C++ 语言标准

确定编译器C++将强制执行的语言标准。 建议尽可能使用最新版本。 设置[/std: c + + 14,/std: c + + 17,/std: c + + 最新版本](std-specify-language-standard-version.md)。

**方案**

- **默认**
- **ISO c + + 14 标准**
- **ISO c + + 17 标准版**
- **预览-最新C++工作草案的功能**

### <a name="enable-c-modules-experimental"></a>启用C++模块 (实验)

C++模块 TS 和标准库模块的实验性支持。

## <a name="cc-precompiled-headers-properties"></a>C/C++预编译标头属性

### <a name="precompiled-header"></a>预编译头

创建/使用预编译标头:在生成期间启用创建或使用预编译标头。 设置[/yc](yc-create-precompiled-header-file.md)、 [/yu](yu-use-precompiled-header-file.md)。

**方案**

- **Create** -指示编译器创建一个预编译标头 (.pch) 文件, 该文件表示某个时间点的编译状态。
- **Use** -指示编译器在当前编译中使用现有预编译头 (.pch) 文件。
- **不使用预编译标头**-不使用预编译头。

### <a name="precompiled-header-file"></a>预编译标头文件

指定创建或使用预编译头文件时要使用的头文件名。 设置[/yc](yc-create-precompiled-header-file.md), [/yu]] (file.md)。

### <a name="precompiled-header-output-file"></a>预编译头输出文件

指定生成的预编译头文件的路径和/或名称。 设置[/fp](fp-name-dot-pch-file.md)。

## <a name="cc-output-files-properties"></a>C/C++ Output 文件属性

### <a name="expand-attributed-source"></a>展开特性化源

创建列表文件, 将展开的特性插入到源文件中。 设置[/fx](fx-merge-injected-code.md)。

### <a name="assembler-output"></a>汇编程序输出

指定汇编语言输出文件的内容。 设置[/FA、/FAc、/FAs、/FAcs](fa-fa-listing-file.md)。

**方案**

- **无列表**-无列表。
- **仅程序集列表**-程序集代码; .asm
- **带有计算机代码的程序集**-计算机和程序集代码;. 货
- **带源代码的程序集**-源和程序集代码; .asm
- **程序集、计算机代码和源**程序集、计算机代码和源代码;. 货

### <a name="use-unicode-for-assembler-listing"></a>为汇编程序列表使用 Unicode

导致以 UTF-8 格式创建输出文件。

### <a name="asm-list-location"></a>ASM 列表位置

指定 ASM 列表文件的相对路径和/或名称;可以是文件名或目录名。 设置[/Fa](fa-fa-listing-file.md)。

### <a name="object-file-name"></a>对象文件名

指定一个名称以替代默认对象文件名；可以是文件或目录名。 设置[/fo](fo-object-file-name.md)。

### <a name="program-database-file-name"></a>程序数据库文件名

指定编译器生成的 PDB 文件的名称;还指定所需的编译器生成的 .IDB 文件的基名称;可以是文件名或目录名。 设置[/fd](fd-program-database-file-name.md)。

### <a name="generate-xml-documentation-files"></a>生成 XML 文档文件

指定编译器应生成 XML 文档注释文件 (。 .XDC)。 设置[/doc](doc-process-documentation-comments-c-cpp.md)。

### <a name="xml-documentation-file-name"></a>XML 文档文件名

指定生成的 XML 文档文件的名称;可以是文件名或目录名。 设置[/doc:\<name >](doc-process-documentation-comments-c-cpp.md)。

## <a name="cc-browse-information-properties"></a>C/C++浏览信息属性

### <a name="enable-browse-information"></a>启用浏览信息

启用浏览信息:指定 .bsc 文件中的浏览信息的级别。 设置[/fr](fr-fr-create-dot-sbr-file.md)。

### <a name="browse-information-file"></a>浏览信息文件

浏览文件:指定浏览器信息文件的可选名称。 设置[/fr\<名称 >](fr-fr-create-dot-sbr-file.md)。

## <a name="cc-advanced-properties"></a>C/C++ Advanced 属性

### <a name="calling-convention"></a>调用约定

选择应用程序的默认调用约定 (可由函数重写)。 设置[/gd、/Gr、/Gz、/Gv](gd-gr-gv-gz-calling-convention.md)。

**方案**

- **__cdecl** -为除成员函数和标记为 __stdcall 或C++ __fastcall 的函数之外的所有函数指定 __cdecl 调用约定。
- **__fastcall** -为除成员函数和标记为 __cdecl 或C++ __stdcall 的函数之外的所有函数指定 __fastcall 调用约定。 所有 __fastcall 函数都必须具有原型。
- **__stdcall** -为除成员函数和标记为 __cdecl 或C++ __fastcall 的函数之外的所有函数指定 __stdcall 调用约定。 所有 __stdcall 函数都必须具有原型。
- **__vectorcall** -为除成员函数和标记为 __cdecl、 C++ __fastcall 或 __stdcall 的函数之外的所有函数指定 __vectorcall 调用约定。 所有 __vectorcall 函数都必须具有原型。

### <a name="compile-as"></a>编译为

选择 .c 和 .cpp 文件的编译语言选项。 设置[/tc、/tp](tc-tp-tc-tp-specify-source-file-type.md)。

**方案**

- 默认 - 默认代码。
- 编译为 C 代码 - 编译为 C 代码。
- 编译为 C++ 代码 - 编译为 C++ 代码。

### <a name="disable-specific-warnings"></a>禁用特定警告

禁用所需的警告编号;将数字放入用分号分隔的列表中。 设置[/wd\<num >](compiler-option-warning-level.md)。

### <a name="forced-include-file"></a>强制包含文件

一个或多个强制包含文件。 [> 设置\</fi 名称](fi-name-forced-include-file.md)。

### <a name="forced-using-file"></a>强制 #using 文件

指定一个或多个强制的 #using 文件。 设置[/FU\<名称 >](fu-name-forced-hash-using-file.md)。

### <a name="show-includes"></a>显示包含文件

生成包含文件的列表及编译器输出。 设置[/showIncludes](showincludes-list-include-files.md)。

### <a name="use-full-paths"></a>使用完整路径

在诊断消息中使用完整路径。 设置[/FC](fc-full-path-of-source-code-file-in-diagnostics.md)。

### <a name="omit-default-library-name"></a>省略默认库名称

不要将默认的库名称包括在 .obj 文件中。 设置[/zl](zl-omit-default-library-name.md)。

### <a name="internal-compiler-error-reporting"></a>内部编译器错误报告

指定应如何将内部工具错误报告给 Microsoft。  IDE 中的默认值为 prompt。  命令行生成中的默认值是 queue。 设置 [/errorReport:\[method]] (errorReport-errors.md)。

**方案**

- 不**发送报告**-不会收集有关内部编译器错误的报告, 也不会将其发送给 Microsoft。
- **立即提示**-当您收到内部编译器错误时, 提示您发送报告。
- **排队等待下一次登录**-将错误报告排队。 使用管理员权限登录时, 将显示一个弹出窗口, 使您能够报告自上次登录后发生的任何故障 (系统不会提示您每三天发送一次失败的报告)。 当在命令行上编译应用程序时, queue 为默认值。
- **自动发送**-自动向 Microsoft 发送内部编译器错误报告。 若要启用此选项, 必须先同意 Microsoft% 27s 数据收集策略。 首次在计算机上指定/errorReport: send 时, 编译器消息将向你介绍包含 Microsoft% 27s 数据收集策略的网站。

### <a name="treat-specific-warnings-as-errors"></a>将特定的警告视为错误

将特定编译器警告视为错误, 其中 n 是编译器警告。

### <a name="additional-options"></a>附加选项

附加选项。
