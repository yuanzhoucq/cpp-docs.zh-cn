---
title: 生成 C/c + + 程序 |Microsoft Docs
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
ms.openlocfilehash: 2792b49d7d3d3f107e39931ff62e6c4137c9c5ca
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723263"
---
# <a name="building-cc-programs"></a>生成 C/C++ 程序

你可以在 Visual Studio 中或命令行上生成 Visual C++ 项目。 使用 Visual Studio IDE [MSBuild](../build/msbuild-visual-cpp.md)以生成项目和解决方案。 可以在命令行使用 C/C++ 编译器 (cl.exe) 和链接器 (link.exe) 来生成简单项目。 若要在命令行上生成更复杂的项目，可以使用 MSBuild 或[NMAKE](../build/nmake-reference.md)。 有关如何使用 Visual Studio 生成项目和解决方案的概述，请参阅[编译和生成](/visualstudio/ide/compiling-and-building-in-visual-studio)。

## <a name="in-this-section"></a>本节内容

[生成 Visual Studio 中的 c + + 项目](../ide/building-cpp-projects-in-visual-studio.md)讨论如何使用 Visual Studio IDE 来生成 C/c + + 项目。

[在命令行上生成 C/c + + 代码](../build/building-on-the-command-line.md)讨论如何使用 C/c + + 命令行编译器和生成包含在 Visual Studio 的工具。

[生成 C/c + + 独立应用程序和通过并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)介绍了 Windows 桌面应用程序，其理论基础的独立应用程序和通过并行程序集的部署模型。

[C/c + + 生成参考](../build/reference/c-cpp-building-reference.md)提供指向有关 c + +、 编译器和链接器选项生成程序的参考文章和各种生成工具。

[配置 Visual c + + 64 位 x64 目标](../build/configuring-programs-for-64-bit-visual-cpp.md)介绍如何配置 Visual Studio 和命令行以使用 64 位工具集以及如何面向 64 位体系结构，并讨论了常见的迁移问题时的代码移到 64 位体系结构。

[为 ARM 处理器配置 Visual c + +](../build/configuring-programs-for-arm-processors-visual-cpp.md)描述由 ARM 处理器使用的约定，并讨论了常见的迁移问题，当代码移动到 ARM 体系结构时。

[配置适用于 Windows XP 的程序](../build/configuring-programs-for-windows-xp.md)介绍了如何将平台工具集设置为目标 Windows XP 开发。

## <a name="related-sections"></a>相关章节

[编译和生成](/visualstudio/ide/compiling-and-building-in-visual-studio)介绍 Visual Studio 生成系统和工具。