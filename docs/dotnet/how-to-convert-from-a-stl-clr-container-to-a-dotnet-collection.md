---
title: 如何：从 STL/CLR 容器转换为 .NET 集合
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, converting to .NET collections
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
ms.openlocfilehash: f7539b10ca6c503aede61d19de3d14fb9dcee8be
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545305"
---
# <a name="how-to-convert-from-a-stlclr-container-to-a-net-collection"></a>如何：从 STL/CLR 容器转换为 .NET 集合

本主题演示如何将 STL/CLR 容器转换为其等效的 .NET 集合。 例如，我们将演示如何将 STL/CLR[向量](../dotnet/vector-stl-clr.md)转换为 .net <xref:System.Collections.Generic.ICollection%601>，以及如何将 STL/clr[映射](../dotnet/map-stl-clr.md)转换为 .net <xref:System.Collections.Generic.IDictionary%602>，但对于所有集合和容器来说，此过程都是类似的。

### <a name="to-create-a-collection-from-a-container"></a>从容器创建集合

1. 使用下列方法之一：

   - 若要转换容器的一部分，请调用[make_collection](../dotnet/make-collection-stl-clr.md)函数，并传递要复制到 .net 集合中的 STL/CLR 容器的开始迭代器和结束迭代器。 此模板函数使用 STL/CLR 迭代器作为模板参数。 第一个示例演示了此方法。

   - 若要转换整个容器，请将容器强制转换为相应的 .NET 集合接口或接口集合。 第二个示例演示了此方法。

## <a name="example"></a>示例

在此示例中，我们将创建一个 STL/CLR `vector` 并向其中添加5个元素。 然后，通过调用 `make_collection` 函数创建 .NET 集合。 最后，我们将显示新创建的集合的内容。

```cpp
// cliext_convert_vector_to_icollection.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/vector>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::vector<int> primeNumbersCont;
    primeNumbersCont.push_back(2);
    primeNumbersCont.push_back(3);
    primeNumbersCont.push_back(5);
    primeNumbersCont.push_back(7);
    primeNumbersCont.push_back(11);

    System::Collections::Generic::ICollection<int> ^iColl =
        make_collection<cliext::vector<int>::iterator>(
            primeNumbersCont.begin() + 1,
            primeNumbersCont.end() - 1);

    Console::WriteLine("The contents of the System::Collections::Generic::ICollection are:");
    for each (int i in iColl)
    {
        Console::WriteLine(i);
    }
}
```

```Output
The contents of the System::Collections::Generic::ICollection are:
3
5
7
```

## <a name="example"></a>示例

在此示例中，我们将创建一个 STL/CLR `map` 并向其中添加5个元素。 然后，创建一个 .NET <xref:System.Collections.Generic.IDictionary%602> 并直接将 `map` 分配给它。 最后，我们将显示新创建的集合的内容。

```cpp
// cliext_convert_map_to_idictionary.cpp
// compile with: /clr

#include <cliext/adapter>
#include <cliext/map>

using namespace cliext;
using namespace System;
using namespace System::Collections::Generic;

int main(array<System::String ^> ^args)
{
    cliext::map<float, int> ^aMap = gcnew cliext::map<float, int>;
    aMap->insert(cliext::make_pair<float, int>(42.0, 42));
    aMap->insert(cliext::make_pair<float, int>(13.0, 13));
    aMap->insert(cliext::make_pair<float, int>(74.0, 74));
    aMap->insert(cliext::make_pair<float, int>(22.0, 22));
    aMap->insert(cliext::make_pair<float, int>(0.0, 0));

    System::Collections::Generic::IDictionary<float, int> ^iDict = aMap;

    Console::WriteLine("The contents of the IDictionary are:");
    for each (KeyValuePair<float, int> ^kvp in iDict)
    {
        Console::WriteLine("Key: {0:F} Value: {1}", kvp->Key, kvp->Value);
    }
}
```

```Output
The contents of the IDictionary are:
Key: 0.00 Value: 0
Key: 13.00 Value: 13
Key: 22.00 Value: 22
Key: 42.00 Value: 42
Key: 74.00 Value: 74
```

## <a name="see-also"></a>另请参阅

[STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)<br/>
[如何：从 .NET 集合转换为 STL/CLR 容器](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)<br/>
[range_adapter (STL/CLR)](../dotnet/range-adapter-stl-clr.md)
