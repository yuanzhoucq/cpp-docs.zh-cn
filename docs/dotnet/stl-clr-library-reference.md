---
title: STL/CLR 库参考 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8cab573b0c1de57ef2629f662108098095b722eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="stlclr-library-reference"></a>STL/CLR 库参考
STL/CLR 库是子集的一种封装的 c + + 标准库，以用于 c + + 和.NET Framework 公共语言运行时 (CLR)。 与 STL/CLR，可以使用所有容器、 迭代器和的托管环境中的标准库的算法。  
  
 若要使用 STL/CLR:  
  
-   包含标头从**cliext**包括子目录，而不是常用等效的 c + + 标准库。  
  
-   用名称限定库`cliext::`而不是`std::`。  
  
 STL/CLR 公开它在.NET 程序集在跨程序集方案中使用的泛型类型和接口**Microsoft.VisualC.STLCLR.dll**。 此 DLL 包括在.NET Framework 3.5。 如果你重新分发使用 STL/CLR 的应用程序，你将需要包括.NET Framework 3.5，以及你的项目使用，你的安装项目的依赖关系部分中的任何其他 Visual c + + 库。  
  
## <a name="in-this-section"></a>本节内容  
 [cliext 命名空间](../dotnet/cliext-namespace.md)  
 讨论包含 STL/CLR 库的所有类型的命名空间。  
  
 [STL/CLR 容器](../dotnet/stl-clr-containers.md)  
 概述在 c + + 标准库，其中包括针对容器元素、 可以插入的元素的类型和所有权问题需求中找到的容器。  
  
 [STL/CLR 容器元素的需求](../dotnet/requirements-for-stl-clr-container-elements.md)  
 描述所有插入到 c + + 标准库容器的引用类型的最低要求。  
  
 [如何：从 .NET 集合转换为 STL/CLR 容器](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)  
 描述如何将.NET 集合转换为 STL/CLR 容器。  
  
 [如何：从 STL/CLR 容器转换为 .NET 集合](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)  
 描述如何将 STL/CLR 容器转换为.NET 集合。  
  
 [如何：公开程序集中的 STL/CLR 容器](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)  
 演示如何显示编写 c + + 程序集中的多个 STL/CLR 容器的元素。  
  
 此外，本部分还描述 STL/CLR 的以下组件：  
  
|||  
|-|-|  
|[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)|[algorithm (STL/CLR)](../dotnet/algorithm-stl-clr.md)|  
|[deque (STL/CLR)](../dotnet/deque-stl-clr.md)|[for each, in](../dotnet/for-each-in.md)|  
|[functional (STL/CLR)](../dotnet/functional-stl-clr.md)|[hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)|  
|[hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)|[hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)|  
|[hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)|[list (STL/CLR)](../dotnet/list-stl-clr.md)|  
|[map (STL/CLR)](../dotnet/map-stl-clr.md)|[multimap (STL/CLR)](../dotnet/multimap-stl-clr.md)|  
|[multiset (STL/CLR)](../dotnet/multiset-stl-clr.md)|[numeric (STL/CLR)](../dotnet/numeric-stl-clr.md)|  
|[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)|[queue (STL/CLR)](../dotnet/queue-stl-clr.md)|  
|[set (STL/CLR)](../dotnet/set-stl-clr.md)|[stack (STL/CLR)](../dotnet/stack-stl-clr.md)|  
|[utility (STL/CLR)](../dotnet/utility-stl-clr.md)|[vector (STL/CLR)](../dotnet/vector-stl-clr.md)|  
  
## <a name="see-also"></a>请参阅  
 [C++ 标准库](../standard-library/cpp-standard-library-reference.md)