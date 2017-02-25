---
title: "STL/CLR 库参考 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cliext 目录"
  - "STL/CLR 库"
  - "STL/CLR, 重新分发"
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# STL/CLR 库参考
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

STL\/CLR 库由标准模板库 \(STL\)（标准 C\+\+ 库的子集）打包而成，用于 C\+\+ 和 .NET Framework 公共语言运行时 \(CLR\)。  通过 STL\/CLR，可以在托管环境中使用 STL 的所有容器、迭代器和算法。  
  
 使用 STL\/CLR：  
  
-   **cliext** 中的包含标题包括子目录而不包括有用的标准 C\+\+ 库等效。  
  
-   使用 `cliext::` 而非 `std::` 限定库名称。  
  
 STL\/CLR 公开其在 .NET 程序集 **Microsoft.VisualC.STLCLR.dll** 中的跨程序集方案中使用的泛型类型和接口。  .NET Framework 3.5 中包含该 DLL。  如果重新发布使用 STL\/CLR 的应用程序，则需要将 .NET framework 3.5 以及项目使用的其他 Visual C\+\+ 库包括在设置项目的依赖项部分中。  
  
## 本节内容  
 [cliext 命名空间](../dotnet/cliext-namespace.md)  
 讨论包含 STL\/CLR 库所有类型的命名空间。  
  
 [STL\/CLR 容器](../dotnet/stl-clr-containers.md)  
 提供包含于标准 C\+\+ 库的容器概述，包括容器元素要求、可插入的元素类型和所有权问题。  
  
 [STL\/CLR 容器元素的要求](../dotnet/requirements-for-stl-clr-container-elements.md)  
 描述对所有插入 STL 容器的引用类型的最低要求。  
  
 [如何：从 .NET 集合转换为 STL\/CLR 容器](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)  
 介绍如何将 .NET 集合转换为 STL\/CLR 容器。  
  
 [如何：从 STL\/CLR 容器转换为 .NET 集合](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)  
 介绍如何将 STL\/CLR 容器转换为 .NET 集合。  
  
 [如何：公开程序集中的 STL\/CLR 容器](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)  
 显示如何显示写入 C\+\+ 程序集的几个 STL\/CLR 容器的元素。  
  
 此外，本节还介绍 STL\/CLR 的以下组件：  
  
|||  
|-|-|  
|[adapter](../dotnet/adapter-stl-clr.md)|[algorithm](../dotnet/algorithm-stl-clr.md)|  
|[deque](../dotnet/deque-stl-clr.md)|[for each，in](../dotnet/for-each-in.md)|  
|[functional](../dotnet/functional-stl-clr.md)|[hash\_map](../dotnet/hash-map-stl-clr.md)|  
|[hash\_multimap](../dotnet/hash-multimap-stl-clr.md)|[hash\_multiset](../dotnet/hash-multiset-stl-clr.md)|  
|[hash\_set](../dotnet/hash-set-stl-clr.md)|[list](../dotnet/list-stl-clr.md)|  
|[map](../dotnet/map-stl-clr.md)|[multimap](../dotnet/multimap-stl-clr.md)|  
|[multiset](../dotnet/multiset-stl-clr.md)|[numeric](../dotnet/numeric-stl-clr.md)|  
|[priority\_queue](../dotnet/priority-queue-stl-clr.md)|[queue](../dotnet/queue-stl-clr.md)|  
|[集合](../dotnet/set-stl-clr.md)|[stack](../dotnet/stack-stl-clr.md)|  
|[utility](../dotnet/utility-stl-clr.md)|[向量](../dotnet/vector-stl-clr.md)|  
  
## 请参阅  
 [C\+\+ 标准库](../standard-library/cpp-standard-library-reference.md)