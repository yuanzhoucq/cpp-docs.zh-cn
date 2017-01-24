---
title: "如何：从 .NET 集合转换为 STL/CLR 容器 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "STL/CLR 容器 [STL/CLR]"
  - "STL/CLR, 从 .NET 集合转换"
ms.assetid: bb927c48-78e8-4150-bd0b-787c651f4a87
caps.latest.revision: 9
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：从 .NET 集合转换为 STL/CLR 容器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主题显示如何将 .NET 集合到等效。STL\/CLR 容器  举例来说我们演示如何转换 <xref:System.Collections.Generic.List%601> .NET。STL\/CLR [矢量](../dotnet/vector-stl-clr.md) 和如何将 .NET <xref:System.Collections.Generic.Dictionary%602>。STL\/CLR [映射](../dotnet/map-stl-clr.md)，但过程为所有集合与容器类似。  
  
### 创建从集合的容器  
  
1.  若要将整个集合，请创建并将该集合传递给构造函数。STL\/CLR 容器  
  
     第一个示例演示此过程。  
  
 \- 或 \-  
  
1.  通过 [collection\_adapter](../dotnet/collection-adapter-stl-clr.md) 创建对象创建泛型容器。STL\/CLR  此模板类采用 .NET 集合接口作为参数。  若要验证的接口支持，请参见 [collection\_adapter](../dotnet/collection-adapter-stl-clr.md)。  
  
2.  将 .NET 集合内容的容器。  使用 [算法](../dotnet/algorithm-stl-clr.md)STL\/CLR，可以完成，或由循环访问 .NET 集合和插入每个元素重复到 STL\/CLR 容器。  
  
     第二个示例演示此过程。  
  
## 示例  
 在此示例中，我们创建泛型 <xref:System.Collections.Generic.List%601> 并添加元素 5 到它。  然后，我们创建 `vector` 使用将 <xref:System.Collections.Generic.IEnumerable%601> 用作参数的构造函数。  
  
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
  
  **cliext::vector 的内容如下：**  
**2**  
**3**  
**5**  
**7**  
**11**   
## 示例  
 在此示例中，我们创建泛型 <xref:System.Collections.Generic.Dictionary%602> 并添加元素 5 到它。  然后，我们创建一个 `collection_adapter` 包装 <xref:System.Collections.Generic.Dictionary%602> 作为简单 STL\/CLR 的容器。  最后，我们创建 `map` 并将 <xref:System.Collections.Generic.Dictionary%602> 的内容设置通过 `map` 循环访问 `collection_adapter`。  使用 `make_pair` 函数，在此过程中，我们创建新对，并插入新对直接为 `map`。  
  
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
  
  **cliext::map 的内容如下：**  
**键：0.00 值：0**  
**键：13.00 值：13**  
**键：22.00 值：22**  
**键：42.00 值：42**  
**键：74.00 值：74**   
## 请参阅  
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)   
 [adapter](../dotnet/adapter-stl-clr.md)   
 [如何：从 STL\/CLR 容器转换为 .NET 集合](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)