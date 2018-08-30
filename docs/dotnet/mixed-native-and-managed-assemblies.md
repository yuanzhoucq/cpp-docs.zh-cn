---
title: 混合 （本机和托管） 程序集 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], mixed assemblies
- /clr compiler option [C++], mixed assemblies
- managed code [C++], interoperability
- interoperability [C++], mixed assemblies
- mixed DLL loading [C++]
- mixed assemblies [C++], about mixed assemblies
- assemblies [C++], mixed
- mixed assemblies [C++]
- native code [C++], .NET interoperatibility
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2a48f34edec8a9f24f22d35be482d3b297215dbe
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210620"
---
# <a name="mixed-native-and-managed-assemblies"></a>混合 （本机和托管） 程序集

混合程序集都能包含非托管的机器指令和 MSIL 指令。 这使他们能够调用并且调用.NET 组件，同时保留与不完全受管理的组件的兼容性。 使用混合程序集，开发人员可以编写使用混合托管和非托管功能的应用程序。 这使得混合程序集的现有 Visual c + + 应用程序迁移到.NET 平台非常适合。

例如，完全由非托管函数组成的现有应用程序可将迁移到.NET 平台重新编译使用的只是一个模块 **/clr**编译器开关。 此模块然后可以使用.NET 功能，但保持兼容的应用程序的剩余部分。 这样一来，应用程序可以转换为.NET 平台中逐步逐块的方式。 甚至可以决定是在同一文件中函数的函数的基础上的托管和非托管编译 (请参阅[managed、 unmanaged](../preprocessor/managed-unmanaged.md))。

Visual c + + 使用仅支持混合的托管程序集的新一代 **/clr**编译器选项。 **/Clr: pure**并 **/clr: safe**编译器选项在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。 如果您需要纯或可验证的托管程序集，我们建议使用 C# 创建它们。

支持三种不同类型的托管程序集生成的早期版本的 Visual c + + 编译器工具集： 混合、 纯代码和可验证。 后一种两个中讨论[纯代码和可验证代码 (C + + CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)。

## <a name="in-this-section"></a>本节内容

[如何： 迁移到 /clr](../dotnet/how-to-migrate-to-clr.md)<br/>
介绍有关引入或升级应用程序中的.NET 功能的建议的步骤。

[如何： 编译 MFC 和 ATL 代码使用 /clr](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
讨论如何将现有的 MFC 和 ATL 程序，以面向公共语言运行时编译。

[混合程序集的初始化](../dotnet/initialization-of-mixed-assemblies.md)<br/>
描述了"加载程序锁"问题和解决方案。

[混合程序集的库支持](../dotnet/library-support-for-mixed-assemblies.md)<br/>
讨论如何使用本机库中的 **/clr**编译。

[性能注意事项](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
描述混合程序集和数据封送处理的性能影响。

[应用程序域和 Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
介绍对应用程序域的 Visual c + + 支持。

[双重形式转换](../dotnet/double-thunking-cpp.md)<br/>
讨论托管函数的本机入口点的性能影响。

[使用 /clr 避免 CLR 关闭时使用 COM 对象生成的异常](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
讨论如何确保正确关闭使用 COM 对象使用编译的托管应用程序 **/clr**。

[如何：通过移除 CRT 库 DLL 上的依赖项来创建部分受信任的应用程序](../dotnet/create-a-partially-trusted-application.md)<br/>
讨论如何创建通过删除依赖于 msvcm90.dll 使用 Visual c + + 的部分受信任的公共语言运行时应用程序。

对于混合程序集的编码指南的详细信息，请参阅 MSDN 文章[概述的托管/非托管代码互操作性](https://msdn.microsoft.com/library/ms973872.aspx)。

## <a name="see-also"></a>请参阅

- [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)
