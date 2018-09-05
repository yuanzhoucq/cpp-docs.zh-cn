---
title: 移植第三方库 | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- 3rd-party libraries
- vspkg
ms.assetid: b055ed20-8a9e-45b2-ac2a-e3d94271c009
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3e1edc9e4a6172b3ac55e7a8bc9b21cdc571774d
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/13/2018
ms.locfileid: "42578490"
---
# <a name="porting-third-party-libraries"></a>移植第三方库

将项目升级到当前版本的 Visual C++ 后，还必须升级项目使用的所有库，以便使用相同的编译器版本和风格构建库和项目。 有关详细信息，请参阅[潜在的升级问题概述](overview-of-potential-upgrade-issues-visual-cpp.md)。 

## <a name="introducing-vcpkg"></a>vcpkg 简介

在过去，查找和升级第三方库有时并非易事。 为了更容易获取和重建 C++ 第三方开源库，Visual C++ 团队创建了一个名为 **VC++ 包工具** 或 **vcpkg** 的命令行工具。 Vcpkg 有一个可搜索目录，包含许多热门 C++ 开源库。 你可以直接从 vcpkg 命令行安装目录中的任何库。 安装库时，Vcpkg 会在计算机上创建一个目录树，并在此文件夹中添加 .h、.lib 和二进制文件。 你可以在编译命令行中使用此文件夹，或者使用 vcpkg 集成安装命令将其集成到 Visual Studio 2015 或更高版本。 集成库位置后，Visual Studio 可以找到该位置，并将其添加到你创建的任何新项目中。 要使用库，只需使用 `#include` 将其包含在内即可，Visual Studio 会自动将 .lib 路径添加到项目设置并将 dll 复制到解决方案文件夹。 有关详细信息，请参阅 [vcpkg：用于 C++ 的程序包管理器 ](../vcpkg.md)。

## <a name="reporting-issues"></a>报告问题

如果你的库不在 vcpkg 目录中，则可在 [GitHub 存储库](https://github.com/Microsoft/vcpkg/issues)提出问题。社区人员和 Visual C++ 团队可在此处看到该问题，并可能创建适用于该库的端口文件。

对于专有的第三方库（非开源），我们建议与该库的提供商联系。 但是，我们想了解你正在使用的所有专有库，以便为你分组，请告知我们你依赖哪个库（可以通过 vcupgrade@microsoft.com 与我们联系）。
  
## <a name="see-also"></a>请参阅  

[Visual C++ 移植和升级指南](visual-cpp-porting-and-upgrading-guide.md)