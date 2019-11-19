---
title: 移植第三方库
ms.date: 10/29/2019
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
ms.openlocfilehash: 89460af1ad0b356f4f5952141636a9f067131750
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627190"
---
# <a name="porting-third-party-libraries"></a>移植第三方库

将项目从 Visual Studio 2013 或更早版本升级到 Visual C++的当前版本时，还必须升级项目所使用的所有库，以便使用相同的编译器版本和风格构建库和项目。 如果你无权访问库源代码，并且库未通过 vcpkg 提供，则必须从库供应商处获取更新的二进制文件。 有关详细信息，请参阅[潜在的升级问题概述](overview-of-potential-upgrade-issues-visual-cpp.md)。

在将应用程序从 Visual Studio 2015 或 Visual Studio 2017 升级到 Visual Studio 2019 时，无需升级依赖项，因为这三个版本生成的代码与二进制兼容。 有关详细信息，请参阅[ C++ visual studio 2015 和 visual studio 2019 之间的二进制兼容性](binary-compat-2015-2017.md)。

## <a name="vcpkg-for-open-source-libraries"></a>开源库的 vcpkg

在过去，查找和升级第三方库有时并非易事。 为了更轻松地获取和重新生成C++第三方开源库，视觉对象C++团队创建了一个名为 " **VC + + 打包工具**" 或 " **vcpkg**" 的命令行工具。 Vcpkg 有一个可搜索目录，包含许多热门 C++ 开源库。 你可以直接从 vcpkg 命令行安装目录中的任何库。 安装库时，Vcpkg 会在计算机上创建一个目录树，并在此文件夹中添加 .h、.lib 和二进制文件。 你可以在编译命令行中使用此文件夹，或者使用 vcpkg 集成安装命令将其集成到 Visual Studio 2015 或更高版本。 集成库位置后，Visual Studio 可以找到该位置，并将其添加到你创建的任何新项目中。 要使用库，只需使用 `#include` 将其包含在内即可，Visual Studio 会自动将 .lib 路径添加到项目设置并将 dll 复制到解决方案文件夹。 有关详细信息，请参阅 [vcpkg：用于 C++ 的程序包管理器 ](../build/vcpkg.md)。

## <a name="reporting-issues"></a>报告问题

如果你的开源库不在**vcpkg**目录中，你可以在[GitHub](https://github.com/Microsoft/vcpkg/issues)存储库中提出问题，社区和视觉对象C++团队可以在其中查看并可能为此库创建端口文件。

## <a name="see-also"></a>请参阅

[Visual C++ 移植和升级指南](visual-cpp-porting-and-upgrading-guide.md)
