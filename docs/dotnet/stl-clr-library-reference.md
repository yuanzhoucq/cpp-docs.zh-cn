---
title: STL/CLR 库参考
ms.date: 09/18/2018
ms.topic: reference
helpviewer_keywords:
- STL/CLR Library
- STL/CLR, redistribution
- cliext directory
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
ms.openlocfilehash: b3c25a40fdb5bade02e112b13d16420b248a177f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384629"
---
# <a name="stlclr-library-reference"></a>STL/CLR 库参考

STL/CLR 库提供一个接口类似于C++与一起使用的标准库容器C++和.NET Framework 公共语言运行时 (CLR)。 STL/CLR 是完全独立于 Microsoft 实现的C++标准库。 STL/CLR 的旧版支持维持不变，但不是保持为最新的C++标准。 我们强烈建议使用本机[C++标准库](../standard-library/cpp-standard-library-reference.md)而不是 STL/CLR 尽可能的容器。

若要使用 STL/CLR:

- 包含从标头**cliext**包括子目录而非常规C++标准库等效项。

- 用限定库`cliext::`而不是`std::`。

STL/CLR 库还提供了一个类似于 STL 的接口，可用于C++和.NET Framework 公共语言运行时 (CLR)。 此库的旧版支持维持不变，但不是保持为最新的C++标准。 我们强烈建议使用本机[C++标准库](../standard-library/cpp-standard-library-reference.md)而不是 STL/CLR 容器。

## <a name="in-this-section"></a>本节内容

[cliext 命名空间](../dotnet/cliext-namespace.md)<br/>
讨论包含 STL/CLR 库所有类型的命名空间。

[STL/CLR 容器](../dotnet/stl-clr-containers.md)<br/>
提供的容器中找到的概述C++标准库，包括对容器元素、 可以插入的元素的类型和所有权问题。

[STL/CLR 容器元素的需求](../dotnet/requirements-for-stl-clr-container-elements.md)<br/>
介绍对所有引用类型插入到的最低要求C++标准库容器。

[如何：从 .NET 集合转换为 STL/CLR 容器](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
介绍如何将.NET 集合转换为 STL/CLR 容器。

[如何：从 STL/CLR 容器转换为 .NET 集合](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)<br/>
介绍如何将 STL/CLR 容器转换为.NET 集合。

[如何：从程序集公开 STL/CLR 容器](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)<br/>
演示如何显示几个 STL/CLR 容器写入的元素C++程序集。

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
