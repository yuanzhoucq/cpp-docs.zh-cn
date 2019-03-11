---
title: 纯代码和可验证代码 (C++/CLI)
ms.date: 11/04/2016
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
ms.openlocfilehash: 66f3b5a33791d20297cde6e6223ba65189a99682
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743841"
---
# <a name="pure-and-verifiable-code-ccli"></a>纯代码和可验证代码 (C + + CLI)

对于.NET 编程，Visual Studio 2017 中 Visual c + + 支持创建混合程序集的使用[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)编译器选项。 **/Clr: pure**并 **: safe**选项是在 Visual Studio 2015 中弃用，在 Visual Studio 2017 中不受支持。 如果你的代码必须是安全或验证，则我们建议你移植到C#。

## <a name="mixed-clr"></a>混合 (/ clr)

混合程序集 (使用编译 **/clr**)、 包含非托管和托管的部分，使他们能够使用.NET 功能，但仍包含本机代码。 这允许应用程序和组件更新，而无需重新编写整个项目中使用.NET 功能。 使用 Visual c + + 混合使用这种方式中的托管和本机代码调用 c + + 互操作。 有关详细信息，请参阅[混合 （本机和托管） 程序集](../dotnet/mixed-native-and-managed-assemblies.md)并[本机和.NET 互操作性](../dotnet/native-and-dotnet-interoperability.md)。

到本机 Dll 通过 P/Invoke 从托管程序集进行的调用将进行编译，但在运行时根据安全设置可能会失败。

没有一个编码方案中，将通过编译器，但这将导致不可验证的程序集： 调用通过使用范围解析运算符为对象实例的虚拟函数。  例如：`MyObj -> A::VirtualFunction();`。

## <a name="see-also"></a>请参阅

- [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
