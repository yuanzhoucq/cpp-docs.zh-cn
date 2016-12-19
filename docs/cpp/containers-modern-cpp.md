---
title: "容器（现代 C++） | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 6e10b758-e928-4827-9c3f-86cafe54bf5b
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 容器（现代 C++）
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

默认情况下，使用 [向量](../standard-library/vector-class.md) 作为 c + + 中的默认顺序容器。 这等同于列表 \< T> 用其他语言。  
  
```cpp  
vector<string> v;  
v.push_back( "Geddy Lee" );  
  
```  
  
 使用 [映射](../standard-library/map-class.md) (不 unordered_map) 作为默认关联容器。 使用 [设置](../standard-library/set-class.md), ，[多重映射](../standard-library/multimap-class.md), ，[多重集](../standard-library/multiset-class.md) 退化和多用例。  
  
```cpp  
map<string, string> phone_book;  
// ...  
phone_book["Alex Lifeson"] = "+1 (416) 555-1212";  
  
```  
  
 当需要性能优化时，请考虑使用︰  
  
1.  数组类型嵌入时非常重要-例如，作为类成员。  
  
2.  无序的关联容器（unordered_map，等等）：降低每个元素的开销（主要的）和固定时间查找（可能是主要的，有时是次要的）。 由于使用不便且具有陡沿，难以正确有效地使用。  
  
3.  有序矢量。 (请参见︰ [算法](../cpp/algorithms-modern-cpp.md)。)  
  
 不要使用 C 数组。 (对于旧的 Api，使用 `f( vec.data(), vec.size() );` 。)  
  
 有关容器的另一篇文章，请参阅 [STL 容器](../standard-library/stl-containers.md)。  
  
## <a name="container-sizes"></a>容器大小  
 下表显示允许的容器大小，以字节为单位，对于 x86 和 x64 平台。  （用于这些目的，32 位 ARM 等效于 x86。）这些表包括版本模式下，因为调试模式下包含占用空间和时间的检查机制。  单独的列进行 [!INCLUDE[cpp_orcas_long](../cpp/includes/cpp_orcas_long_md.md)] SP1 中，其中 `_SECURE_SCL` 默认设置为 1，并为 [!INCLUDE[cpp_orcas_long](../cpp/includes/cpp_orcas_long_md.md)] SP1 中的 `_SECURE_SCL` 手动设置为 0，最大速度。  在 Visual Studio 2010 中，visual c + + [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)], ，和 [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] 默认 `_SECURE_SCL` 为 0 (现在称为 `_ITERATOR_DEBUG_LEVEL`)。  
  
|x86 容器大小 （字节）|VC9 SP1|VC9 SP1<br /><br /> SCL=0|VC10|VC11|  
|-----------------------------------|-------------|------------------------|----------|----------|  
|向量 \< int>|24|16|16|12|  
|数组 \< int，5 >|20|20|20|20|  
|e q u e \< int>|32|32|24|20|  
|forward_list \< int>|不可用|不可用|8|4|  
|列表 \< int>|28|12|12|8|  
|priority_queue \< int>|28|20|20|16|  
|队列 \< int>|32|32|24|20|  
|堆栈 \< int>|32|32|24|20|  
|对 \< int、 int >|8|8|8|8|  
|元组 \< int、 int、 int >|16|16|16|12|  
|地图 \< int、 int >|32|12|16|8|  
|多重映射 \< int、 int >|32|12|16|8|  
|设置 \< int>|32|12|16|8|  
|多重集合 \< int>|32|12|16|8|  
|hash_map \< int、 int >|72|44|44|32|  
|hash_multimap \< int、 int >|72|44|44|32|  
|hash_set \< int>|72|44|44|32|  
|hash_multiset \< int>|72|44|44|32|  
|unordered_map \< int、 int >|72|44|44|32|  
|unordered_multimap \< int、 int >|72|44|44|32|  
|_ s e t \< int>|72|44|44|32|  
ordered_multiset \< int>|72|44|44|32|  
|string|28|28|28|24|  
|wstring|28|28|28|24|  
  
|x64 容器大小 （字节）|VC9 SP1|VC9 SP1<br /><br /> SCL=0|VC10|VC11|  
|-----------------------------------|-------------|------------------------|----------|----------|  
|向量 \< int>|48|32|32|24|  
|数组 \< int，5 >|20|20|20|20|  
|e q u e \< int>|64|64|48|40|  
|forward_list \< int>|不可用|不可用|16|8|  
|列表 \< int>|56|24|24|16|  
|priority_queue \< int>|56|40|40|32|  
|队列 \< int>|64|64|48|40|  
|堆栈 \< int>|64|64|48|40|  
|对 \< int、 int >|8|8|8|8|  
|元组 \< int、 int、 int >|16|16|16|12|  
|地图 \< int、 int >|64|24|32|16|  
|多重映射 \< int、 int >|64|24|32|16|  
|设置 \< int>|64|24|32|16|  
|多重集合 \< int>|64|24|32|16|  
|hash_map \< int、 int >|144|88|88|64|  
|hash_multimap \< int、 int >|144|88|88|64|  
|hash_set \< int>|144|88|88|64|  
|hash_multiset \< int>|144|88|88|64|  
|unordered_map \< int、 int >|144|88|88|64|  
|unordered_multimap \< int、 int >|144|88|88|64|  
|_ s e t \< int>|144|88|88|64|  
ordered_multiset \< int>|144|88|88|64|  
|string|40|40|40|32|  
|wstring|40|40|40|32|  
  
## <a name="see-also"></a>另请参阅  
 [欢迎回到 c + +](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C + + 语言参考](../cpp/cpp-language-reference.md)   
 [C + + 标准库](../standard-library/cpp-standard-library-reference.md)