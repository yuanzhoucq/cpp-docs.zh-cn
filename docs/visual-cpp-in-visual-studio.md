---
title: "Visual Studio 中的 Visual C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- visual c++
- visual c
- vc
dev_langs:
- C++
helpviewer_keywords:
- unmanaged code, C++
- development environment, Visual C++
- unmanaged code
- Visual C++
- Visual C++, reference
ms.assetid: e8dcc44c-a3e2-4ffe-887c-fd15b18dc458
caps.latest.revision: 61
author: mikeblome
ms.author: mblome
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
ms.translationtype: Human Translation
ms.sourcegitcommit: da3c2e6ce7247d3e8c9a401bc0a133cb8d46a970
ms.openlocfilehash: 81a7d724a4a3b2e5aa7de47461d20cc3385896eb
ms.contentlocale: zh-cn
ms.lasthandoff: 03/15/2017

---
# <a name="visual-c-in-visual-studio"></a>Visual Studio 中的 Visual C++
Visual Studio 2017 编程语言和开发工具有助于开发本机通用 Windows 应用、本机桌面和服务器应用程序、在 Android 和 iOS 以及 Windows 上运行的跨平台库、在 .NET Framework 上运行的托管应用。  
  
 **本文档的适用对象？**  
  
 此内容适用于正在编写程序的 C++ 开发人员。  
  
-   如果要查找 C++ 可再发行包和运行时组件以便能够运行程序，请转到 [Microsoft 下载中心](http://www.microsoft.com/en-us/download/) ，并在搜索框中输入“Visual C++”  。  
  
-   如果要查找 C++ 编程概念的简介，请转到众多提供此内容的网站之一，或获取 C++ 的创造者 Bjarne Stroustup 撰写的 [Programming -- Principles and Practice Using C++ (Second Edition)](http://stroustrup.com/Programming/) 《C++ 程序设计原理与实践》（第二版）的副本。 Visual C++ 内容假设你已基本熟悉 C++。  
  
-   如果要查找 Visual C++ 编译器，需从 [https://www.visualstudio.com/](https://www.visualstudio.com/) 下载 Visual Studio 的付费或免费版本。  

## <a name="general-information-about-visual-c"></a>有关 Visual C++ 的常规信息  
 [Visual C++ 的新增功能](what-s-new-for-visual-cpp-in-visual-studio.md)  
 查明 Visual C++ 中的新增功能。  

 [Visual Studio 2017 中 C++ 的符合性改进](cpp-conformance-improvements-2017.md) 
了解 Visual Studio 2017 中 C++ 的符合性改进。 

 [Visual C++ 语言一致性](visual-cpp-language-conformance.md)  
 Visual C ++ 中按功能列出的一致性状态列表。

 [Visual C++ 更改历史记录（2003 - 2015）](porting/visual-cpp-change-history-2003-2015.md)  
 了解先前版本中的重大更改。  
  
 [欢迎回到 C++](cpp/welcome-back-to-cpp-modern-cpp.md)  
 基于可使你快速、安全地编写代码并避免 C 样式编程的多个缺陷的 C++11 和 C++14，了解有关现代 C++ 编程技术的详细信息。  
  
 [如何使用 Visual C++ 工具集报告问题](how-to-report-a-problem-with-the-visual-cpp-toolset.md)  
 了解如何针对 Visual C++ 工具集（编译器、链接器和其他工具）创建有效的错误报告，以及提交报告的方法。  
  
 [Visual C++ 移植和升级指南](porting/visual-cpp-porting-and-upgrading-guide.md)  
 有关在 Visual Studio 2017 中移植代码并将项目升级到 Visual C++ 的指南，其中包括将 C++ 代码移植到 Windows 10 和通用 Windows 平台。  
  
 [Visual C++ 团队博客](http://blogs.msdn.com/b/vcblog/)  
 详细了解 [!INCLUDE[vcprvc](build/includes/vcprvc_md.md)] 开发人员发布的新功能和最新信息。  
  
 [Visual Studio 下载](http://go.microsoft.com/fwlink/?LinkId=235233)  
 下载 Visual C++。  
  
 [Visual Studio 版本中的 Visual C++ 工具和功能](ide/visual-cpp-tools-and-features-in-visual-studio-editions.md)  
 查明不同的 Visual Studio 版本。  
  
 [支持的平台](supported-platforms-visual-cpp.md)  
 查明支持哪些平台。  
  
 [Visual C++ 示例](visual-cpp-samples.md)  
 有关示例的信息。  
  
 [Visual Studio Community](http://go.microsoft.com/fwlink/?LinkId=235296)  
 查明如何获取帮助、报告 Bug，并提出 Visual Studio 建议。  
  
## <a name="writing-applications-in-c"></a>使用 C++ 编写应用程序  
 [通用 Windows 应用](windows/universal-windows-apps-cpp.md)  
 在 Windows 开发人员中心查找指南和参考内容。 有关开发 Windows 应用商店应用的信息，请参阅 [使用 Visual Studio 开发 Windows 应用商店应用](http://go.microsoft.com/fwlink/p/?LinkId=248364) 和 [使用 C++ 的 Windows 应用商店应用指南](http://go.microsoft.com/fwlink/p/?LinkId=244654)。  
  
 [桌面应用程序 (Visual C++)](windows/desktop-applications-visual-cpp.md)  
 了解如何创建具有消息循环和回调的桌面应用程序。  
  
 [Visual C++ 中的 DLL](build/dlls-in-visual-cpp.md)  
 查明如何使用 Win32、ATL 和 MFC 创建 Windows 桌面 DLL，并提供有关如何编译和注册 DLL 的信息。  
  
 [并行编程](parallel/parallel-programming-in-visual-cpp.md)  
 了解如何使用并行模式库、C++ AMP、OpenMP 以及与 Windows 多线程相关的其他功能。  
  
 [安全性最佳做法](security/security-best-practices-for-cpp.md)  
 了解如何保护应用程序免受恶意代码威胁和未经授权的使用。  
  
 [云和 Web 编程](cloud/cloud-and-web-programming-in-visual-cpp.md)  
 C++ 中有多种选项可使你连接到 Web 和云。  
  
 [数据访问](http://msdn.microsoft.com/Library/a9455752-39c4-4457-b14e-197772d3df0b)  
 使用 ODBC 和其他数据库访问技术连接到数据库。  
  
 [文本和字符串](text/text-and-strings-in-visual-cpp.md)  
 了解有关处理不同的文本和字符串格式以及针对本地和国际开发编码的信息。  
  
## <a name="c-development-tools"></a>C++ 开发工具  
 要了解有关如何创建项目、使用源代码文件、链接到库、编译、调试、分析、部署等的信息，请参阅 [IDE 和开发工具](ide/ide-and-tools-for-visual-cpp-development.md)。  
  
## <a name="c-language-reference"></a>C++ 语言参考  
 有关 C++ 语言的信息，请参阅 [C++ 语言参考](cpp/cpp-language-reference.md)。  
  
 有关 C++ 预处理器的信息，请参阅 [C/C++ 预处理器参考](preprocessor/c-cpp-preprocessor-reference.md)。  
  
## <a name="c-libraries-in-visual-studio"></a>Visual Studio 中的 C++ 库  
 以下各节提供了有关 Visual C++ 中不同 C++ 库的信息。  
  
 [C 运行时库参考](c-runtime-library/c-run-time-library-reference.md)  
 包括用安全性增强的函数来替代已知会引起安全问题的函数。  
  
 [C++ 标准库](standard-library/cpp-standard-library-reference.md)  
 C++ 标准库。  
  
 [活动模板库 (ATL)](atl/atl-com-desktop-components.md)  
 对 COM 组件和应用的支持。  
  
 [Microsoft 基础类 (MFC) 库](mfc/mfc-desktop-applications.md)  
 对创建具有传统或 Office 样式用户界面的桌面应用的支持。  
  
 [并行模式库 (PPL)](parallel/concrt/parallel-patterns-library-ppl.md)  
 在 CPU 上执行的异步和并行算法。  
  
 [C++ AMP (C++ Accelerated Massive Parallelism)](parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)  
 在 GPU 上执行的大量并行算法。  
  
 [Windows 运行时模板库 (WRL)](http://msdn.microsoft.com/library/windows/apps/hh438466.aspx)  
 [!INCLUDE[win8_appname_long](build/includes/win8_appname_long_md.md)] 应用和组件。  
  
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)  
 公共语言运行时 (CLR) 编程。  
  
 另请参阅 [STL/CLR](dotnet/stl-clr-library-reference.md) 和 [C++ 支持库](dotnet/cpp-support-library.md)文档。  
  
## <a name="other-c-libraries"></a>其他 Visual C++ 库  
 本节中包含指向未包括在 Visual Studio 中的库的链接，但可以下载该库并将其用于 Visual C++。  
  
 [Boost](http://www.boost.org/)  
 一种广泛使用的常用库。  
  
 [C++ REST SDK](http://casablanca.codeplex.com)。  
 用于通过 HTTP 与 Web 服务进行通信的 Microsoft 库。  
  
## <a name="more-resources"></a>更多资源  
 [Visual C++ 资源](http://msdn.microsoft.com/vstudio/hh386302.aspx)  
 更多 Visual C++ 资源。  
  
 [标准 C++](http://isocpp.org/)  
 了解 C++、获取现代 C++ 的概述，并查找各种书籍、文章、谈话和会议的链接  
  
 [学习 Visual C++](http://msdn.microsoft.com/vstudio/hh386302.aspx)  
 开始学习 C++。  
  
## <a name="see-also"></a>另请参阅  
 [C 语言参考](c-language/c-language-reference.md)   
 [C 运行时库参考](c-runtime-library/c-run-time-library-reference.md)   
 [编译器内部函数和程序集语言](intrinsics/compiler-intrinsics-and-assembly-language.md)

