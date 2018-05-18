---
title: 部署 Visual c + + |Microsoft 文档
ms.custom: ''
ms.date: 05/11/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b9dfdcdce618df3f2bfec64892f62aec20b6db9
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/17/2018
---
# <a name="deployment-in-visual-c"></a>Visual C++ 中的部署

开发计算机之外的计算机上的应用程序的安装被称为*部署*。 在部署到另一台计算机的 Visual c + + 应用程序时，你必须安装应用程序和它所依赖的任何库文件。 Visual Studio 提供三种方法来部署 Visual c + + 库以及你的应用程序：*集中部署*，*本地部署*，和*静态链接*。 集中部署放入其中 Windows 更新服务可以自动更新的 Windows 目录下的库文件。 本地部署将在你的应用程序所在的目录的库文件。 你必须重新部署任何本地部署的库自行更新它们。 静态链接将库代码绑定到你的应用程序。 你必须重新编译并重新部署应用程序以充分利用任何更新对库，当你使用静态链接。

在 Visual Studio 2015 中，Microsoft C 运行时库被重构为特定于版本的本地库组件和新的通用 C 运行时库，现在是 Windows。 有关通用 CRT 的部署的详细信息，请参阅[通用 CRT 部署](universal-crt-deployment.md)。

## <a name="central-deployment"></a>集中部署

在集中部署中，库 DLL 文件安装在 Windows\System32 目录中，或为 x64 上的 32 位库文件系统、 Windows\SysWow64 目录。 Microsoft 会自动更新集中部署的库。 对于本地部署或静态链接的 Visual c + + 库，你必须提供更新。

若要集中部署 Visual c + + 库，你可以使用这些文件的两个源之一安装：

- *可再发行组件包*文件是包含压缩的窗体中的所有 Visual c + + 可再发行库独立命令行的可执行文件，或

- *可再发行合并模块*（.msm 文件），它可用于部署特定的库，并将其包含在应用程序的 Windows Installer (.msi) 文件。

可再发行组件包文件将安装所有适用于特定的系统体系结构的 Visual c + + 库。 例如，如果你的应用程序生成为 x64 中，你可以使用 vcredist_x64.exe 可再发行组件包若要安装应用程序使用的所有 Visual c + + 库。 你可以编程应用程序安装程序，以在安装你的应用程序之前，运行可再发行组件包作为必备组件。

合并模块可包含的 Windows Installer 应用程序安装文件中的特定 Visual c + + 库的安装逻辑。 根据你的应用程序的需要，可以包括尽可能多或尽可能少的合并模块。 在需要以最小化大小部署二进制文件的位置时，请使用合并模块。

由于使用可再发行组件包或合并模块进行集中部署使 Windows 更新自动更新的 Visual c + + 库，我们建议你在你的应用程序而不是静态库中使用的库 Dll 并使用中心而不是本地的部署的部署。

## <a name="local-deployment"></a>本地部署

在本地部署中，库文件安装在你的应用程序文件夹，以及可执行文件。 因为每个版本的文件名称包含其版本号，可以在同一文件夹中安装不同版本的 Visual c + + 可再发行库。 例如，c + + 运行时库的 12 版本是 msvcp120.dll 和 14 是 msvcp140.dll 的版本。

库可以分布到多个其他 Dll，称为*点库*。 例如，在 Visual Studio 2017 版本 15.6 中发布的标准库中的某些功能已添加到 msvcp140_1.dll，到 preverve msvcp140.dll 的 ABI 兼容性。 如果你使用 Visual Studio 2017 版本 15.6 （工具集 14.13） 或从 Visual Studio 2017 更高版本的工具集，你可能需要本地部署这些点库，以及主库。 ABI 更改时，这些单独的点库均然后汇总到基础库，下一个主要版本。

由于 Microsoft 无法自动更新本地部署 Visual c + + 库，我们不建议本地部署的这些库。 如果你决定使用可再发行库的本地部署，建议你实现自己的自动更新本地部署库的方法。

## <a name="static-linking"></a>静态链接

除了动态链接库，Visual Studio 还提供其库的大多数作为静态库。 静态，你可以将静态库链接到你的应用程序，即，库对象代码直接链接到应用程序。 这将创建一个单一的二进制文件，而无需 DLL 依赖关系，以便无需单独部署 Visual c + + 库文件。 但是，我们不建议此方法因为静态链接库无法就地更新。 如果你使用静态链接并且希望更新链接的库，则必须重新编译和重新部署应用程序。

## <a name="troubleshooting-deployment-issues"></a>部署问题疑难解答

Visual c + + 库的加载顺序与系统相关。 若要诊断加载程序问题，请使用 depends.exe 或 where.exe。 有关详细信息，请参阅[动态链接库搜索顺序 (Windows)](http://msdn.microsoft.com/library/windows/desktop/ms682586.aspx)。

## <a name="see-also"></a>请参阅

- [部署桌面应用程序](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [通用 CRT 部署](universal-crt-deployment.md)
