---
title: "互操作的性能注意事项 (C++) | Microsoft Docs"
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
  - "/clr 编译器选项 [C++], 互操作性能注意事项"
  - "互操作 [C++], 性能注意事项"
  - "互操作性 [C++], 性能注意事项"
  - "混合程序集 [C++], 性能注意事项"
  - "平台调用 [C++], 互操作性"
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 互操作的性能注意事项 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题提供一些准则，用于减少运行时托管\/非托管 Interop 转换对性能的影响。  
  
 Visual C\+\+ 不仅支持与其他 .NET 语言（如 Visual Basic 和 C\#）相同的互操作性机制 \(P\/Invoke\)，而且还提供特定于 Visual C\+\+ 的 Interop 支持 \(C\+\+ Interop\)。  对于性能甚为关键的应用程序而言，重要的是要了解每种 Interop 技术的性能含义。  
  
 无论使用哪种 Interop 技术，托管函数每次调用非托管函数（反之亦然）时，都需要特殊的转换序列（称为形式转换）。  这些形式转换由 Visual C\+\+ 编译器自动插入，但是请务必谨记，就性能而言，这些转换的开销可能会很大。  
  
## 减少转换  
 避免或减少 Interop 形式转换成本的一种方法是重构尽可能减少托管\/非托管转换时所涉及的接口。  通过定向到常用接口可以大大提高性能，这些接口经常跨托管\/非托管边界进行调用。  例如，在紧凑循环中调用非托管函数的托管函数就是一个不错的重构候选对象。  如果循环本身被移动到非托管一侧，或者如果创建代替非托管调用的托管调用（或许将数据在托管一侧排队，然后在循环后立即将数据封送到非托管 API），则可以大大减少转换次数。  
  
## P\/Invoke 与 C\+\+ Interop  
 对于 .NET 语言（如 Visual Basic 和 C\#）而言，规定的用于与本机组件交互的方法为 P\/Invoke。  由于 P\/Invoke 受 .NET Framework 支持，因此 Visual C\+\+ 也对其提供支持，不过 Visual C\+\+ 还提供自己的互操作性支持，这称为 C\+\+ Interop。  C\+\+ Interop 优于 P\/Invoke，因为 P\/Invoke 不具有类型安全性。  这样，错误将主要在运行时报告，但是与 P\/Invoke 相比，C\+\+ Interop 的性能也相对更好。  
  
 托管函数每次调用非托管函数时，这两种技术都要求执行以下几项操作：  
  
-   将函数调用参数从 CLR 封送到本机类型。  
  
-   执行托管到非托管形式转换。  
  
-   调用非托管函数（使用参数的本机版本）。  
  
-   执行非托管到托管形式转换。  
  
-   将返回类型及任何“out”或“in,out”参数从本机类型封送到 CLR 类型。  
  
 托管\/非托管形式转换是 Interop 正常工作所必需的，但是所需的数据封送处理取决于涉及到的数据类型、函数签名以及使用数据的方式。  
  
 C\+\+ Interop 执行的数据封送处理可能是最简单的封送形式：仅采用按位方式跨托管\/非托管边界复制参数；而根本不执行任何转换。  对于 P\/Invoke，仅在所有参数都为简单的可直接复制到本机结构中的类型时才能这样做。  否则，如果参数被标记为“out”或“in,out”，则 P\/Invoke 将执行非常可靠的步骤，将每个托管参数转换为相应的本机类型，反之亦然。  
  
 换句话说，C\+\+ Interop 使用的可能是最快的数据封送处理方法，而 P\/Invoke 使用的则是最可靠的方法。  这意味着，默认情况下，C\+\+ Interop（采用 C\+\+ 典型的方式）提供最佳性能，而程序员负责解决此行为不安全或不适宜的情况。  
  
 因此，C\+\+ Interop 要求必须显式提供数据封送处理，但优点是，在考虑了给定数据性质的情况下，程序员可以自由决定哪种情况适宜以及如何使用数据封送处理。  此外，尽管可以在一定程度上通过自定义来修改 P\/Invoke 数据封送处理的行为，但是 C\+\+ Interop 允许在逐个调用的基础上自定义数据封送处理。  这对于 P\/Invoke 来说是不可能的。  
  
 有关 C\+\+ Interop 的更多信息，请参见[使用 C\+\+ 互操作（隐式 PInvoke）](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
## 请参阅  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)