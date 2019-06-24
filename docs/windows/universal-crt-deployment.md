---
title: 通用 CRT 部署
ms.date: 05/11/2018
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
ms.openlocfilehash: 1f6e685cca65c4b31ac2e6147341c4b5a3fe8228
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344457"
---
# <a name="universal-crt-deployment"></a>通用 CRT 部署

从 Visual Studio .NET 到 Visual Studio 2013，C++ 编译器和工具的每个主版本都包含一个新的独立版本的 Microsoft C 运行 (CRT) 库。 CRT 的这些独立版本彼此独立，并在不同程度上彼此不兼容。 例如，Visual Studio 2012 使用的 CRT 库是第 11 版，名为 msvcr110.dll，而 Visual Studio 2013 使用的 CRT 是第 12 版，名为 msvcr120.dll。 从 Visual Studio 2015 开始，不再这种情况。 Visual Studio 2015 及更高版本的 Visual Studio 都使用一个通用 CRT。

通用 CRT 是作为在 Windows 10 操作系统的一部分包含的 Microsoft Windows 操作系统组件。 它是适用于较旧操作系统，通过 Windows 8.1 的 Windows Vista 通过 Windows 更新。 支持的通用 CRT 的本地部署，有一些限制。

## <a name="central-deployment"></a>集中部署

集中安装通用 CRT 的首选方法是使用 Microsoft Windows 更新。 通用 CRT 是所有支持的 Microsoft Windows 操作系统的推荐更新，所以默认情况下，大多数计算机在常规更新过程中都会安装它。 通用 CRT 的初始版本是[KB2999226](https://support.microsoft.com/kb/2999226)。 在进行了更高版本更新了各种 bug 修复[KB3118401](https://support.microsoft.com/kb/3118401)，并且发生了进一步的 bug 修复和新功能的其他更新。 有关最新更新，请搜索 [support.microsoft.com](https://support.microsoft.com) 以查找通用 C 运行时或通用 CRT。

并非所有 Microsoft Windows 计算机都使用 Windows 更新定期安装更新，有些计算机可能不会安装所有推荐的更新。 若要支持生成使用 Visual Studio 2015 及更高版本的应用程序使用C++工具集在这些计算机上有通用 CRT 可再发行文件可用于脱机通讯组。 可能从上面的 KB 链接之一下载这些可再发行文件。 通用 CRT 可再发行组件要求计算机具有已更新为新的 service pack。 举个例子，Windows 7 的可再发行组件仅安装到 Windows 7 SP1 上，而不会安装到 Windows 7 RTM 上。

因为通用 CRT 的基本依赖项C++库，视觉对象C++可再发行组件 (VCRedist) 还没有安装的计算机上安装的通用 CRT （版本 10.0.10240） 的初始版本。 此版本就足以满足C++库依赖项。 如果你的应用程序依赖于最新版本的通用 CRT，则必须使用 Windows 更新来使你完全保持最新的计算机或显式安装该版本。 最好是先安装通用 C 运行时通过 Windows 更新或 MSU，然后安装 VCRedist，以避免潜在的多个所需重新启动。

并非所有操作系统都有资格获得最新的通用 C 运行时通过 Windows Update。 Windows 10 上的集中部署的版本匹配的操作系统版本。 此外，若要更新通用 C 运行时必须更新操作系统。 对于通过 Windows 8.1 的 Windows Vista，最新可用通用 C 运行时当前基于 Windows 10 周年更新中，使用额外的修补程序 （版本号为 10.0.14393） 中包含的版本。

## <a name="local-deployment"></a>本地部署

支持通用 CRT 的本地部署（但由于性能和安全原因不推荐）。 根据计算机体系结构，本地部署的 DLL 作为 Windows SDK 的一部分包含在 Windows Kits\\10\\Redist\\ucrt\\DLL 子目录中。 所需的 DLL 包括 ucrtbase.dll 和名为 api-ms-win-\*.dll 的一组 APISet forwarder DLL。 每个操作系统所需的 Dll 集各不相同。 强烈建议在本地部署时包括所有 Dll。

本地部署有两个需要注意的限制：

- 在 Windows 10 上，即使应用程序包含通用 CRT 的应用程序本地副本，也始终使用系统目录中的通用 CRT。 即使本地副本是更高版本，因为通用 CRT 是 Windows 10 上的核心操作系统组件，它为 true。

- 上的 Windows 8 之前的 Windows 版本中，通用 CRT 无法打包本地使用插件，如果该文件位于主应用程序可执行文件的目录之外的目录。 在这种情况下，APISet forwarder DLL 无法成功解析 ucrtbase.dll。 以下为建议的替代解决方案：

  - 静态链接通用 CRT，
  - 集中部署通用 CRT，或
  - 将通用 CRT 文件放在与应用相同的目录中。

## <a name="deployment-on-microsoft-windows-xp"></a>Microsoft Windows XP 上的部署

Visual Studio 2015 和 Visual Studio 2017 继续支持用于 Microsoft Windows XP 的软件开发。 若要支持这一发展，在 Microsoft Windows XP 工作原理的通用 CRT 版本。 Microsoft Windows XP 操作系统不再是主流或扩展的支持，因此在 Microsoft Windows XP 上集中部署通用 CRT 不同于其他操作系统。

当视觉对象C++可再发行组件安装在 Windows XP 上，它直接将安装的通用 CRT 和所有依赖项到系统目录。 它不会安装或依赖于任何 Windows 更新。 可再发行的合并模块（即 Microsoft_VC*version*_CRT_\*.msm 文件）执行相同操作。

Windows XP 上通用 CRT 的本地部署与其他支持的操作系统相同。

## <a name="see-also"></a>请参阅

- [Visual C++ 中的部署](deployment-in-visual-cpp.md)
