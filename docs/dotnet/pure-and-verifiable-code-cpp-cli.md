---
title: 纯代码和可验证代码 (C + + /cli CLI) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- /clr compiler option [C++], verifiable assemblies
- /clr compiler option [C++], mixed assemblies
- pure MSIL [C++]
- verifiable assemblies [C++]
- verifiably type-safe code [C++]
- /clr compiler option [C++], pure assemblies
- .NET Framework [C++], pure and verifiable code
- assemblies [C++], mixed code
- verifiable assemblies [C++], about verifiable assemblies
- mixed assemblies [C++], about mixed assemblies
- pure MSIL [C++], about pure code
- assemblies [C++], verifiable code
- mixed assemblies [C++]
- assemblies [C++], pure code
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 453bb40e94c1d345adbe22f8792b59d1e584499a
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704823"
---
# <a name="pure-and-verifiable-code-ccli"></a>纯代码和可验证代码 (C + + /cli CLI)

对于.NET 编程，Visual c + + 在 Visual Studio 2017 支持创建混合程序集的使用[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)编译器选项。 **/Clr: pure**和 **: safe**选项是在 Visual Studio 2015 中已过时，在 Visual Studio 2017 中不支持。 如果你的代码必须是安全或可验证，我们建议你对 C# 移植它。

## <a name="mixed-clr"></a>混合 (/ clr)

混合程序集 (使用编译 **/clr**)、 非托管同时包含和托管的部分，使它们使用.NET 功能，同时仍包含本机代码。 这允许应用程序和组件进行更新，而无需重写整个项目中使用.NET 功能。 使用 Visual c + + 混合托管代码和本机代码以这种方式被调用 c + + 互操作。 有关详细信息，请参阅[混合 （本机和托管） 程序集](../dotnet/mixed-native-and-managed-assemblies.md)和[本机和.NET 互操作性](../dotnet/native-and-dotnet-interoperability.md)。

从托管程序集进行到本机 Dll 通过 P/Invoke 的调用将编译，但在运行时，具体取决于安全设置可能会失败。

没有一个编码方案，将通过编译器，但这将导致无法验证的程序集： 调用通过使用范围解析运算符的对象实例的虚拟函数。  例如：`MyObj -> A::VirtualFunction();`。

## <a name="see-also"></a>请参阅

- [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

