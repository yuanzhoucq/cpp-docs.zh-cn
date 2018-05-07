---
title: 互操作 （c + +） 的性能注意事项 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- /clr compiler option [C++], interop performance considerations
- platform invoke [C++], interoperability
- interop [C++], performance consideraitons
- mixed assemblies [C++], performance considerations
- interoperability [C++], performance considerations
ms.assetid: bb9a282e-c3f8-40eb-a2fa-45d80d578932
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9223c52e4ef831a9a1ff657db1a0d7859dd6ce6c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="performance-considerations-for-interop-c"></a>互操作的性能注意事项 (C++)
本主题提供减少托管/非托管互操作转换对运行时性能的影响的指南。  
  
 Visual c + + 支持 Visual Basic 和 C# (P/Invoke) 等其他.NET 语言为相同的互操作性机制，但它还提供特定于 Visual c + + （c + + 互操作） 的互操作支持。 对于性能关键的应用程序，务必了解每个互操作方法的性能影响。  
  
 无论使用的互操作方法，特殊的转换序列，调用 thunk，所需每次托管的函数调用非托管的函数，反之亦然。 由 Visual c + + 编译器，自动插入这些 thunk，但务必请记住，累积，这些转换可能会产生很大影响性能。  
  
## <a name="reducing-transitions"></a>减少转换  
 若要避免或减少的互操作的 thunk 的成本的一种方法是重构涉及尽量减少托管/非托管的转换的接口。 可以通过定向聊天式界面，是指那些涉及跨托管/非托管边界频繁调用进行极大地提高性能。 托管调用的函数，非托管的函数在紧凑循环，例如，是的良好候选重构。 如果循环本身移动到非托管端，或者如果一个托管的替代方法创建非托管的调用 （可能是在托管端上的队列数据，然后封送到非托管 API 在一次循环后） 的转换数可以减少登录ificantly。  
  
## <a name="pinvoke-vs-c-interop"></a>P/Invoke vs。C++ 互操作  
 对于.NET 语言，例如 Visual Basic 和 C# 中，与本机组件互操作性的规定的方法是 P/Invoke。 因为.NET Framework 支持 P/Invoke，则 Visual c + + 支持，但 Visual c + + 还提供其自己的互操作性的支持，这被称为 c + + 互操作。 C + + 互操作通过 P/Invoke 中都是首选的因为 P/Invoke 不是类型安全。 因此，在运行时，主要报告错误，但 c + + 互操作还具有通过 P/Invoke 的性能优势。  
  
 这两种方法需要发生每当托管的函数调用非托管的函数的几种方法：  
  
-   函数调用自变量进行封送从 CLR 到本机类型。  
  
-   执行托管到非托管的转换 （thunk）。  
  
-   非托管的函数调用 （使用参数的本机版本）。  
  
-   执行非托管到托管的转换 （thunk）。  
  
-   返回类型和任何"out"或"中，out"参数进行封送从本机到 CLR 类型。  
  
 托管/非托管 thunk 是必需的互操作正常工作所，但是所需的数据封送处理取决于涉及的数据类型、 函数签名，以及如何使用数据。  
  
 由 c + + 互操作执行数据封送处理是最简单的可能形式： 跨托管/非托管边界方式按位; 只需复制参数在所有不执行任何转换。 对于 P/Invoke，这是仅当所有参数都是简单的则为 true 通用类型。 否则，将 P/Invoke 执行十分可靠的步骤将每个托管的参数转换为相应的本机类型，并且，反之亦然，这样如果自变量均被标记为"out"或"中，out"。  
  
 换而言之，c + + 互操作使用的封送处理数据，最快的可能的方法，而 P/Invoke 使用最可靠的方法。 也就是说，c + + 互操作 （在典型的 c + + 的方式） 默认情况下，提供最佳性能，程序员负责寻址情况下此行为不安全或不适合的情况。  
  
 因此，c + + 互操作要求必须显式提供数据封送处理但的优点是程序员可以自由地确定什么是适当的情况下，数据的性质，因此它是要使用。 此外，尽管的 P/Invoke 数据封送处理行为可以修改在程度的自定义，c + + 互操作允许数据封送处理调用的基础上可自定义。 这不是，可以使用 P/Invoke。  
  
 有关 c + + 互操作的详细信息，请参阅[使用 c + + 互操作 (隐式 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)。  
  
## <a name="see-also"></a>请参阅  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)