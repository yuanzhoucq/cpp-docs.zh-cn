---
title: Visual Studio 2019 中 C++ 的新增功能
ms.date: 04/02/2019
ms.technology: cpp-ide
ms.assetid: 8801dbdb-ca0b-491f-9e33-01618bff5ae9
author: mikeblome
ms.author: mblome
ms.openlocfilehash: 493b96a8ce3359cc18287adbae8cbd6c374671ec
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779481"
---
<!--NOTE all https:// links to docs.microsoft.com need to be converted to site-relative links prior to publishing-->

# <a name="whats-new-for-c-in-visual-studio-2019"></a>Visual Studio 2019 中 C++ 的新增功能

Visual Studio 2019 向 Microsoft C++ 环境引入了许多更新和修补程序。 我们修复了编译器和工具方面的许多 bug 及所报告的问题，其中某些问题是客户通过“发送反馈”下的[报告问题](/visualstudio/how-to-report-a-problem-with-visual-studio-2017)和[提供建议](https://developercommunity.visualstudio.com/spaces/62/index.html)提交的。 感谢你报告 bug！ 有关整个 Visual Studio 中新增功能的详细信息，请访问 [Visual Studio 中的新增功能](/visualstudio/ide/whats-new-visual-studio-2019)。

## <a name="c-compiler"></a>C++ 编译器

- `/std:c++latest` 选项现在包含 C++20 功能（不一定完整），包括对用于三向比较的 C++20 运算符 <=>（“宇宙飞船”）的初始支持。

- [P0941R2 - 功能测试宏](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html)已完成，支持 `__has_cpp_attribute`。 所有标准模式都支持功能测试宏。

- [C++20 P1008R1 - 禁止使用用户声明的构造函数进行聚合](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf)也已完成。

- 增强了对 C++17 功能的支持，以及对 C++20 功能（如模块和协同程序）的实验性支持。 有关详细信息，请参阅 [Visual Studio 2019 中 C++ 的符合性改进](../cpp-conformance-improvements.md)。

- 现在已弃用 C++ 编译器交换机 `/Gm`。 如果已显式定义，请考虑在生成脚本中禁用 `/Gm` 交换机。 但也可以安全地忽略针对 `/Gm` 的弃用警告，因为在使用“将警告视为错误”(`/WX`) 时不会将其视为错误。

- 对于 C++ 控制台和桌面应用，默认情况下不再生成预编译头文件。

### <a name="codegen-security-diagnostics-and-versioning"></a>Codegen、安全性、诊断和版本控制

借助用于为 Spectre Variant 1 提供迁移缓解的 `/Qspectre` 改进分析 (CVE-2017-5753)。 有关详细信息，请参阅 [MSVC 中的 Spectre 缓解措施](https://devblogs.microsoft.com/cppblog/spectre-mitigations-in-msvc/)。

## <a name="c-standard-library-improvements"></a>C++ 标准库改进

- [C++20 P0550R2 \(remove_cvref)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf) 已完成。

- C++17 \<charconv> 浮点 to_chars() 已改进：最短的 chars_format::fixed 提速 60-80%，最短的/精确的 chars_format::hex 已完成。

- 更多算法具有并行实现：is_sorted()、 is_sorted_until()、is_partitioned()、set_difference()、set_intersection()、is_heap()、is_heap_until()。

- 对 `std::variant` 进行了改进，使其更易于优化，从而更好地生成代码。 借助 `std::visit`，现在可更好地进行代码内联。

- 我们已将 clang-format 应用于 C++ 标准库头文件以提高可读性。

- 提高了使用 `if constexpr` 编译多个标准库功能时的吞吐量。

- 优化了标准库物理设计，以避免编译不属于 #include'd 的标准库部分，将仅包含 \<vector> 的空文件的生成时间缩短一半。

## <a name="performancethroughput-fixes"></a>性能/吞吐量修复

- 改进生成吞吐量，包括 PDB 类型合并和创建过程中，链接器对文件 I/O 和链接时间的处理方式。

- 添加了对 OpenMP SIMD 矢量化的基本支持。 可以使用新的 CL 开关 `-openmp:experimental` 启用它。 此选项可能使带 `#pragma omp simd` 注释的循环被矢量化。 无法保证矢量化，已注释但未矢量化的循环将收到系统警告。 不支持 SIMD 子句，只需将其忽略并报告警告。

- 添加了一个新的内联命令行开关 `-Ob3`，它是 `-Ob2` 的更高版本。 `-O2`（优化二进制以提高速度）仍默认指代 `-Ob2`。 如果发现编译器内联不足，请考虑传递 `-O2 -Ob3`。

- 为了支持循环（包含对数学库函数的调用和整数除法等某些其他操作）的手动矢量化，添加了对短向量数学库 (SVML) 内部函数的支持。 这些函数计算 128 位、256 位或 512 位的向量等效项。 有关支持的函数的定义，请参阅 [Intel 内部函数指南](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#!=undefined&techs=SVML)。

- 新的和已改进的优化：

  - 可使用 SIMD 矢量内部函数简化表达式的常量合并和算法（针对浮点和整数形式）。

  - 提供更强大的分析功能，帮助从控制流（if/else/switch 语句）中提取信息以删除被证明为 true 或 false 的分支。

  - 改进了 memset 展开，以使用 SSE2 矢量指令。

  - 改进了无用 struct/class 副本（特别是针对按值传递的 C++ 程序）的删除操作。

  - 使用 `memmove`（例如 `std::copy` 或 `std::vector` 和 `std::string` 构造）优化代码的过程。

## <a name="c-ide"></a>C++ IDE

### <a name="live-share-c-support"></a>Live Share C++ 支持

[Live Share](/visualstudio/liveshare/) 现在支持 C++，使开发者可以使用 Visual Studio 或 Visual Studio Code 进行实时协作。 有关详细信息，请参阅 [Announcing Live Share for C++:Real-Time Sharing and Collaboration](https://devblogs.microsoft.com/cppblog/cppliveshare/)（宣布推出用于 C++ 的 Live Share：实时共享和协作）

### <a name="intellicode-for-c"></a>适用于 C++ 的 IntelliCode

IntelliCode 是一个可选扩展，它使用其广泛的培训和代码上下文，将用户最有可能使用的内容放在完成列表的顶部。 它通常可使用户无需向下滚动列表。 对于 C++，IntelliCode 可在使用标准库等热门库时提供最大帮助。 有关详细信息，请参阅 [AI-Assisted Code Completion Suggestions Come to C++ via IntelliCode](https://devblogs.microsoft.com/cppblog/cppintellicode/)（AI 辅助的代码完成建议通过 IntelliCode 提供给 C++）。

### <a name="template-intellisense"></a>模板 IntelliSense

“模板栏”现使用“速览窗口”用户界面而不是模式窗口，它支持嵌套模板，并且可以将任何默认参数预先填充到“速览窗口”中。 有关详细信息，请参阅 [Template IntelliSense Improvements for Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/template-intellisense-improvements-for-visual-studio-2019-preview-2/)（Visual Studio 2019 预览版 2 的模板 IntelliSense 改进）。 借助“模板栏”中的“最近使用”下拉列表，可以在以前的示例参数集之间快速切换。

### <a name="new-start-window-experience"></a>新启动窗口体验

启动 IDE 时，将显示一个新的“启动”窗口，可通过其中的选项打开最近使用的项目、从源代码管理克隆代码、将本地代码作为解决方案或文件夹打开，或者创建新项目。 “新项目”对话框也已彻底改造为一种搜索优先的可筛选体验。

### <a name="new-names-for-some-project-templates"></a>某些项目模板的新名称

我们修改了几个项目模板名称和描述以适应更新的“新建项目”对话框。

### <a name="various-productivity-improvements"></a>多种工作效率提升

Visual Studio 2019 包含以下功能，有助于使编码更简单、更直观：

- 快速修复：
  - 添加缺少的 #include
  - NULL 到 nullptr
  - 添加缺少的分号
  - 解析缺少的命名空间或范围
  - 替换错误的间接操作数（\* 替换为 ＆ 和 ＆ 替换为 \*）
- 通过悬停在右大括号上，获取块的快速信息
- 速览标题/代码文件
- 转到 #include 上的定义可打开文件

有关详细信息，请参阅 [C++ Productivity Improvements in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/c-productivity-improvements-in-visual-studio-2019-preview-2/)（Visual Studio 2019 预览版 2 中的 C++ 生产力改进）。

## <a name="cmake-support"></a>CMake 支持

- Visual Studio 现可打开由外部工具（如 CMakeGUI）、自定义元构建系统或自行调用 cmake.exe 的构生成脚本生成的现有 CMake 缓存。

- 改进了 IntelliSense 性能。

- 新的设置编辑器提供了手动编辑 CMakeSettings.json 文件的替代方案，并且可进行一些 CMakeGUI 奇偶校验。

- Visual Studio 可检测 Linux 计算机上是否具有兼容的 CMake 版本（如果没有兼容的版本，它会自行安装），从而帮助在 Linux 上使用 CMake 启动 C++ 开发。

- CMakeSettings 中不兼容的设置（例如不匹配的体系结构或不兼容的 CMake 生成器设置）在 JSON 编辑器中显示为波形曲线，并在错误列表中显示错误。

- 对于运行 `vcpkg integrate install` 后在 IDE 中打开的 CMake 项目，将自动为其检测并启用 vcpkg 工具链。 可通过在 CMakeSettings 中指定空工具链文件来关闭此行为。

- CMake 项目现默认启用“仅我的代码”调试。

- 静态分析警告现可在后台进行处理，并显示在 CMake 项目的编辑器中。

- 针对 CMake 项目更明晰的有关生成和配置的“开始”及“结束”消息，以及对 Visual Studio 生成进度用户界面的支持。 此外，“工具”>“选项”中现提供 CMake 详细级别设置，用于在输出窗口中自定义 CMake 生成和配置消息的详细级别。

- CMakeSettings.json 现支持 `cmakeToolchain` 设置，无需手动修改 CMake 命令行即可指定工具链。

- 新的“全部生成”菜单快捷方式 Ctrl+Shift+B。

## <a name="debugging"></a>调试

- 对于在 Windows 上运行的 C++ 应用程序，PDB 文件现可在单独的 64 位进程中加载。 此更改解决了在调试包含大量模块和 PDB 文件的应用程序时，由调试程序耗尽内存导致的一系列故障。

## <a name="windows-desktop-development-with-c"></a>使用 C++ 的 Windows 桌面开发

- 这些 C++ ATL/MFC 向导不再可用：

  - ATL COM+ 1.0 组件向导
  - ATL Active Server Pages 组件向导
  - ATL OLE DB 提供程序向导
  - ATL 属性页向导
  - ATL OLE DB 使用者向导
  - MFC ODBC 使用者
  - ActiveX 控件中的 MFC 类
  - Type Lib 中的 MFC 类。

  这些技术的示例代码存档在 Microsoft Docs 和 VCSamples GitHub 存储库中。

- Visual Studio 安装程序中不再提供 Windows 8.1 SDK。 建议将 C++ 项目升级到最新的 Windows 10 SDK。 如果在 8.1 上具有硬依赖项，则可以从 Windows SDK 存档下载它。

- Windows XP 目标将不再适用于最新的 C++ 工具集。 仍支持使用 VS 2017 级 MSVC 编译器和库的 XP 目标定向，并且可通过“单个组件”进行安装。

- 我们的文档不推荐使用 Merge 模块部署 Visual C++ 运行时。 此版本执行了额外步骤，将 MSM 标记为已弃用。 请考虑将 VCRuntime 核心部署从 MSM 迁移到可再发行组件包。

## <a name="mobile-development-with-c-android-and-ios"></a>使用 C++ 的移动开发（Android 和 iOS）

现在，C++ Android 体验默认为 Android SDK 25 和 Android NDK 16b。

## <a name="clangc2-platform-toolset"></a>Clang/C2 平台工具集

已删除 Clang/C2 实验性组件。 使用 MSVC 工具集，以完全符合 `/permissive-` 和 `/std:c++17` 的 C++ 标准，或者适用于 Windows 的 Clang/LLVM 工具链。

## <a name="code-analysis"></a>代码分析

- 代码分析现可自动在后台运行。 键入时，警告在编辑器中显示为绿色波形曲线。 有关详细信息，请参阅 [In-editor code analysis in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/in-editor-code-analysis-in-visual-studio-2019-preview-2/)（Visual Studio 2019 预览版 2 中的编辑器内代码分析）。

- 针对 \<mutex> 标头中已知的标准库类型的新实验性 ConcurrencyCheck 规则。 有关详细信息，请参阅 [Concurrency Code Analysis in Visual Studio 2019](https://devblogs.microsoft.com/cppblog/concurrency-code-analysis-in-visual-studio-2019/)（Visual Studio 2019 中的并发代码分析）。

- [生存期配置文件检查器](https://herbsutter.com/2018/09/20/lifetime-profile-v1-0-posted/)的部分更新的实现，可检测无关联指针和引用。 有关详细信息，请参阅 [Lifetime Profile Update in Visual Studio 2019 Preview 2](https://devblogs.microsoft.com/cppblog/lifetime-profile-update-in-visual-studio-2019-preview-2/)（Visual Studio 2019 预览版 2 中的生存期配置文件更新）。

- 更多与协同程序相关的检查，包括 C26138、C26810、C26811 和实验性规则 C26800。 有关详细信息，请参阅 [New Code Analysis Checks in Visual Studio 2019: use-after-move and coroutine](https://devblogs.microsoft.com/cppblog/new-code-analysis-checks-in-visual-studio-2019-use-after-move-and-coroutine/)（Visual Studio 2019 中的新代码分析检查：移动后使用和协同程序）。

## <a name="unit-testing"></a>单元测试

托管的 C++ 测试项目模板不再可用。 可在现有项目中继续使用托管的 C++ 测试框架。 对于新的单元测试，请考虑使用 Visual Studio 为其提供模板（MSTest、Google Test）或托管的 C# 测试项目模板的某个本机测试框架。
