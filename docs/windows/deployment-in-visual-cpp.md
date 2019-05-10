---
title: Visual C++ 中的部署
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
ms.openlocfilehash: 8dccf581cff88dc2e8c4a889bed8b47fc140eb7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345365"
---
# <a name="deployment-in-visual-c"></a>Visual C++ 中的部署

在开发计算机以外的计算机上安装应用程序称为部署。 将 Visual C++ 应用程序部署到另一台计算机时，必须安装该应用程序及其依赖的任何库文件。 Visual Studio 提供三种方法来部署 Visual C++ 库以及你的应用程序：集中部署、本地部署和静态链接。 集中部署将库文件放在 Windows 目录下，Windows 更新服务可在其中自动更新它们。 本地部署将库文件放在与应用程序相同的目录中。 要进行更新，用户必须亲自重新部署任何本地部署的库。 静态链接将库代码绑定到应用程序中。 使用静态链接时，必须重新编译和重新部署应用程序才能利用库的任何更新。

在 Visual Studio 2015 中，Microsoft C 运行时库被重构为特定于版本的本地库组件和一个新的通用 C 运行库，该库现在属于 Windows。 如需深入了解通用 CRT 的部署，请参阅[通用 CRT 部署](universal-crt-deployment.md)。

## <a name="central-deployment"></a>集中部署

在集中部署中，库 DLL 文件安装在 Windows\System32 目录中，对于 x64 系统上的 32 位库文件，则安装在 Windows\SysWow64 目录中。 Microsoft 会自动更新集中部署的库。 对于本地部署或静态链接的 Visual C++ 库，必须提供更新。

要集中部署 Visual C++ 库，可使用以下两个源中的一个源来安装文件：

- 可再发行组件包文件，这是独立的命令行可执行文件，包含压缩形式的所有 Visual C++ 可再发行库，或

- 可再发行合并模块（.msm 文件），可用于部署特定的库，并且将其包含在应用程序的 Windows Installer (.msi) 文件中。

可再发行组件包文件将安装特定系统体系结构的所有 Visual C++ 库。 例如，如果应用程序是为 x64 生成的，则可使用 vcredist_x64.exe 可再发行组件包安装应用程序使用的所有 Visual C++ 库。 安装应用程序之前，可编程应用程序安装程序以运行作为先决条件的可再发行组件包。

合并模块可将特定 Visual C++ 库的安装逻辑包含在 Windows Installer 应用程序的安装文件中。 可包含应用程序所要求的任意数量的合并模块。 如果需要最小化部署二进制文件的大小，请使用合并模块。

由于使用可再发行组件包或合并模块进行集中部署使 Windows 更新能自动更新 Visual C++ 库，因此建议在应用程序中使用库 DLL 而不是静态库，并使用集中部署而不使用本地部署。

## <a name="local-deployment"></a>本地部署

在本地部署中，库文件以及可执行文件安装在应用程序文件夹中。 不同版本的 Visual C++ 可再发行库可安装在同一文件夹中，因为每个版本的文件名都包含其版本号。 例如，C++ 运行时库的版本 12 是 msvcp120.dll，版本 14 是 msvcp140.dll。

库可以分布在多个附加 DLL 中，称为“点库”。 例如，Visual Studio 2017 版本 15.6 中发布的一些标准库功能已添加到 msvcp140_1.dll 中，以维护 msvcp140.dll 的 ABI 兼容性。 如果使用 Visual Studio 2017 版本 15.6（工具集 14.13）或 Visual Studio 2017 中更高版本的工具集，则可能需要本地部署这些点库以及主库。 然后，当 ABI 发生更改时，这些单独的点库将滚动到基本库的下一个主版本中。

由于 Microsoft 无法自动更新本地部署的 Visual C++ 库，因此不建议本地部署这些库。 如果你决定使用可再发行库的本地部署，建议你实现自己的自动更新本地部署库的方法。

## <a name="static-linking"></a>静态链接

除动态链接的库外，Visual Studio 还会将其大多数库作为静态库提供。 可将静态库静态链接到应用程序，即将库对象代码直接链接到应用程序中。 这将创建一个没有 DLL 依赖项的二进制文件，因此无需单独部署 Visual C++ 库文件。 但是，我们不建议采用这种方法，因为静态链接的库无法就地更新。 如果你使用静态链接并且希望更新链接的库，则必须重新编译和重新部署应用程序。

## <a name="troubleshooting-deployment-issues"></a>部署问题疑难解答

Visual C++ 库的加载顺序与系统相关。 若要诊断加载程序问题，请使用 depends.exe 或 where.exe。 有关详细信息，请参阅 [Dynamic-Link Library Search Order (Windows)](/windows/desktop/Dlls/dynamic-link-library-search-order)（动态链接库搜索顺序 (Windows)）。

## <a name="see-also"></a>请参阅

- [部署桌面应用程序](deploying-native-desktop-applications-visual-cpp.md)
- [通用 CRT 部署](universal-crt-deployment.md)
