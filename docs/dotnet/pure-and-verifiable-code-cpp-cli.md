---
title: "纯代码和可验证代码 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".NET Framework [C++], 纯代码和可验证代码"
  - "/clr 编译器选项 [C++], 混合程序集"
  - "/clr 编译器选项 [C++], 纯程序集"
  - "/clr 编译器选项 [C++], 可验证程序集"
  - "程序集 [C++], 混合模式"
  - "程序集 [C++], 纯代码"
  - "程序集 [C++], 可验证代码"
  - "混合程序集 [C++]"
  - "混合程序集 [C++], 关于混合程序集"
  - "纯 MSIL [C++]"
  - "纯 MSIL [C++], 关于纯代码"
  - "可验证程序集 [C++]"
  - "可验证程序集 [C++], 关于可验证程序集"
  - "可验证类型安全代码 [C++]"
ms.assetid: 9050e110-fa11-4356-b56c-665187ff871c
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 纯代码和可验证代码 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对于 .NET 编程，Visual C\+\+ 支持创建三种不同类型的组件和应用程序：混合类型、纯类型和可验证类型。  三者都可通过 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md) 编译器选项来获得。  
  
## 备注  
 有关可验证程序集的更多信息，请参见：  
  
-   [混合、纯 MSIL 和可验证编译模式的功能比较](../dotnet/mixed-pure-and-verifiable-feature-comparison-cpp-cli.md)  
  
-   [如何：迁移到 \/clr:pure](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [如何：创建可验证的 C\+\+ 项目](../dotnet/how-to-create-verifiable-cpp-projects-cpp-cli.md)  
  
-   [如何：迁移到 \/clr:safe](../dotnet/how-to-migrate-to-clr-safe-cpp-cli.md)  
  
-   [结合使用 SQL Server 和可验证的程序集](../dotnet/using-verifiable-assemblies-with-sql-server-cpp-cli.md)  
  
-   [安全性最佳做法](../top/security-best-practices-for-cpp.md)  
  
-   [将项目从混合模式转换为纯中间语言项目](../dotnet/converting-projects-from-mixed-mode-to-pure-intermediate-language.md)  
  
## 混合代码 \(\/clr\)  
 混合程序集（用 **\/clr** 编译），既包含非托管部分又包含托管部分，这使得它们可以在使用 .NET 功能的同时仍包含非托管代码。  这允许将应用程序和组件更新为使用 .NET 功能而不要求重写整个项目。  以这种方式使用 Visual C\+\+ 来混合托管和非托管代码称为 C\+\+ Interop。  有关更多信息，请参见[混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)和[本机和 .NET 的互操作性](../dotnet/native-and-dotnet-interoperability.md)。  
  
## 纯代码 \(\/clr:pure\)  
 纯程序集（用 **\/clr:pure** 编译）既可包含本机数据类型也可包含托管数据类型，但只能包含托管函数。  与混合程序集一样，纯程序集允许通过 P\/Invoke 与本机 DLL 进行互操作（请参见[在 C\+\+ 中使用显式 PInvoke（DllImport 特性）](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)），但 C\+\+ Interop 功能不可用。  此外，由于纯程序集中的入口点使用 [\_\_clrcall](../cpp/clrcall.md) 调用约定，纯程序集无法导出可从本机函数调用的函数。  
  
### \/clr:pure 的优点  
  
-   更好的性能：由于纯程序集只包含 MSIL，没有本机函数，因此不需要托管\/非托管转换。（此规则的例外是通过 P\/Invoke 进行的函数调用。）  
  
-   AppDomain 感知度：托管函数和 CLR 数据类型存在于 `Application Domains` 内部，这影响它们的可见性和可访问性。  纯程序集是可识别域的（每个类型都暗含 \_\_declspec\([appdomain](../cpp/appdomain.md)\)），这样从其他 .NET 组件访问它们的类型和功能更轻松、更安全。  因此，与混合程序集相比，纯程序集与其他 .NET 组件的交互操作更容易。  
  
-   非磁盘加载：纯程序集可在内存中加载甚至进行流式处理。  这对使用 .NET 程序集作为存储过程来说是很重要的。  这与混合程序集的区别在于：由于混合程序集在 Windows 加载机制上的依赖项，混合程序集必须存在于磁盘上才能执行。  
  
-   反射：不能在混合可执行文件上进行反射，但纯程序集提供了完整的反射支持。  有关详细信息，请参阅[反射](../dotnet/reflection-cpp-cli.md)。  
  
-   承载可控性：因为纯程序集只包含 MSIL，当用于承载 CLR 并修改其默认行为的应用程序中时，与混合程序集相比，纯程序集的行为更加可预测、更加灵活。  
  
### clr:pure 的局限性  
 本节包含 **\/clr:pure** 当前不支持的功能。  
  
-   纯程序集无法由非托管函数调用。  因此，纯程序集无法实现 COM 接口或公开本机回调。  纯程序集无法通过 \_\_declspec\(dllexport\) 或 .DEF 文件导出函数。  此外，无法通过 \_\_declspec\(dllimport\) 导入用 \_\_clrcall 约定声明的函数。  本机模块中的函数可从纯程序集调用，但纯程序集无法公开本机可调用的函数，因此在纯程序集中公开功能必须通过混合程序集中的托管函数来完成。  有关更多信息，请参见[如何：迁移到 \/clr:pure](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)。  
  
-   在 Visual C\+\+ 中，纯模式编译不支持 ATL 和 MFC 库。  
  
-   纯粹的网络模块不能成为Visual C\+\+链接器的输入。  但是，链接器接受纯 .obj 文件，而 .obj 文件包含在 netmodule 中包含的信息的超集。  有关更多信息，请参见[用作链接器输入的 .netmodule 文件](../build/reference/netmodule-files-as-linker-input.md)。  
  
-   不支持编译器 COM 支持 \(\#import\)，因为这样会将非托管指令引入纯程序集中。  
  
-   对于纯程序集，用于对齐和异常处理的浮点选项是不可调整的。  因此，无法使用 \_\_declspec\(align\)。  这导致一些头文件（例如 fpieee.h）与 \/clr:pure 不兼容。  
  
-   当用 **\/clr:pure** 编译时，PSDK 中的 GetLastError 函数可能发生未定义的行为。  
  
## 可验证类型 \(\/clr:safe\)  
 **\/clr:safe** 编译器选项生成可验证程序集，它们类似于在 Visual Basic 和 C\# 中编写的那些程序集，符合允许公共语言运行时 \(CLR\) 保证代码不与当前安全设置冲突的要求。  例如，如果安全设置禁止某组件写入磁盘，则在执行任何代码之前，CLR 可以确定可验证组件是否满足此标准。  对于可验证程序集，没有 CRT 支持。（纯程序集可通过 C 运行库的纯 MSIL 版本获得 CRT 支持。）  
  
 与纯程序集和混合程序集相比，可验证程序集具有下列优点：  
  
-   提高的安全性。  
  
-   某些情况要求使用可验证程序集（例如 SQL 组件）。  
  
-   Windows 的将来版本日益要求组件和应用程序是可验证的。  
  
 一个缺点是 C\+\+ interop 功能不可用。  可验证程序集无法包含任何非托管函数或本机数据类型，即使它们不是由托管代码引用的。  
  
 尽管使用了词语“safe”，但用 **\/clr:safe** 编译应用程序并不表示不存在 bug；它只是表示 CLR 可在运行时验证安全设置。  
  
 无论程序集为什么类型，通过 P\/Invoke 从托管程序集到本机 DLL 的调用将进行编译，但根据具体安全设置，在运行时可能失败。  
  
> [!NOTE]
>  以下编码方案可以通过编译器，但会导致不可验证的程序集：使用范围解析运算符通过对象实例调用虚函数。例如：`MyObj -> A::VirtualFunction();`。  
  
## 请参阅  
 [使用 C\+\+\/CLI 进行 .NET 编程](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)