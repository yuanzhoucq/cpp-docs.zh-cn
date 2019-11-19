---
title: Visual Studio 中的 C++
description: Visual C++ 是 Microsoft C++ 编译器、代码编辑器和 Visual Studio IDE 中相关工具的名称。 使用 Visual C++ 开发面向 Windows、Linux、Android 和 iOS 的程序。
ms.date: 07/02/2019
ms.technology: cpp-ide
helpviewer_keywords:
- Visual C++, home page
author: mikeblome
ms.author: mblome
ms.openlocfilehash: ea047aca90b03179c0a39cb653e0b9bc08306c64
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626215"
---
# <a name="c-in-visual-studio"></a>Visual Studio 中的 C++

> [!NOTE]
> 此开发人员文档适用于 Visual Studio 2015 及更高版本。 请使用页面左上角的版本选择器来匹配你的 Visual Studio 版本。
>
> 如果要查找 Visual C++ 可再发行包以便运行程序，请转到 [Microsoft 下载中心](https://www.microsoft.com/download/) ，并在搜索框中输入“Visual C++”  。

Microsoft Visual C++（通常缩写为 Visual C++ 或 MSVC）是 Windows Visual Studio 的一部分，指 C++、C 和汇编语言开发的工具和库。 这些工具和库可用于创建通用 Windows 平台 (UWP) 应用、本机 Windows 桌面和服务器应用程序、在 Windows、Linux、Android 和 iOS 上运行的跨平台库和应用以及使用 .NET Framework 的托管应用和库。 从 Windows 桌面的简单控制台应用到最复杂的应用，从移动设备的设备驱动程序和操作系统组件到跨平台游戏，再从 Azure 云中的最小 IoT 设备到多服务器的高性能计算等所有内容都可以使用 Visual C++ 编写。

可以并行安装 Visual Studio 2015、2017 和 2019。 可以结合使用 Visual Studio 2019（编译器工具集 v142）与 Visual Studio 2015 (v140) 和 Visual Studio 2017 (v141) 中的工具集来编辑和生成程序。

## <a name="whats-new-and-conformance-history"></a>新增功能和符合性历史记录

[Visual Studio 中的 C++ 新变化](what-s-new-for-visual-cpp-in-visual-studio.md)<br/>
了解 Visual Studio 中的新增功能。

[Visual Studio 2003 到 2015 中 C++ 新增功能](../porting/visual-cpp-what-s-new-2003-through-2015.md)<br/>
Visual Studio 2003 到 2015 每个版本中的 C++ 新增功能。

[Visual Studio 中的 C++ 符合性改进](cpp-conformance-improvements.md)<br/>
了解 Visual Studio 中 C++ 的符合性改进情况。

[Microsoft C++ 语言一致性表](visual-cpp-language-conformance.md)<br/>
MSVC C++ 编译器中按功能列出的符合性状态列表。

[Visual C++ 更改历史记录（2003 - 2015）](../porting/visual-cpp-change-history-2003-2015.md)<br/>
了解先前版本中的重大更改。

## <a name="install-visual-studio-and-upgrade-from-earlier-versions"></a>安装 Visual Studio 并从早期版本升级

[在 Visual Studio 中安装 C++ 支持](../build/vscpp-step-0-installation.md)<br/>
下载 Visual Studio 2017 或 Visual Studio 2019 并安装 Visual C++ 工具集。

[Visual C++ 移植和升级指南](../porting/visual-cpp-porting-and-upgrading-guide.md)<br/>
移植代码并将项目升级到 Visual Studio 2015 或更高版本的指南，以利用更高的编译器 C++ 标准符合性，以及大幅改进的编译时间和安全功能（例如 Spectre 缓解）。

[Visual Studio 版本中的 Visual C++ 工具和功能](visual-cpp-tools-and-features-in-visual-studio-editions.md)<br/>
查明不同的 Visual Studio 版本。

[支持的平台](supported-platforms-visual-cpp.md)<br/>
查明支持哪些平台。

## <a name="learn-c"></a>了解 C++

[欢迎回到 C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
基于可使你快速、安全地编写代码并避免 C 样式编程的多个缺陷的 C++11 及更高版本，了解有关现代 C++ 编程技术的详细信息。

[标准 C++](https://isocpp.org/)<br/>
了解 C++、获取现代 C++ 的概述，并查找各种书籍、文章、谈话和会议的链接

[学习 Visual C++](../build/vscpp-step-1-create.md)<br/>
开始学习 C++。

[Visual C++ 示例](visual-cpp-samples.md)<br/>
有关示例的信息。

## <a name="c-development-tools"></a>C++ 开发工具

[Visual Studio 中的 C++ 开发概述](overview-of-cpp-development.md)<br/>
如何使用 Visual Studio IDE 来创建项目、编辑代码、链接到库、编译、调试、创建单元测试、执行静态分析、部署等。

[项目和生成系统](../build/projects-and-build-systems-cpp.md)<br/>
如何使用 MSVC 编译器和链接器选项创建和配置 Visual Studio C ++ 项目、CMake 项目和其他类型的项目。

[编写和重构 C++ 代码](../ide/writing-and-refactoring-code-cpp.md)<br/>
如何使用 C++ 编辑器中的高效工作功能来重构、导航、理解和编写代码。

[调试本机代码](/visualstudio/debugger/debugging-native-code)<br/>
在 C++ 项目中使用 Visual Studio 调试器。

[C/C++ 代码分析概述](/visualstudio/code-quality/code-analysis-for-c-cpp-overview)<br/>
使用 SAL 注释或 C++ Core Guidelines 检查器执行静态分析。

[在 Visual Studio 中编写 C/C++ 单元测试](/visualstudio/test/writing-unit-tests-for-c-cpp)<br/>
使用面向 C++、Google Test、Boost.Test，或 CTest 的 Microsoft 单元测试框架创建单元测试。

## <a name="write-applications-in-c"></a>使用 C++ 编写应用程序

[通用 Windows 应用 (C++)](../cppcx/universal-windows-apps-cpp.md)<br/>
在 Windows 开发人员中心查找指南和参考内容。 有关开发 UWP 应用的信息，请参阅[通用 Windows 平台简介](/windows/uwp/get-started/universal-application-platform-guide)和[使用 C++ 创建第一个 UWP 应用](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)。

[桌面应用程序 (C++)](../windows/desktop-applications-visual-cpp.md)<br/>
了解如何创建适用于 Windows 的传统本机 C++ 桌面应用程序。

[使用 C++/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
了解如何创建 DLL，在本机 C++ 和以 C# 或 Visual Basic 等语言编写的 .NET 程序之间实现互操作性。

[Linux 编程](../linux/index.md)<br/>
使用 Visual Studio IDE 编写代码，并将其部署到远程 Linux 计算机上，以便使用 GCC 进行编译。

[在 Visual Studio 中创建 C/C++ DLL](../build/dlls-in-visual-cpp.md)<br/>
查明如何使用 Win32、ATL 和 MFC 创建 Windows 桌面 DLL，并提供有关如何编译和注册 DLL 的信息。

[并行编程](../parallel/parallel-programming-in-visual-cpp.md)<br/>
了解如何使用并行模式库、C++ AMP、OpenMP 以及与 Windows 多线程相关的其他功能。

[安全性最佳做法](../security/security-best-practices-for-cpp.md)<br/>
了解如何保护应用程序免受恶意代码威胁和未经授权的使用。

[云和 Web 编程](../cloud/cloud-and-web-programming-in-visual-cpp.md)<br/>
C++ 中有多种选项可使你连接到 Web 和云。

[数据访问](../data/data-access-in-cpp.md)<br/>
使用 ODBC 和 OLE DB 连接到数据库。

[文本和字符串](../text/text-and-strings-in-visual-cpp.md)<br/>
了解有关处理不同的文本和字符串格式以及针对本地和国际开发编码的信息。

## <a name="languages-reference"></a>语言参考

[C++ 语言参考](../cpp/cpp-language-reference.md)

[C/C++ 预处理器参考](../preprocessor/c-cpp-preprocessor-reference.md)

[C 语言参考](../c-language/c-language-reference.md)

[编译器内部函数和程序集语言](../intrinsics/compiler-intrinsics-and-assembly-language.md)

## <a name="c-libraries-in-visual-studio"></a>Visual Studio 中的 C++ 库

以下各节提供了有关 Visual Studio 中不同 C 和 C++ 库的信息。

[C 运行时库参考](../c-runtime-library/c-run-time-library-reference.md)<br/>
包括用安全性增强的函数来替代已知会引起安全问题的函数。

[C++ 标准库](../standard-library/cpp-standard-library-reference.md)<br/>
C++ 标准库。

[活动模板库 (ATL)](../atl/atl-com-desktop-components.md)<br/>
对 COM 组件和应用的支持。

[Microsoft 基础类 (MFC) 库](../mfc/mfc-desktop-applications.md)<br/>
对创建具有传统或 Office 样式用户界面的桌面应用的支持。

[并行模式库 (PPL)](../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
在 CPU 上执行的异步和并行算法。

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
在 GPU 上执行的大量并行算法。

[Windows 运行时模板库 (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)<br/>
通用 Windows 平台 (UWP) 应用和组件。

[使用 C++/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
公共语言运行时 (CLR) 编程。

## <a name="third-party-open-source-c-libraries"></a>第三方开源 C++ 库

跨平台 vcpkg  命令行工具，可以显著简化 900 多个 C++ 开源库的发现和安装操作。 请参阅 [vcpkg：用于 Windows 的 C++ 程序包管理器](../build/vcpkg.md)。

## <a name="feedback-and-community"></a>反馈和社区

[如何使用 Visual C++ 工具集报告问题](how-to-report-a-problem-with-the-visual-cpp-toolset.md)<br/>
了解如何针对 Visual C++ 工具集（编译器、链接器和其他工具）创建有效的错误报告，以及提交报告的方法。

Microsoft [C++ 团队博客](https://devblogs.microsoft.com/cppblog/)<br/>
从开发人员角度详细了解 Visual Studio 中 C++ 工具的新功能和最新信息。

[Visual Studio 开发者社区](https://developercommunity.visualstudio.com/)<br/>
查明如何获取帮助、报告 Bug，并提出 Visual Studio 建议。

## <a name="see-also"></a>请参阅

- [C 语言参考](../c-language/c-language-reference.md)
- [C 运行时库参考](../c-runtime-library/c-run-time-library-reference.md)
- [编译器内部函数和程序集语言](../intrinsics/compiler-intrinsics-and-assembly-language.md)
