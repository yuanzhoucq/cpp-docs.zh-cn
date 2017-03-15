---
title: "如何：迁移到 /clr:pure (C++/CLI) | Microsoft Docs"
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
  - "/clr 编译器选项 [C++], 迁移到 /clr:pure"
  - "迁移 [C++], 纯 MSIL"
  - "纯 MSIL [C++], 迁移到"
ms.assetid: 5ffb1184-2095-4ade-84aa-4fa6324bc764
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：迁移到 /clr:pure (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题讨论使用 **\/clr:pure** 迁移到纯 MSIL 时可能出现的问题（有关更多信息，请参见 [\/clr（公共语言运行时编译）](../build/reference/clr-common-language-runtime-compilation.md)）。  本主题假定：当前使用 **\/clr** 选项将被迁移的代码编译为混合程序集，因为从非托管代码迁移到纯 MSIL 的路径不是直接路径。  对于非托管代码，应先参考 [如何：迁移到 \/clr](../dotnet/how-to-migrate-to-clr.md)，然后再尝试迁移到纯 MSIL。  
  
## 基本更改  
 纯 MSIL 由 MSIL 指令组成，因此，如果代码中含有无法用 MSIL 表示的函数，则相应代码将无法编译。  这些函数中包括定义为使用调用约定（[\_\_clrcall](../cpp/clrcall.md) 除外）的函数。（非 \_\_clrcall 函数可以在纯 MSIL 组件中调用，但未定义。）  
  
 若要确保不会出现运行时错误，应启用 C4412 警告。  可以通过以下方法启用 C4412：在使用 **\/clr:pure** 编译且在 IJW（**\/clr\)** 或本机代码）之间传递 C\+\+ 类型的每个模块中添加 `#pragma warning (default : 4412)`。  有关更多信息，请参见[编译器警告（等级 2）C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)。  
  
## 结构注意事项  
 [纯代码和可验证代码](../dotnet/pure-and-verifiable-code-cpp-cli.md) 中列出的一些纯 MSIL 程序集的限制对应用程序设计和迁移策略具有重要含义。  最值得注意的是，纯 MSIL 程序集与混合程序集不同，它与非托管模块不完全兼容。  
  
 纯 MSIL 程序集可以调用非托管函数，但不能由非托管函数调用。  因此，与非托管函数使用的服务器代码相比，纯 MSIL 更适合于使用非托管函数的客户端代码。  如果纯 MSIL 程序集中包含的功能将由非托管函数使用，则必须将混合程序集用作接口层。  
  
 使用 ATL 或 MFC 的应用程序并不适合迁移到纯 MSIL，因为此版本不支持这些库。  同样，[!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 包含未在 **\/clr:pure** 下编译的头文件。  
  
 尽管纯 MSIL 程序集可以调用非托管函数，但是此功能限于简单的 C 样式函数。  使用更为复杂的非托管 API 可能需要采用 COM 接口形式公开非托管功能，或者需要可作为纯 MSIL 与非托管组件之间接口的混合程序集。  如果非托管函数采用回调函数，则使用这些非托管函数的唯一方式就是使用混合程序集层。例如，如果纯程序集无法提供本机可调用函数作为回调函数使用。  
  
## 应用程序域和调用约定  
 虽然纯 MSIL 程序集可以使用非托管功能，但是，函数和静态数据的处理方式各不相同。  在纯程序集中，函数使用 [\_\_clrcall](../cpp/clrcall.md) 调用约定实现，而静态数据则按应用程序域进行存储。  这不同于非托管程序集和混合程序集的默认操作，这些程序集对函数使用 [\_\_cdecl](../cpp/cdecl.md) 调用约定，并且按进程存储静态数据。  
  
 在纯 MSIL（和使用 \/clr:safe 编译的可验证代码）的上下文中，这些默认设置是透明的，因为 [\_\_clrcall](../cpp/clrcall.md) 是 CLR 的默认调用约定，并且应用程序域是 .NET 应用程序中的静态和全局数据的本机范围。  但是，在与非托管组件或混合组件连接时，函数和全局数据的不同处理方式会引起问题。  
  
 例如，如果纯 MSIL 组件调用非托管 DLL 或混合 DLL 中的函数，则将使用 DLL 的头文件来编译纯程序集。  但是，如果没有显式指定头文件中每个函数的调用约定，则假定所有这些调用约定均为 [\_\_clrcall](../cpp/clrcall.md)。  这在以后会导致运行时失败，因为这些函数很可能是使用 [\_\_cdecl](../cpp/cdecl.md) 约定来实现的。  可以将非托管头文件中的函数显式标记为 [\_\_cdecl](../cpp/cdecl.md)，或者必须在 **\/clr:pure** 下重新编译整个 DLL 源代码。  
  
 同样，假定函数指针指向 **\/clr:pure** 编译下的 [\_\_clrcall](../cpp/clrcall.md) 函数。  也必须使用正确的调用约定对这些函数指针进行显式批注。  
  
 有关详细信息，请参阅[应用程序域和 Visual C\+\+](../dotnet/application-domains-and-visual-cpp.md)。  
  
## 链接限制  
 Visual C\+\+ 链接器不会尝试将混合 OBJ 文件和纯 OBJ 文件链接在一起，因为存储范围和调用约定不同。  
  
## 请参阅  
 [纯代码和可验证代码](../dotnet/pure-and-verifiable-code-cpp-cli.md)