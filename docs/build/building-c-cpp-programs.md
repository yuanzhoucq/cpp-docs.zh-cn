---
title: 生成 C/c + + 程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- vcbuilding
- buildingaprogramVC
dev_langs:
- C++
helpviewer_keywords:
- builds [C++]
- Visual C++ projects, building
- projects [C++], building
- builds [C++], options
- Visual C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2894c503dde89668bfb90b615c7b0966fe5fe2e5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360970"
---
# <a name="building-cc-programs"></a>生成 C/C++ 程序

你可以在 Visual Studio 中或命令行上生成 Visual C++ 项目。 Visual Studio IDE 使用[MSBuild](../build/msbuild-visual-cpp.md)以生成项目和解决方案。 可以在命令行使用 C/C++ 编译器 (cl.exe) 和链接器 (link.exe) 来生成简单项目。 若要在命令行上生成更复杂的项目，你可以使用 MSBuild 或[NMAKE](../build/nmake-reference.md)。 有关如何使用的概述[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]若要生成项目和解决方案，请参阅[编译和生成](/visualstudio/ide/compiling-and-building-in-visual-studio)。  
  
## <a name="in-this-section"></a>本节内容  

[在 Visual Studio 中生成 C++ 项目](../ide/building-cpp-projects-in-visual-studio.md)  
讨论如何使用 Visual Studio IDE 来生成 C/C++ 项目。  
  
[在命令行上生成 C/C++ 代码](../build/building-on-the-command-line.md)  
讨论如何使用 C/C++ 命令行编译器和 Visual Studio 中所包含的生成工具。  
  
[生成 C/C++ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
描述了适用于 Windows 桌面应用程序的部署模型，这一模型的理论基础是独立应用程序和并行程序集。  
  
[C/C++ 生成参考](../build/reference/c-cpp-building-reference.md)  
提供指向有关使用 C++ 生成程序、编译器和链接器选项以及各种生成工具的参考文章的链接。  
  
[针对 64 位 x64 目标配置 Visual C++](../build/configuring-programs-for-64-bit-visual-cpp.md)  
介绍如何将 Visual Studio 和命令行配置为使用 64 位工具集以及如何面向 64 位体系结构，还讨论了在将代码移到 64 位体系结构时常见的迁移问题。  
  
[为 ARM 处理器配置 Visual C++](../build/configuring-programs-for-arm-processors-visual-cpp.md)  
描述了 ARM 处理器使用的约定，并讨论了在代码移动到 ARM 架构时常见的迁移问题。  
  
[配置适用于 Windows XP 的程序](../build/configuring-programs-for-windows-xp.md)  
描述如何将平台工具集设置为面向 Windows XP 开发。  
  
## <a name="related-sections"></a>相关章节  
 [编译和生成](/visualstudio/ide/compiling-and-building-in-visual-studio)  
 介绍 Visual Studio 生成系统和工具。