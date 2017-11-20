---
title: "纯代码和可验证代码 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "31"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9ec68a6179cd74020638aa895028942bc76e21f5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="pure-and-verifiable-code-ccli"></a>纯代码和可验证代码 (C++/CLI)
对于.NET 编程，Visual c + + 支持三种不同类型的组件和应用程序创建： 混合、 纯代码和可验证。 这三个可通过[/clr （公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)编译器选项。  
  
## <a name="remarks"></a>备注  
 有关可验证程序集的详细信息，请参阅：  
  
-   [混合代码、纯代码和可验证代码的功能比较 (C++/CLI)](../dotnet/mixed-pure-and-verifiable-feature-comparison-cpp-cli.md)  
  
-   [如何： 迁移到 /clr: pure (C + + /cli CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [如何：创建可验证的 C++ 项目 (C++/CLI)](../dotnet/how-to-create-verifiable-cpp-projects-cpp-cli.md)  
  
-   [如何： 将迁移到 /clr: safe (C + + /cli CLI)](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)  
  
-   [结合使用 SQL Server 和可验证的程序集 (C++/CLI)](../dotnet/using-verifiable-assemblies-with-sql-server-cpp-cli.md)  
  
-   [安全性最佳做法](../security/security-best-practices-for-cpp.md)  
  
-   [将项目从混合模式转换为纯中间语言项目](../dotnet/converting-projects-from-mixed-mode-to-pure-intermediate-language.md)  
  
## <a name="mixed-clr"></a>混合 (/ clr)  
 混合程序集 (使用编译**/clr**)、 非托管同时包含和托管的部分，使它们使用.NET 功能，同时仍包含非托管的代码。 这允许应用程序和组件进行更新，而无需重写整个项目中使用.NET 功能。 使用 Visual c + + 混合托管代码和非托管代码以这种方式被调用 c + + 互操作。 有关详细信息，请参阅[混合 （本机和托管） 程序集](../dotnet/mixed-native-and-managed-assemblies.md)和[本机和.NET 互操作性](../dotnet/native-and-dotnet-interoperability.md)。  
  
## <a name="pure-clrpure"></a>纯 (/ clr： 纯)  
 纯程序集 (使用编译**/clr: pure**) 可以包含这两种本机和托管数据类型，但仅托管函数。 与混合程序集，一样纯程序集允许通过 P/Invoke 的本机 Dll 使用互操作 (请参阅[c + + （DllImport 特性） 中使用显式 PInvoke](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md))，但 c + + 互操作功能不可用。 此外，纯程序集不能导出函数，不能从本机函数中调用，因为纯程序集使用的入口点[__clrcall](../cpp/clrcall.md)调用约定。  
  
### <a name="advantages-of-clrpure"></a>利用 /clr: pure  
  
-   更好的性能： 纯程序集包含仅 MSIL，因为没有本机函数，并因此没有托管/非托管的转换是必要。 （通过 P/Invoke 进行的函数调用是此规则的例外。）  
  
-   AppDomain 感知： 托管的函数和 CLR 数据类型存在于内`Application Domains`，这将影响其可见性和可访问性。 纯程序集是域感知 (__declspec ([appdomain](../cpp/appdomain.md)) 都隐含具有每种类型) 以便访问它们的类型和功能的其他.NET 组件会更加容易、 更安全。 因此，纯程序集进行互操作更轻松地与混合程序集比其他.NET 组件。  
  
-   非磁盘加载： 可以加载纯程序集，内存中和甚至进行流式处理。 这是必需的.NET 程序集使用作为存储过程。 这不同于混合程序集，它们由于依赖于 Windows 加载机制，在磁盘上必须存在才能执行。  
  
-   反射： 不能以反映通过混合的可执行文件，而纯程序集提供完整的反射支持。 有关详细信息，请参阅[反射 (C + + /cli CLI)](../dotnet/reflection-cpp-cli.md)。  
  
-   主机可控性： 纯程序集包含仅 MSIL，因为它们的行为更可预测的方式和灵活比混合 CLR 的程序集时在应用程序中使用该主机并修改其默认行为。  
  
### <a name="limitations-of-clrpure"></a>限制 /clr: pure  
 本部分介绍当前不支持的功能**/clr: pure**。  
  
-   纯程序集不能由非托管函数调用。 因此纯程序集无法实现 COM 接口或公开本机的回调。 纯程序集不能导出通过 __declspec （dllexport） 的函数或。DEF 文件。 此外，函数声明与\__clrcall 约定无法通过导入\__declspec(dllimport)。 可以从一个纯程序集，调用本机模块中的函数，但纯程序集不能公开本机调用的函数，因此公开中纯程序集的功能必须通过在混合的程序集中的托管函数来完成。 请参阅[如何： 迁移到 /clr: pure (C + + /cli CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)有关详细信息。  
  
-   纯模式下编译 Visual c + + 中不支持 ATL 和 MFC 库。  
  
-   纯 .netmodule 不能作为 Visual C++ 链接器的输入被接受。 但是，链接器中，接受纯.obj 文件，并且.obj 文件包含模块中包含的信息的一个超集。 请参阅[用作链接器输入的.netmodule 文件](../build/reference/netmodule-files-as-linker-input.md)有关详细信息。  
  
-   编译器 COM 支持 (#import) 不支持，这将会带来纯程序集的程序集的非托管的说明。  
  
-   浮点数的对齐方式和异常处理的选项是不可调整为纯程序集。 因此，不能使用 __declspec(align)。 此呈现某些标头文件，如 fpieee.h 兼容使用 /clr: pure。  
  
-   在 PSDK GetLastError 函数在编译时可让未定义的行为**/clr: pure**。  
  
## <a name="verifiable-clrsafe"></a>可验证 (/: safe)  
 **/Clr: safe**编译器选项生成可验证程序集，如 Visual Basic 和 C# 中，允许公共语言运行时 (CLR) 若要确保代码不违反当前的要求与编写安全设置。 例如，如果安全设置禁止组件从写入到磁盘，CLR 可以确定可验证组件是否满足此条件在执行的任何代码之前。 这是可验证程序集没有 CRT 支持。 （CRT 支持可供 C 运行时库的纯 MSIL 版本通过纯程序集。）  
  
 可验证程序集相比，具有这些优点纯和混合程序集：  
  
-   增强的安全性。  
  
-   某些情况下需要它 （例如 SQL 组件）。  
  
-   组件和应用程序是可验证的越来越多地将需要 Windows 的未来版本。  
  
 一个缺点是 c + + 互操作性功能不可用。 可验证程序集不能包含任何非托管的函数或本机数据类型，即使它们未引用的托管代码。  
  
 尽管使用了"安全"一词，编译应用程序与**/clr: safe**并不意味着不有任何 bug; 它仅表示 CLR 可以在运行时验证的安全设置。  
  
 不管哪种程序集类型，从托管程序集进行到本机 Dll 通过 P/Invoke 的调用将编译，但在运行时，具体取决于安全设置可能会失败。  
  
> [!NOTE]
>  没有一个编码方案，将通过编译器，但这将导致无法验证的程序集： 调用通过使用范围解析运算符的对象实例的虚拟函数。  例如：`MyObj -> A::VirtualFunction();`。  
  
## <a name="see-also"></a>另请参阅  
 [使用 C++/CLI (Visual C++) 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)