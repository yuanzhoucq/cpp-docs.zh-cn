---
title: "混合（本机和托管）程序集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/clr 编译器选项 [C++], 混合程序集"
  - "程序集 [C++], 混合的"
  - "互操作 [C++], 混合程序集"
  - "互操作性 [C++], 混合程序集"
  - "托管代码 [C++], 互操作性"
  - "混合程序集 [C++]"
  - "混合程序集 [C++], 关于混合程序集"
  - "混合 DLL 加载 [C++]"
  - "本机代码 [C++], .NET 互操作性"
ms.assetid: 4299dfce-392f-4933-8bf0-5da2f0d1c282
caps.latest.revision: 35
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# 混合（本机和托管）程序集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

混合程序集能够同时包含非托管计算机指令和 MSIL 指令。  这使它们可以调用 .NET 组件或被其调用，同时保留与完全非托管组件的兼容性。  使用混合程序集，开发人员可以混合使用托管和非托管功能创作应用程序。  这使得混合程序集成为将现有 Visual C\+\+ 应用程序迁移到 .NET 平台的理想选择。  
  
 例如，通过使用 **\/clr** 编译器开关仅重新编译一个模块，就可将完全由非托管函数组成的现有应用程序迁移到 .NET 平台。  然后，此模块就可以使用 .NET 功能，但是仍保留与应用程序的其余部分的兼容性。  通过此种方式，应用程序可以按渐近、逐个部分的方式转换到 .NET 平台。  甚至可以决定在同一文件内每个函数的基础上进行托管或非托管编译（请参见 [managed、unmanaged](../preprocessor/managed-unmanaged.md)）。  
  
 Visual C\+\+ 支持生成三种不同类型的托管程序集：混合程序集、纯程序集和可验证程序集。  后两者在[纯代码和可验证代码](../dotnet/pure-and-verifiable-code-cpp-cli.md)中讨论。  
  
## 本节内容  
 [如何：迁移到 \/clr](../dotnet/how-to-migrate-to-clr.md)  
 描述在您的应用程序中引入或升级 .NET 功能的建议步骤。  
  
 [如何：使用 \/clr 编译 MFC 和 ATL 代码](../dotnet/how-to-compile-mfc-and-atl-code-by-using-clr.md)  
 讨论如何编译现有的 MFC 和 ATL 程序，以面向公共语言运行时。  
  
 [混合程序集的初始化](../dotnet/initialization-of-mixed-assemblies.md)  
 描述“加载程序锁”问题及其解决方案。  
  
 [混合程序集的库支持](../dotnet/library-support-for-mixed-assemblies.md)  
 讨论如何在 **\/clr** 编译中使用本机库。  
  
 [性能注意事项](../dotnet/performance-considerations-for-interop-cpp.md)  
 描述混合程序集和数据封送处理的性能含义。  
  
 [应用程序域和 Visual C\+\+](../dotnet/application-domains-and-visual-cpp.md)  
 讨论 Visual C\+\+ 对应用程序域的支持。  
  
 [双重形式转换](../dotnet/double-thunking-cpp.md)  
 讨论托管函数的本机入口点的性能含义。  
  
 [使用以 \/clr 生成的 COM 对象时避免 CLR 关闭异常](../dotnet/avoiding-exceptions-on-clr-shutdown-when-consuming-com-objects-built-with-clr.md)  
 讨论如何确保正确关闭使用用 **\/clr** 编译的 COM 对象的托管应用程序。  
  
 [如何：通过移除 CRT 库 DLL 上的依赖项来创建部分受信任的应用程序](../dotnet/create-a-partially-trusted-application.md)  
 讨论如何使用 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)]，通过移除 msvcm90.dll 中的依赖项，创建部分受信任的公共语言运行时应用程序。  
  
 了解混合程序集的代码准则有关的更多信息，请参见 MSDN 文档“托管\/非托管代码互操作性概述”。[http:\/\/msdn.microsoft.com\/netframework\/default.aspx?pull\=\/library\/dndotnet\/html\/manunmancode.asp](http://msdn.microsoft.com/netframework/default.aspx?pull=/library/dndotnet/html/manunmancode.asp)  
  
## 请参阅  
 [本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)