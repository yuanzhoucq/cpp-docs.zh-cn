---
title: 通用 CRT 部署 |Microsoft 文档
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
ms.openlocfilehash: 20006118d4bf27c379b78b84dc8807a4fd6c5e6c
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="universal-crt-deployment"></a>通用 CRT 部署

从 Visual Studio.NET 通过 Visual Studio 2013 中，c + + 编译器和工具的每个主版本具有包含新的独立版本的 Microsoft C 运行时 (CRT) 库。 这些独立版本的 CRT 是独立的从和程度各不相同，与相互不兼容。 例如，使用由 Visual Studio 2012 的 CRT 库版本 11，命名的 msvcr110.dll，且由 Visual Studio 2013 的 CRT 为版本 12，命名的 msvcr120.dll。 从 Visual Studio 2015 开始，这已经不成问题。 Visual Studio 2015 和更高版本的所有 Visual Studio 使用一个通用 CRT。

通用 CRT 是一个 Microsoft Windows 操作系统组件。 它是 Windows 10 中的操作系统的一部分包括，可对较旧操作系统，通过 Windows 8.1 的 Windows Vista 通过使用 Windows 更新。 此外，本地部署的通用 CRT 支持，但受到一些限制。

## <a name="central-deployment"></a>集中部署

集中安装通用 CRT 的首选的方法是使用 Microsoft Windows Update。 通用 CRT 是所有的推荐更新受 Microsoft Windows 操作系统，因此默认情况下，大多数计算机将其作为安装定期更新过程的一部分。 通用 CRT 的初始发行版[KB2999226](https://support.microsoft.com/en-us/kb/2999226); 具有各种 bug 修复的后续更新中进行[KB3118401](https://support.microsoft.com/en-us/kb/3118401)，且已进一步 bug 修补程序和新功能的其他更新。 有关更多更新，搜索[support.microsoft.com](https://support.microsoft.com)对于通用 C 运行库或通用 CRT。

并非所有的 Microsoft Windows 计算机定期通过使用 Windows 更新安装更新和一些可能无法安装所有推荐更新。 若要支持通过这些计算机上使用 Visual Studio 2015 和更高版本的 c + + 工具集生成的应用程序使用，有可用的通用的 CRT 可再发行文件脱机分发。 可能从上面的 KB 链接之一下载这些可再发行文件。 请注意，通用的 CRT 可再发行文件要求计算机具有已更新为新的 service pack。 因此，例如，对于 Windows 7 可再发行将仅安装 Windows 7 SP1、 Windows 7 RTM 不到。

Visual c + + 可再发行组件 (VCRedist) 由于通用 CRT 是基本的 c + + 库依赖项，在不具有已安装的不足以满足 c + + 库的版本的计算机上安装的通用 crt 的基础版本依赖关系。 如果你的应用程序依赖于通用 CRT 的较新版本，则必须显式安装该较新版本。 最好安装此客户端之前安装 VCRedist，以避免潜在的多个所需重新启动。

## <a name="local-deployment"></a>本地部署

本地部署的通用 CRT 支持，但不是建议出于性能和安全原因。  为本地部署 Dll 是 Windows SDK，在 Windows 工具包的一部分包括\\10\\Redist\\ucrt\\Dll 子目录，通过计算机体系结构。 Dll 所需包括是 ucrtbase.dll 和 APISet 转发器 Dll 名为 api 的一组-ms-win-\*.dll。 会有所变化的一套每个操作系统上所需的 Dll，因此强烈建议你在本地部署时包括所有 Dll。

有两个本地部署，需要注意的限制：

- 在 Windows 10 中，通用 CRT 中的系统目录将始终使用的即使应用程序包括通用 CRT 的应用程序本地副本。 即使通用 CRT 的本地副本是较新，也是如此。 这是因为通用 CRT 是 Windows 10 上的核心操作系统组件。

- 在 Windows 8 之前的 Windows 版本中，通用 CRT 不能打包本地与位于包含你的应用程序的主可执行文件的目录之外的目录中的插件。 不能在这种情况下成功解析是 ucrtbase.dll APISet 转发器 Dll。 一些建议的替代解决方案包括：

  - 静态链接通用的 CRT，
  - 集中部署通用的 CRT，或
  - 将通用 CRT 文件放在应用程序所在的目录。

## <a name="deployment-on-microsoft-windows-xp"></a>Microsoft Windows XP 上的部署

Visual Studio 2015 和 Visual Studio 2017 继续支持在 Microsoft Windows XP 上使用的软件的开发。 若要支持此功能，版本的通用 CRT 无法 Microsoft Windows XP 上工作。 Microsoft Windows XP 操作系统不再处于主流或扩展的支持，因此集中部署到 Microsoft Windows XP 的通用 crt 是不同于其他操作系统。

在 Windows XP 上安装时返回 Visual c + + 可再发行组件，它直接安装通用 CRT 和所有依赖项到系统目录中，而无需安装或具体取决于任何 Windows 更新。 可再发行合并模块，Microsoft_VC*版本*_CRT_\*.msm 文件，也是如此。

在 Windows XP 上的通用 crt 的本地部署是与在其他支持的操作系统上相同的。

## <a name="see-also"></a>请参阅

- [Visual C++ 中的部署](deployment-in-visual-cpp.md)
