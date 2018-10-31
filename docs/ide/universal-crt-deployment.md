---
title: 通用 CRT 部署 | Microsoft Docs
ms.custom: ''
ms.date: 05/11/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b7fe21753dc4310752c1081d17ddff942bcbd89f
ms.sourcegitcommit: a738519aa491a493a8f213971354356c0e6a5f3a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/05/2018
ms.locfileid: "48820992"
---
# <a name="universal-crt-deployment"></a>通用 CRT 部署

从 Visual Studio .NET 到 Visual Studio 2013，C++ 编译器和工具的每个主版本都包含一个新的独立版本的 Microsoft C 运行 (CRT) 库。 CRT 的这些独立版本彼此独立，并在不同程度上彼此不兼容。 例如，Visual Studio 2012 使用的 CRT 库是第 11 版，名为 msvcr110.dll，而 Visual Studio 2013 使用的 CRT 是第 12 版，名为 msvcr120.dll。 从 Visual Studio 2015 开始，这种情况不会再出现。 Visual Studio 2015 及更高版本的 Visual Studio 都使用一个通用 CRT。

通用 CRT 是 Microsoft Windows 操作系统组件。 它作为操作系统的一部分包含在 Windows 10 中，并通过使用 Windows 更新可用于较旧的操作系统（Windows Vista 到 Windows 8.1）。 此外，支持通用 CRT 的本地部署，但有一些限制。

## <a name="central-deployment"></a>集中部署

集中安装通用 CRT 的首选方法是使用 Microsoft Windows 更新。 通用 CRT 是所有支持的 Microsoft Windows 操作系统的推荐更新，所以默认情况下，大多数计算机在常规更新过程中都会安装它。 通用 CRT 的初始版本为 [KB2999226](https://support.microsoft.com/kb/2999226)；后续更新包括 [KB3118401](https://support.microsoft.com/kb/3118401) 中进行的各种 Bug 修复，另外还有其他更新，其中包括更多 bug 修补程序和新功能。 有关最新更新，请搜索 [support.microsoft.com](https://support.microsoft.com) 以查找通用 C 运行时或通用 CRT。

并非所有 Microsoft Windows 计算机都使用 Windows 更新定期安装更新，有些计算机可能不会安装所有推荐的更新。 为支持在这些计算机上使用通过 Visual Studio 2015 及更高版本的 C++ 工具集生成的应用程序，通用 CRT 可再发行组件可用于脱机分发。 这些可再发行组件可从上述任一知识库链接下载。 请注意，通用 CRT 可再发行组件要求计算机已更新到当前服务包。 举个例子，Windows 7 的可再发行组件仅安装到 Windows 7 SP1 上，而不会安装到 Windows 7 RTM 上。

由于通用 CRT 是 C++ 库的基本依赖项，因此 Visual C++ 可再发行组件 (VCRedist) 会在未安装任何版本的计算机上安装通用 CRT 的基础版本，这足以满足 C++ 库依赖项。 如果应用程序依赖于最新版本的通用 CRT，则必须显式安装该最新版本。 最好在安装 VCRedist 之前安装它，以避免可能的多次重新启动。

## <a name="local-deployment"></a>本地部署

支持通用 CRT 的本地部署（但由于性能和安全原因不推荐）。  根据计算机体系结构，本地部署的 DLL 作为 Windows SDK 的一部分包含在 Windows Kits\\10\\Redist\\ucrt\\DLL 子目录中。 所需的 DLL 包括 ucrtbase.dll 和名为 api-ms-win-\*.dll 的一组 APISet forwarder DLL。 每个操作系统所需的 DLL 集都各不相同，因此强烈建议在本地进行部署时包括所有 DLL。

本地部署有两个需要注意的限制：

- 在 Windows 10 上，即使应用程序包含通用 CRT 的应用程序本地副本，也始终使用系统目录中的通用 CRT。 即使通用 CRT 的本地副本更新，也是如此。 这是因为通用 CRT 是 Windows 10 上的核心操作系统组件。

- 在 Windows 8 之前的 Windows 版本中，如果某个插件位于包含应用的主要可执行文件的目录以外的目录中，则通用 CRT 无法在本地使用该插件进行打包。 在这种情况下，APISet forwarder DLL 无法成功解析 ucrtbase.dll。 以下为建议的替代解决方案：

  - 静态链接通用 CRT，
  - 集中部署通用 CRT，或
  - 将通用 CRT 文件放在与应用相同的目录中。

## <a name="deployment-on-microsoft-windows-xp"></a>Microsoft Windows XP 上的部署

Visual Studio 2015 和 Visual Studio 2017 继续支持用于 Microsoft Windows XP 的软件开发。 为支持此功能，要求在 Microsoft Windows XP 上运行 Universal CRT 的某个版本。 Microsoft Windows XP 操作系统不再是主流或扩展的支持，因此在 Microsoft Windows XP 上集中部署通用 CRT 不同于其他操作系统。

在 Windows XP 上安装 Visual C++ 可再发行组件时，它会直接将通用 CRT 及其所有依赖项安装到系统目录中，而无需安装或依赖于任何 Windows 更新。 可再发行的合并模块（即 Microsoft_VC*version*_CRT_\*.msm 文件）执行相同操作。

Windows XP 上通用 CRT 的本地部署与其他支持的操作系统相同。

## <a name="see-also"></a>请参阅

- [Visual C++ 中的部署](deployment-in-visual-cpp.md)
