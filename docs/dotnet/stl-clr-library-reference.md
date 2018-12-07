---
title: STL/CLR 库参考
ms.date: 09/18/2018"
ms.topic: reference
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
ms.openlocfilehash: 6914b61597e38c94a214089ecc3aeed17aec46d3
ms.sourcegitcommit: 984fb4814a2dd9bcea5ec88c9528707f17a7cffa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/19/2018
ms.locfileid: "51949513"
---
# <a name="stlclr-library-reference"></a>STL/CLR 库参考

STL/CLR 库提供类似于 c + + 标准库容器的接口与 c + + 和.NET Framework 公共语言运行时 (CLR) 一起使用。 STL/CLR 是完全独立于 c + + 标准库的 Microsoft 实现。 STL/CLR 的旧版支持维持不变，但不是保持为最新的 c + + 标准。 我们强烈建议使用本机[c + + 标准库](../standard-library/cpp-standard-library-reference.md)而不是 STL/CLR 尽可能的容器。

若要使用 STL/CLR:

- 包含从标头**cliext**包括子目录而不是常规 c + + 标准库等效项。

- 用限定库`cliext::`而不是`std::`。

STL/CLR 库适用于 c + + 和.NET Framework 公共语言运行时 (CLR) 提供一个类似于 STL 的接口。 此库的旧版支持维持不变，但不是保持为最新的 c + + 标准。 我们强烈建议使用本机[c + + 标准库](../standard-library/cpp-standard-library-reference.md)而不是 STL/CLR 容器。

## <a name="in-this-section"></a>本节内容

[cliext 命名空间](../dotnet/cliext-namespace.md)<br/>
讨论包含 STL/CLR 库所有类型的命名空间。

[STL/CLR 容器](../dotnet/stl-clr-containers.md)<br/>
概述在 c + + 标准库，包括对容器元素、 可以插入的元素的类型和所有权问题中找到的容器。

[STL/CLR 容器元素的需求](../dotnet/requirements-for-stl-clr-container-elements.md)<br/>
介绍对插入到 c + + 标准库容器的所有引用类型的最低要求。

[如何：从 .NET 集合转换为 STL/CLR 容器](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
介绍如何将.NET 集合转换为 STL/CLR 容器。

[如何：从 STL/CLR 容器转换为 .NET 集合](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)<br/>
介绍如何将 STL/CLR 容器转换为.NET 集合。

[如何：公开程序集中的 STL/CLR 容器](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)<br/>
演示如何显示编写的 c + + 程序集的几个 STL/CLR 容器元素。

此外，本部分还介绍 STL/CLR 的以下组件：

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
