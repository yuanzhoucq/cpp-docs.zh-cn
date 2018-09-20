---
title: 如何： 创建可验证 c + + 项目 (C + + CLI) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], creating
- conversions, C++ projects
- Visual C++ projects
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a84fcd660f8cc7ef5686fe0e03f9b520d1251bc4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408929"
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>如何： 创建可验证 c + + 项目 (C + + CLI)

Visual c + + 应用程序向导不会创建可验证的项目。

> [!IMPORTANT]
> 不推荐使用 visual Studio 2015 和 Visual Studio 2017 不支持 **/clr: pure**并 **/clr: safe**创建可验证项目。 如果需要可验证代码，我们建议将转换为 C# 代码。

但是，如果使用支持的 Visual c + + 编译器工具集的较旧版本 **/clr: pure**并 **/clr: safe**，项目可以转换为可验证。 本主题介绍如何设置项目属性和修改项目源文件来转换你的 Visual c + + 项目以生成可验证应用程序。

## <a name="compiler-and-linker-settings"></a>编译器和链接器设置

默认情况下，.NET 项目使用 /clr 编译器标志，并配置目标 x86 硬件到链接器。 对于可验证代码，你必须使用 /clr: safe 标志，并且必须指示链接器生成 MSIL，而不是本机指令。

### <a name="to-change-the-compiler-and-linker-settings"></a>若要更改的编译器和链接器设置

1. 显示项目属性页。 有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。

1. 上**常规**页**配置属性**节点中，设置**公共语言运行时支持**属性设置为**安全 MSIL 公共语言运行时支持 (/: safe)**。

1. 上**高级**页**链接器**节点中，设置**CLR 映像类型**属性设置为**强制安全 IL 映像 (/ /clrimagetype: safe)**。

## <a name="removing-native-data-types"></a>正在删除本机数据类型

由于即使实际上并不用于本机数据类型是不可验证，必须删除包含本机类型的所有标头文件。

> [!NOTE]
> 以下过程适用于 Windows 窗体应用程序 (.NET) 和控制台应用程序 (.NET) 项目。

### <a name="to-remove-references-to-native-data-types"></a>若要删除对本机数据类型的引用

1. 注释掉 Stdafx.h 文件中的所有内容。

## <a name="configuring-an-entry-point"></a>配置的入口点

可验证应用程序不能使用 C 运行时库 (CRT)，因为它们不能依赖于 CRT 来调用作为标准的入口点的主函数。 这意味着，你必须显式提供到链接器最初调用的函数的名称。 （在本例中为 main （） 使用而不是 main （） 或 _tmain() 以指示非 CRT 入口点，但必须显式指定的入口点，因为此名称可以是任意。）

> [!NOTE]
> 以下过程适用于控制台应用程序 (.NET) 项目。

#### <a name="to-configure-an-entry-point"></a>若要配置的入口点

1. 将 _tmain() 更改为项目的主.cpp 文件中的 main （）。

1. 显示项目属性页。 有关详细信息，请参阅[使用项目属性](../ide/working-with-project-properties.md)。

1. 上**高级**页**链接器**节点中，输入`Main`作为**入口点**属性值。

## <a name="see-also"></a>请参阅

- [纯代码和可验证代码 (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
