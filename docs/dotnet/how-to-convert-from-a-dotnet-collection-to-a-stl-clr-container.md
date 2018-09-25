---
title: 如何： 从.NET 集合转换为 STL/CLR 容器 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- STL/CLR, converting from .NET collections
- STL/CLR Containers [STL/CLR]
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: ba6d6193c8422e25e174c7a4b73b2b74095cced9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436502"
---
# <a name="how-to-convert-from-a-net-collection-to-a-stlclr-container"></a>如何：从 .NET 集合转换为 STL/CLR 容器

本主题演示如何将.NET 集合转换为其等效的 STL/CLR 容器。 作为示例，我们演示如何将.NET 转换<xref:System.Collections.Generic.List%601>到 STL/CLR[向量](../dotnet/vector-stl-clr.md)以及如何将.NET 转换<xref:System.Collections.Generic.Dictionary%602>到 STL/CLR[映射](../dotnet/map-stl-clr.md)，但该过程是相似的所有集合和容器.

### <a name="to-create-a-container-from-a-collection"></a>若要从集合中创建容器

1. 将整个集合时，创建 STL/CLR 容器，并将集合传递给构造函数。

     第一个示例演示了此过程。

- 或 -

1. 通过创建来创建一个通用的 STL/CLR 容器[collection_adapter](../dotnet/collection-adapter-stl-clr.md)对象。 此模板类将.NET 集合接口作为参数。 若要验证哪些接口受支持，请参阅[collection_adapter (STL/CLR)](../dotnet/collection-adapter-stl-clr.md)。

1. 将.NET 集合中的内容复制到容器。 这可以通过使用 STL/CLR[算法](../dotnet/algorithm-stl-clr.md)，或通过遍历.NET 集合并将每个元素的副本插入到 STL/CLR 容器。

     第二个示例演示了此过程。

## <a name="example"></a>示例

在此示例中，我们将创建一个泛型<xref:System.Collections.Generic.List%601>并向其添加 5 个元素。 然后，我们创建`vector`使用构造函数采用<xref:System.Collections.Generic.IEnumerable%601>作为自变量。

```
// cliext_convert_list_to_vector.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/vector>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    List<int> ^primeNumbersColl = gcnew List<int>();
    primeNumbersColl->Add(2);
    primeNumbersColl->Add(3);
    primeNumbersColl->Add(5);
    primeNumbersColl->Add(7);
    primeNumbersColl->Add(11);

    cliext::vector<int> ^primeNumbersCont =
        gcnew cliext::vector<int>(primeNumbersColl);

    Console::WriteLine("The contents of the cliext::vector are:");
    cliext::vector<int>::const_iterator it;
    for (it = primeNumbersCont->begin(); it != primeNumbersCont->end(); it++)
    {
        Console::WriteLine(*it);
    }
}
```

```Output
The contents of the cliext::vector are:
2
3
5
7
11
```

## <a name="example"></a>示例

在此示例中，我们将创建一个泛型<xref:System.Collections.Generic.Dictionary%602>并向其添加 5 个元素。 然后，我们创建`collection_adapter`包装<xref:System.Collections.Generic.Dictionary%602>作为简单的 STL/CLR 容器。 最后，我们创建`map`并将复制的内容<xref:System.Collections.Generic.Dictionary%602>到`map`通过遍历`collection_adapter`。 在此过程中，我们创建一个新的对通过使用`make_pair`函数，并插入新的对直接`map`。

```
// cliext_convert_dictionary_to_map.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/algorithm>
#include <cliext/map>

using namespace System;
using namespace System::Collections;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    System::Collections::Generic::Dictionary<float, int> ^dict =
        gcnew System::Collections::Generic::Dictionary<float, int>();
    dict->Add(42.0, 42);
    dict->Add(13.0, 13);
    dict->Add(74.0, 74);
    dict->Add(22.0, 22);
    dict->Add(0.0, 0);

    cliext::collection_adapter<System::Collections::Generic::IDictionary<float, int>> dictAdapter(dict);
    cliext::map<float, int> aMap;
    for each (KeyValuePair<float, int> ^kvp in dictAdapter)
    {
        cliext::pair<float, int> aPair = cliext::make_pair(kvp->Key, kvp->Value);
        aMap.insert(aPair);
    }

    Console::WriteLine("The contents of the cliext::map are:");
    cliext::map<float, int>::const_iterator it;
    for (it = aMap.begin(); it != aMap.end(); it++)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", it->first, it->second);
    }
}
```

```Output
The contents of the cliext::map are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>请参阅

[STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)<br/>
[adapter (STL/CLR)](../dotnet/adapter-stl-clr.md)<br/>
[如何：从 STL/CLR 容器转换为 .NET 集合](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)