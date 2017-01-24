---
title: "如何：从 STL/CLR 容器转换为 .NET 集合 | Microsoft Docs"
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
  - "STL/CLR, 转换为 .NET 集合"
ms.assetid: 70b2dfd9-869c-4e0f-9a29-b1ee0cb0d107
caps.latest.revision: 8
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：从 STL/CLR 容器转换为 .NET 集合
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此主题演示如何转换 STL\/CLR 容器为其等效的 .NET 集合。  例如，我们演示如何翻译 STL\/CLR [矢量](../dotnet/vector-stl-clr.md) 到 .NET <xref:System.Collections.Generic.ICollection%601> 以及如何转换 STL\/CLR [映射](../dotnet/map-stl-clr.md) 到 .NET <xref:System.Collections.Generic.IDictionary%602>，但是，对于所有过程集合与容器类似。  
  
### 创建从容器的集合  
  
1.  使用下列方法之一：  
  
    -   转换一部分，容器调用 [make\_collection](../dotnet/make-collection-stl-clr.md) 函数并将开始迭代器和要复制的 STL\/CLR 容器结束迭代器为 .NET 集合。  此模板函数采用 STL\/CLR 迭代数作为模板参数。  第一个示例演示了此方法。  
  
    -   若要转换整个容器，则转换容器的相应的 .NET 集合接口或接口的集合。  第二个示例演示了该方法。  
  
## 示例  
 在此示例中，我们创建 STL\/CLR `vector` 并添加元素 5 到它。  然后，我们通过调用 `make_collection` 函数创建 .NET 集合。  最后，将显示新生成集合的内容。  
  
```  
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
  
  **System::Collections::Generic::ICollection 的内容如下：**  
**3**  
**5**  
**7**   
## 示例  
 在此示例中，我们创建 STL\/CLR `map` 并添加元素 5 到它。  然后，我们创建 .NET <xref:System.Collections.Generic.IDictionary%602> 并将 `map` 直接给它。  最后，将显示新生成集合的内容。  
  
```  
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
  
  **IDictionary 的内容如下：**  
**键：0.00 值：0**  
**键：13.00 值：13**  
**键：22.00 值：22**  
**键：42.00 值：42**  
**键：74.00 值：74**   
## 请参阅  
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)   
 [如何：从 .NET 集合转换为 STL\/CLR 容器](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)   
 [range\_adapter](../dotnet/range-adapter-stl-clr.md)