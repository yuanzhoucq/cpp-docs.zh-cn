---
title: 混合（本机和托管）程序集
ms.date: 09/18/2018
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
ms.openlocfilehash: 11bdfc98c64b2612129e10c002c68ee243bec7da
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544506"
---
# <a name="mixed-native-and-managed-assemblies"></a>混合（本机和托管）程序集

混合程序集能够同时包含非托管计算机指令和 MSIL 指令。 这允许它们调用并由 .NET 组件调用，同时保持与本机C++库的兼容性。 使用混合程序集，开发人员可以使用 .NET 和本机C++代码的组合创作应用程序。

例如，通过使用 **/clr**编译器开关仅重新编译C++一个模块，可将完全由本机代码组成的现有库引入 .net 平台。 然后，此模块可以使用 .NET 功能，但仍与应用程序的其余部分兼容。 在同一文件中，甚至可以在每个函数的基础上确定托管和本机编译的情况（请参阅[托管的非托管](../preprocessor/managed-unmanaged.md)的）。

Visual C++仅支持通过使用 **/clr**编译器选项生成混合托管程序集。 **/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。 如果需要纯或可验证的托管程序集，我们建议使用C#来创建它们。

Microsoft C++编译器工具集的早期版本支持生成三个不同类型的托管程序集：混合、纯和可验证。 后两个[代码在纯代码和可验证代码C++（/cli）](../dotnet/pure-and-verifiable-code-cpp-cli.md)中讨论。

## <a name="in-this-section"></a>在本节中

[如何：迁移到/clr](../dotnet/how-to-migrate-to-clr.md)<br/>
介绍在应用程序中引入或升级 .NET 功能的建议步骤。

[如何：使用/clr 编译 MFC 和 ATL 代码](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)<br/>
讨论如何编译现有的 MFC 和 ATL 程序以面向公共语言运行时。

[混合程序集的初始化](../dotnet/initialization-of-mixed-assemblies.md)<br/>
介绍 "加载程序锁" 的问题和解决方案。

[混合程序集的库支持](../dotnet/library-support-for-mixed-assemblies.md)<br/>
讨论如何在 **/clr**编译中使用本机库。

[性能注意事项](../dotnet/performance-considerations-for-interop-cpp.md)<br/>
介绍混合程序集和数据封送处理的性能影响。

[应用程序域和 Visual C++](../dotnet/application-domains-and-visual-cpp.md)<br/>
讨论对C++应用程序域的可视化支持。

[双 Thunk](../dotnet/double-thunking-cpp.md)<br/>
讨论托管函数的本机入口点的性能影响。

[在使用通过/clr 生成的 COM 对象时避免 CLR 关闭异常](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)<br/>
讨论如何确保正确关闭使用使用 **/clr**编译的 COM 对象的托管应用程序。

[如何：通过移除 CRT 库 DLL 上的依赖项来创建部分受信任的应用程序](../dotnet/create-a-partially-trusted-application.md)<br/>
讨论如何通过删除对 msvcm90 的依赖关系，使用 Visual C++创建部分受信任的公共语言运行时应用程序。

有关混合程序集的编码准则的详细信息，请参阅 MSDN 文章[托管/非托管代码互操作性概述](/previous-versions/dotnet/articles/ms973872(v=msdn.10))。

## <a name="see-also"></a>另请参阅

- [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)
