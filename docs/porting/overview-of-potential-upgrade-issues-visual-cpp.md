---
title: 潜在的升级问题概述 (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2c99a8cb-098f-4a9d-bf2c-b80fd06ace43
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2411c5deb3a14ee3eaebb76fc69b6f36fa3bed42
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2018
ms.locfileid: "42578333"
---
# <a name="overview-of-potential-upgrade-issues-visual-c"></a>潜在的升级问题概述 (Visual C++)

多年来，Microsoft Visual C++ 编译器已历经多次更改，而 C++ 语言本身、C++ 标准库、C 运行时 (CRT) 以及其他库（如 MFC 和 ATL）亦然。 因此，在从 Visual Studio 的早期版本升级应用程序时，可能遇到编译器和链接器错误，以及先前已完全编译的代码中的警告。 原始基本代码越早，发生此类错误的可能性越大。 本概述总结了可能遇到的最常见类型的问题，并提供有关详细信息的链接。

> [!NOTE] 
> 在过去，我们建议要以增量方式执行跨多版本 Visual Studio 的升级，一次执行一个版本。 现在我们不再推荐这种方法。 我们发现，无论基本代码有多早，采用升级至最新版本 Visual Studio 的方法几乎总是更简单。

可将有关升级过程的问题或评论发送至 vcupgrade@microsoft.com。

## <a name="library-and-toolset-dependencies"></a>库和工具集依赖项

在将应用程序升级至 Visual Studio 的新版本时，强烈建议升级应用程序链接的所有库和 DLL，这在许多情况下是必要的。 这要求你拥有访问源代码的权限，或库供应商能提供使用相同的主版本编译器进行编译的新二进制文件。 若下列条件之一为 true，则可跳过此部分，此部分介绍有关二进制兼容性的详细信息。 如果不符合以下任一条件，则可能无法在已升级的应用程序中使用库。 此部分的信息将帮助你了解是否可以继续进行升级。

### <a name="toolset"></a>工具集

.obj 和 .lib 文件格式都定义完善且很少更改。 有时会对这些文件格式进行添加，但这些添加通常不会影响较新工具集使用由较旧工具集生成的对象文件和库的能力。 但如果使用 [/GL（全程序优化）](../build/reference/gl-whole-program-optimization.md)进行编译，则是一个大的例外。 如果使用 `/GL` 进行编译，则生成的对象文件只能使用生成它时所用的同一工具集进行链接。 因此，如果使用 `/GL` 和 Visual Studio 2017 (v141) 编译器生成对象文件，则必须使用 Visual Studio 2017 (v141) 链接器对其进行链接。 这是由于对象文件中的内部数据结构在各主版本的工具集之间不稳定，且较新的工具集无法识别较旧的数据格式。

C++ 不具备稳定的应用程序二进制接口 (ABI)。 Visual Studio 为版本的所有次要版本维护稳定的 C++ ABI。 例如，Visual Studio 2017 及其所有更新均兼容二进制文件。 但 ABI 不一定具有跨 Visual Studio 主版本的兼容性（2015 和 2017 除外，它们兼容二进制文件）。 也就是说，可以对 C++ 类型布局、名称修饰、异常处理和 C++ ABI 的其他部件进行重大更改。 因此，如果对象文件具有包含 C++ 链接的外部符号，则该对象文件可能无法与由其他主版本工具集生成的对象文件正确链接。 请注意：“可能无效”具有多种可能的结果：链接可能彻底失效（例如，如果名称修饰已更改）；链接可能成功，但在运行时可能无效（例如，如果类型布局已更改）；或在许多情况下，虽然可能出现一些状况，但一切运行正常。 另请注意，尽管 C++ ABI 不稳定，但 COM 所需的 C ABI 和 C++ ABI 的子集是稳定的。

如果链接到导入库，保留 ABI 兼容性的 Visual Studio 可再发行库的更高版本可在运行时使用。 例如，如果使用 Visual Studio 2015 Update 3 工具集编译和链接应用，可使用任何 Visual Studio 2017 可再发行库，因为 2015 和 2017 库具有保留的二进制后向兼容性。 反之则不然。不能将可再发行库用于低于之前生成代码所使用的工具集版本的版本，即使其具有可兼容 ABI，也是如此。

### <a name="libraries"></a>库

如果使用 Visual Studio C++ 库头文件的特定版本来编译源文件（通过 #including 标头），生成的对象文件必须与相同版本的库链接。 例如，如果使用 Visual Studio 2015 Update 3 \<immintrin.h> 编译源文件，则必须使用 Visual Studio 2015 Update 3 vcruntime 库进行链接。 同样地，如果使用 Visual Studio 2017 版本 15.5 \<iostream> 编译源文件，则必须使用 Visual Studio 2017 版本 15.5 标准 C++ 库 msvcprt 进行链接。 不支持混合与匹配。

对于 C++ 标准库，从 Visual Studio 2010 起，通过在标准标头中使用 `#pragma detect_mismatch` 显示禁止混合与匹配。 如果尝试链接不兼容的对象文件，或尝试与错误的标准库链接，链接将失败。

CRT 向来不支持混合与匹配，但通常还是能使用混合与匹配（至少在 Visual Studio 2015 和通用 CRT 之前，都是如此），这是因为 API 接口一直以来的变化不大。 通用 CRT 中断了后向兼容性，以便我们将来维护向后兼容性。 也就是说，将来我们不打算引入新的、已进行版本管理的通用 CRT 二进制文件。 现有的通用 CRT 已更新就绪。

为了提供与使用早期版本的 Microsoft C 运行时标头编译的对象文件（和库）的部分链接兼容性，我们提供库 legacy_stdio_definitions.lib，用于 Visual Studio 2015 及更高版本。 此库为大部分从通用 CRT 删除的函数和数据导出提供兼容性符号。 legacy_stdio_definitions.lib 提供的兼容性符号集足以满足大多数依赖项，包括 Windows SDK 所包含的库中的所有依赖项。 但是，对于某些从通用 CRT 删除的符号，则无法提供类似的兼容性符号。 这些符号包括一些函数（如 \_\_iob\_func）和数据导出（如 \_\_imp\_\_\_iob、\_\_imp\_\_\_pctype、\_\_imp\_\_\_mb\_cur\_max）。

如果静态库由较旧版本的 C 运行时标头生成，建议采取下列操作（按以下顺序）：

1. 使用 Visual Studio 2017 和通用 CRT 标头重新生成静态库，以支持与通用 CRT 的链接。 这是完全受支持的选项，也是最佳选项。

1. 如果无法（或不希望）重新生成静态库，可以尝试使用 legacy\_stdio\_definitions.lib 进行链接。 如果它满足静态库的链接时间依赖项，则需要彻底测试静态库在二进制文件中的使用情况，以确保[对通用 CRT 所做的行为更改](visual-cpp-change-history-2003-2015.md#BK_CRT)不会对其造成不利影响。

1. 如果 legacy\_stdio\_definitions.lib 不能满足静态库的依赖项，或库不适用于通用 CRT（由于上述行为更改），则建议将静态库封装到与 Microsoft C 运行时的正确版本链接的 DLL。 例如，如果使用 Visual Studio 2013 生成静态库，则也需要使用 Visual Studio 2013 和 Visual Studio 2013 C++ 库来生成此 DLL。 通过将库构建到 DLL 中，可封装实现的详细信息（此详细信息是在特定版本 Microsoft C 运行时上的它的依赖项）。 （注意：需要小心的是 DLL 接口不会泄露其使用的是哪种 C 运行时的详细信息，例如通过返回跨 DLL 边界的 FILE*，或通过返回 malloc 分配的指针并让调用方释放它。）

在单个进程中使用多个 CRT 本身不是问题（实际上，大多数进程最终将加载多个 CRT DLL；例如 Windows 操作系统组件依赖于 msvcrt.dll，而 CLR 也依赖于它自己的专用 CRT）。 当混杂不同 CRT 中的状态时，会出现问题。 例如，不应使用 msvcr110.dll!malloc 分配内存，也不应使用 msvcr120.dll!free 取消分配内存，不应尝试使用 msvcr110!fopen 打开文件，也不应尝试使用 msvcr120!fread 读取文件。 只要不混杂不同 CRT 中的状态，就能安全地在单个进程中加载多个 CRT。

有关详细信息，请参阅[将代码升级到通用 CRT](upgrade-your-code-to-the-universal-crt.md)。

## <a name="errors-due-to-project-settings"></a>项目设置导致的错误

要开始升级进程，仅需在最新版本的 Visual Studio 中打开旧的 project/solution/workspace。 Visual Studio 将基于旧的项目设置创建新项目。 如果旧项目具有库，或包含非标准位置的硬编码路径，则当项目使用默认设置时，这些路径中的文件有可能对编译器不可见。 有关详细信息，请参阅[链接器 OutputFile 设置](porting-guide-spy-increment.md#linker_output_settings)。

一般情况下，现在是恰当组织项目代码的绝佳时机，以便简化项目维护，并尽可能加快已升级代码编译。 如果已恰当组织源代码，且使用 Visual Studio 2010 或更高版本对旧项目进行编译，则可手动编辑新项目文件，以支持在旧编译器和新编译器上进行编译。 下面的示例演示了如何为 Visual Studio 2015 和 Visual Studio 2017 进行编译：

```xml
<PlatformToolset Condition="'$(VisualStudioVersion)'=='14.0'">v140</PlatformToolset>
<PlatformToolset Condition="'$(VisualStudioVersion)'=='15.0'">v141</PlatformToolset>
```

### <a name="lnk2019-unresolved-external"></a>LNK2019：无法解析的外部符号

对于无法解析的符号，可能需要修复项目设置。

- 如果源文件位于非默认位置，你是否将路径添加到了项目的包含目录？

- 如果在 .lib 文件中定义了外部符号，你是否在项目属性中指定了 lib 路径？正确版本的 .lib 文件是否位于此处？

- 是否尝试链接到由其他版本的 Visual Studio 编译的 .lib 文件？ 如果是，请参阅前面部分中关于库和工具集依赖项的内容。

- 调用站点处的参数类型是否匹配现有的函数重载？ 验证函数签名和调用函数的代码中的 typedef 的基础类型是否是你需要的类型。

若要解决无法解析的符号错误，可以尝试使用 dumpbin.exe 来检查二进制文件中定义的符号。 请尝试使用下面的命令行来查看在库中定义的符号：

```cmd
dumpbin.exe /LINKERMEMBER somelibrary.lib
```

### <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t（wchar_t 是本机类型）

（在 Microsoft Visual C++ 6.0 及早期版本中，wchar_t 未作为内置类型实现，而是在 wchar.h 中声明作为 unsigned short 的 typedef。）C++ 标准要求 wchar_t 为内置类型。 使用 typedef 版本可能导致可移植性问题。 如果你从 Visual Studio 的早期版本进行升级，并遇到编译器错误 C2664（理由是代码尝试将 wchar_t 隐式转换为 unsigned short），则建议更改代码来修正错误，而不是设置 `/Zc:wchar_t-`。 有关详细信息，请参阅 [/Zc:wchar_t（wchar_t 是本机类型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。

### <a name="upgrading-with-the-linker-options-nodefaultlib-entry-and-noentry"></a>使用链接器选项 /NODEFAULTLIB、/ENTRY 和 /NOENTRY 升级。

通过 `/NODEFAULTLIB` 链接器选项（或“忽略所有默认库”链接器属性），可使链接器不在 CRT 等默认库中自动链接。 这意味着，每个库必须作为输入单独列出。 “项目属性”对话框的“链接器”部分中的“附加依赖项”属性中，提供了此库列表。

在升级过程中，使用此选项的项目会出现问题，因为某些默认库的名称已更改。 由于每个库都需被列在“附加依赖项”属性或链接器命令行中，因此需要使用当前名称来更新库列表。

下表显示自 Studio 2015 开始名称已更改的库。 若要升级，需要将第一列中的名称替换为第二列中的名称。 其中有些库是导入库，但这应该没有什么影响。

|||
|-|-|
|如果你使用的是：|需要将其替换为：|
|libcmt.lib|libucrt.lib、libvcruntime.lib|
|libcmtd.lib|libucrtd.lib、libvcruntimed.lib|
|msvcrt.lib|ucrt.lib、vcruntime.lib|
|msvcrtd.lib|ucrtd.lib、vcruntimed.lib|

使用 `/ENTRY` 选项或 `/NOENTRY` 选项也会出现此问题，这两个选项也有绕过默认库的效果。

## <a name="errors-due-to-improved-language-conformance"></a>改进语言符合性带来的错误

多年来，Microsoft Visual C++ 编译器一直不断改进针对 C++ 标准的符合性。 在早期版本中编译的代码可能无法在 Visual Studio 2017 中编译，因为编译器会正确标记先前忽略或显式允许的错误。

例如，早期版本的 MSVC 引入了 `/Zc:forScope` 开关。 它允许不符合循环变量的行为。 现已弃用该开关，并可能在将来版本中将其删除。 强烈建议不要在升级代码时使用该开关。 有关详细信息，请参阅[已弃用 /Zc:forScope](porting-guide-spy-increment.md#deprecated_forscope)。

升级时一个常见的编译器错误是将非常数参数传递到常数参数。 旧版本的编译器并不总是将其标记为错误。 有关详细信息，请参阅[编译器的更严格转换](porting-guide-spy-increment.md#stricter_conversions)。

有关特定符合性改进的详细信息，请参阅 [Visual C++ 更改历史记录 2003 - 2015](visual-cpp-change-history-2003-2015.md) 以及 [Visual Studio 2017 中 C++ 的符合性改进](../cpp-conformance-improvements-2017.md)。

## <a name="errors-involving-stdinth-integral-types"></a>涉及 \<stdint.h> 整型类型的错误

\<stdint.h> 标头定义了 typedef 和宏，它们保证在所有平台上具有指定长度，这与内置整型类型不同。 一些示例包括 `uint32_t` 和 `int64_t`。 \<stdint.h> 标头已添加到 Visual Studio 2010 中。 编写于 2010 年之前的代码可能为这些类型提供了专用定义，这些定义可能无法总是与 \<stdint.h> 定义保持一致。

如果错误为 C2371 且涉及 `stdint` 类型，这可能意味着该类型是在代码或第三方 lib 文件中的标头中定义的。 升级时，应消除 \<stdint.h> 类型的任何自定义定义，但应先将自定义定义与当前标准定义进行对比，确保不会引入新问题。

可按 F12（转到定义）查看有所述类型的定义位置。

此处可使用 [/showIncludes](../build/reference/showincludes-list-include-files.md) 编译器选项。 在项目的“属性页”对话框中，打开“C/C++” > “高级”页，并将“显示包含文件”设置为“是”。 然后重新生成项目，并在输出窗口中查看 `#include` 列表。 每个标头在包含它的标头下都是缩进的。

## <a name="errors-involving-crt-functions"></a>涉及 CRT 函数的错误

多年来，针对 C 运行时进行了许多更改。 已添加函数的许多安全版本，也删除了函数的一些安全版本。 此外，如前文所述，Microsoft 的 CRT 实现在 Visual Studio 2015 中重构为新的二进制文件和相关的 .lib 文件。

如果错误涉及 CRT 函数，请搜索 [Visual C++ 更改历史记录（2003 - 2015）](visual-cpp-change-history-2003-2015.md)或 [Visual Studio 2017 中 C++ 的符合性改进](../cpp-conformance-improvements-2017.md)，查阅这些主题中是否包含附加信息。 如果错误为 LNK2019，无法解析的外部对象，请确保未删除函数。 否则，若确定函数仍存在，且调用代码正确，请检查项目是否使用了 `/NODEFAULTLIB`。 如果是这样，则需更新库列表，以便项目使用新通用 (UCRT) 库。 有关详细信息，请参阅有关库和依赖项的上述部分。

如果错误涉及 `printf` 或 `scanf`，请确保未在不包含 stdio.h 的情况下私下定义这两种函数中的任意一种。 如果定义了，请删除私有定义或删除到 legacy\_stdio\_definitions.lib 的链接。 可以在“附加依赖项”属性中的“配置属性” > “链接器” > “输入”下的“属性页”对话框中对此进行设置。 若要使用 Windows SDK 8.1 或更早的版本进行链接，请添加 legacy\_stdio\_definitions.lib。

如果错误涉及格式字符串参数，这可能是由于编译器在强制执行标准方面更严格。 有关详细信息，请参阅更改历史记录。 请密切注意此处的任何错误，因为它们可能表示存在安全风险。

## <a name="errors-due-to-changes-in-the-c-standard"></a>C++ 标准中的更改导致的错误

C++ 标准发展的方式并不总是后向兼容。 在 C++11 中引入移动语义、新关键字以及其他语言和标准库功能可能导致编译器错误和不同的运行时行为。

例如，旧 C++ 程序可能包含 iostream.h 标头。 此标头已在早期版本的 C++ 中弃用，且最终从 Visual Studio 中彻底删除。 在此情况下，需使用 \<iostream>，并重写代码。 有关详细信息，请参阅[更新旧的 iostreams 代码](porting-guide-spy-increment.md#updating_iostreams_code)。

### <a name="c4838-narrowing-conversion-warning"></a>C4838：收缩转换警告

目前根据 C++ 标准，将无符号整型值转换为带符号整型值视为收缩转换。 在 Visual Studio 2015 之前，编译器不会发出此警告。 应检查每个事件，以确保收缩不会影响代码的正确性。

## <a name="warnings-to-use-secure-crt-functions"></a>使用安全 CRT 函数的警告

多年来，已引入 C 运行时函数的多个安全版本。 尽管不安全的旧版本仍然可用，但建议更改代码以使用安全版本。 编译器将对使用不安全版本的行为发出警告。 可选择禁用或忽略这些警告。 要为解决方案中的所有项目禁用警告，请打开“视图” > “属性管理器”，选择要禁用警告的所有项目，然后右键单击所选项，并选择“属性”。 在“配置属性” > “C/C++” > “高级”下的“属性页”中，选择“禁用特定警告”。 单击下拉箭头，然后单击“编辑”。 在文本框中输入 4996。 （请勿包括“C”前缀。）有关详细信息，请参阅[移植以使用安全 CRT](porting-guide-spy-increment.md#porting_to_secure_crt)。

## <a name="errors-due-to-changes-in-windows-apis-or-obsolete-sdks"></a>对 Windows API 或已过时 SDK 进行的更改所导致的错误

多年来，已添加若干 Windows API 和数据类型，有时还会对其进行更改或删除。 此外，不属于核心操作系统的其他 SDK 也是添了又删。 因此，较旧的程序可能包含对已不存在的 API 的调用。 它们还可能包含对已不受支持的其它 Microsoft SDK 中 API 的调用。 如果错误涉及 Windows API 或较旧 Microsoft SDK 中的 API，则 API 可能已删除且/或已被更新、更安全的函数取代。

若要深入了解当前 API 设置以及特定 Windows API 支持的操作系统最低版本，请参阅 [Microsoft API 和参考目录](https://msdn.microsoft.com/library)，并导航至出现问题的 API。

### <a name="windows-version"></a>Windows 版本

在升级直接或间接使用 Windows API 的程序时，需要决定要支持的 Windows 最低版本。 在大多数情况下，Windows 7 是一个不错的选择。 有关详细信息，请参阅[头文件问题](porting-guide-spy-increment.md#header_file_problems)。 `WINVER` 宏定义了设计用于运行程序的 Windows 旧版本。 若 MFC 程序将 WINVER 设置为 0x0501 (Windows XP)，用户将收到警告，因为虽然编译器本身具有 XP 模式，但 MFC 已不再支持 XP。  

有关详细信息，请参阅[更新目标 Windows 版本](porting-guide-spy-increment.md#updating_winver)和[更多过时的头文件](porting-guide-spy-increment.md#outdated_header_files)。

## <a name="atl--mfc"></a>ATL / MFC

ATL 和 MFC 是相对稳定的 API，但偶尔对其进行更改。 有关详细信息，请参阅 [Visual C++ 更改历史记录 2003 - 2015](visual-cpp-change-history-2003-2015.md)、[Visual Studio 2017 中 Visual C++ 的新增功能](../what-s-new-for-visual-cpp-in-visual-studio.md)以及[Visual Studio 2017 中 C++ 的符合性改进](../cpp-conformance-improvements-2017.md)。

### <a name="lnk-2005-dllmain12-already-defined-in-msvcrtdlib"></a>已在 MSVCRTD.lib 中定义 LNK 2005 _DllMain@12

MFC 应用程序中可能发生此错误。 它指示 CRT 库和 MFC 库之间的顺序问题。 需要先链接 MFC，使其提供 new 和 delete 运算符。 要修复此错误，请使用 `/NODEFAULTLIB` 开关忽略 MSVCRTD.lib 和 mfcs140d.lib 这两个默认库。 然后将这些相同的 lib 添加为附加依赖项。

## <a name="32-vs-64-bit"></a>32 位和 64 位

如果原始代码针对 32 位系统编译，除了新建 32 位应用外，还可以选择创建 64 位版本。 一般情况下，应首先在 32 位模式下编译程序，然后再尝试使用 64 位模式。 针对 64 位进行编译是直截了当的方法，但在某些情况下，这可能暴露出 32 位版本中隐藏的一些 Bug。

此外，还应注意可能的编译时和运行时问题，这些问题与 printf 和 scanf 函数中的指针大小、时间和大小值以及格式说明符相关。 有关详细信息，请参阅[针对 64 位 x64 目标配置 Visual C++](../build/configuring-programs-for-64-bit-visual-cpp.md) 和 [Visual C++ 64 位迁移的常见问题](../build/common-visual-cpp-64-bit-migration-issues.md)。 有关迁移的其他提示，请参阅[适用于 64 位 Windows 的编程指南](/windows/desktop/WinProg64/programming-guide-for-64-bit-windows)。

## <a name="unicode-vs-mbcsascii"></a>Unicode 和 MBCS/ASCII

在标准化 Unicode 之前，许多程序使用多字节字符集 (MBCS) 来表示未包含在 ASCII 字符集中的字符。 在较早的 MFC 项目中，MBCS 是默认设置，在升级此类程序时，你将收到建议使用 Unicode 的警告。 如果你认为考虑到开发成本，不值得转换至 Unicode，则可以选择禁用或忽略此警告。 要为解决方案中的所有项目禁用警告，请打开“视图” > “属性管理器”，选择要禁用警告的所有项目，然后右键单击所选项，并选择“属性”。 在“属性页”对话框中，选择“配置属性” > “C/C++” > “高级”。 在“禁用特定警告”属性中展开下拉箭头，然后选择“编辑”。 在文本框中输入 4996。 （请勿包括“C”前缀。）选择“确定”保存该属性，然后选择“确定”保存所做更改。

有关详细信息，请参阅[从 MBCS 移植到 Unicode](porting-guide-spy-increment.md#porting_to_unicode)。 有关 MBCS 和 Unicode 的常规信息，请参阅 [Visual C++ 中的文本和字符串](../text/text-and-strings-in-visual-cpp.md)，以及[国际化](../c-runtime-library/internationalization.md)。

## <a name="see-also"></a>请参阅

[从 Visual C++ 早期版本升级项目](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[Visual Studio 2017 中 C++ 的符合性改进](../cpp-conformance-improvements-2017.md)  