---
title: 混合 （本机和托管） 程序集 |Microsoft 文档
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
ms.openlocfilehash: 469e0429408e1b8afed65889539202650cd28413
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704784"
---
# <a name="mixed-native-and-managed-assemblies"></a>混合 （本机和托管） 程序集

混合程序集是可以包含非托管的计算机的说明和 MSIL 指令。 这使他们可以调用和由.NET 组件，同时保留与不完全受管理的组件的兼容性。 使用混合程序集，开发人员可以编写使用混合的托管和非托管功能的应用程序。 这使得混合程序集现有 Visual c + + 应用程序迁移到.NET 平台的理想选择。

例如，完全由非托管函数组成的现有应用程序可将迁移到.NET 平台通过重新编译只是一个带有以下模块 **/clr**编译器开关。 此模块是然后可以使用.NET 功能，但保持兼容而应用程序的其余部分。 这种方式，可将应用程序转换中逐步执行、 逐块方式的.NET 平台。 甚至可以决定在同一文件内的函数的函数基础上的托管和非托管编译 (请参阅[managed、 unmanaged](../preprocessor/managed-unmanaged.md))。

Visual c + + 仅支持混合的托管程序集的生成使用 **/clr**编译器选项。 **/Clr: pure**和 **/clr: safe**编译器选项是在 Visual Studio 2015 中已过时，在 Visual Studio 2017 中不支持。 如果你需要纯或可验证的托管程序集，我们建议使用 C# 创建它们。

早期版本的 Visual c + + 编译器工具集支持的三种不同类型的托管程序集生成： 混合、 纯代码和可验证。 后者两个中讨论了[纯代码和可验证代码 (C + + /cli CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)。

## <a name="in-this-section"></a>本节内容

[如何： 迁移到 /clr](../dotnet/how-to-migrate-to-clr.md)<br/>
介绍引入或升级你的应用程序中的.NET 功能的建议的步骤。

[如何： /clr 编译 MFC 和 ATL 代码使用](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
讨论如何编译现有的 MFC 和 ATL 程序，以面向公共语言运行时。

[混合程序集的初始化](../dotnet/initialization-of-mixed-assemblies.md)<br/>
描述"加载程序锁"问题和解决方案。

[混合程序集的库支持](../dotnet/library-support-for-mixed-assemblies.md)<br/>
讨论如何使用中的本机库 **/clr**编译。

[性能注意事项](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
描述混合程序集和数据封送处理的性能影响。

[应用程序域和 Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
讨论 Visual c + + 应用程序域的支持。

[双重形式转换](../dotnet/double-thunking-cpp.md)<br/>
讨论托管函数的本机入口点的性能影响。

[使用 /clr 避免 CLR 关闭时使用 COM 对象生成的异常](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
讨论如何确保正确关闭的托管应用程序使用 COM 对象使用编译 **/clr**。

[如何：通过移除 CRT 库 DLL 上的依赖项来创建部分受信任的应用程序](../dotnet/create-a-partially-trusted-application.md)<br/>
讨论如何创建通过移除对 msvcm90.dll 依赖性使用 Visual c + + 的部分受信任公共语言运行时应用程序。

有关编码准则对于混合程序集的详细信息，请参阅 MSDN 文章[概述的托管/非托管代码互操作性](https://msdn.microsoft.com/en-us/library/ms973872.aspx)。

## <a name="see-also"></a>请参阅

- [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)
