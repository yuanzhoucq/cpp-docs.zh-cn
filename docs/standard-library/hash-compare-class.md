---
title: "hash_compare 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "hash_set/stdext::hash_compare"
  - "std.hash_compare"
  - "hash_compare"
  - "std::hash_compare"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "hash_compare 类"
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
caps.latest.revision: 21
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# hash_compare 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述了一个对象，任何哈希关联容器（hash\_map、hash\_multimap、hash\_set 或 hash\_multiset）都可将该对象用作默认的 **Traits** 参数对象，以对其所包含的元素进行排序和哈希处理。  
  
## 语法  
  
```  
template<class Key, class Traits = less<Key> >  
   class hash_compare  
   {  
   Traits comp;  
public:  
   const size_t bucket_size = 4;  
   const size_t min_buckets = 8;  
   hash_compare( );  
   hash_compare( Traits pred );  
   size_t operator( )( const Key& _Key ) const;  
   bool operator( )(   
      const Key& _Key1,  
      const Key& _Key2  
   ) const;  
   };  
```  
  
## 备注  
 每个哈希关联容器都存储一个 **Traits** 类型的哈希特征对象（模板参数）。  可以从 hash\_compare 专用化中派生一个类，用于选择性地重写某些函数和对象，也可以在满足某些最低要求时提供你所拥有的该类的版本。  具体而言，对于类型 **hash\_compare\<Key, Traits\>** 的对象 hash\_comp，上述容器需要以下行为：  
  
-   对于类型 **Key** 的所有值 `_Key`，调用 **hash\_comp** \(`_Key`\) 用作哈希函数，这将产生类型为 **size\_t** 的值的分布。  由 hash\_compare 提供的函数将返回 `_Key`。  
  
-   对于序列中位于 `_Key2` 之前且具有相同哈希值（由哈希函数返回的值）的类型 **Key** 的任何值`_Key1`，**hash\_comp**\(`_Key2`, `_Key1`\) 为 false。  该函数必须在**键**类型的值上施加全面排序。  由 hash\_compare 提供的函数将返回 *comp*\(`_Key2`, `_Key1`\)`,`其中 *comp* 是构造对象 hash\_comp 时可指定的类型 **Traits** 的存储对象。  对于默认的 **Traits** 参数类型 **less\<Key\>**，排序键的值永远不会减小。  
  
-   整数常量 **bucket\_size** 指定容器不应尝试超过的每个"存储桶"（哈希表项）的平均元素数目。  该数目必须大于零。  由 hash\_compare 提供的值为 4。  
  
-   整数常量 **min\_buckets** 指定要保留在哈希表中的存储桶的最小数目。  该数目必须是 2 的幂且大于零。  Hash\_compare 提供的值为 8。  
  
 在 Visual C\+\+ .NET 2003 中，[\<hash\_map\>](../standard-library/hash-map.md) 和 [\<hash\_set\>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。  有关更多信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
## 示例  
 有关如何声明和使用 hash\_compare 的示例，请参阅 [hash\_map::hash\_map](../Topic/hash_map::hash_map.md)、[hash\_multimap::hash\_multimap](../Topic/hash_multimap::hash_multimap.md)、[hash\_set::hash\_set](../Topic/hash_set::hash_set.md) 和 [hash\_multiset::hash\_multiset](../Topic/hash_multiset::hash_multiset.md) 的示例。  
  
## 要求  
 **标头：**\<hash\_map\>  
  
 **命名空间：**stdext  
  
## 请参阅  
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [标准模板库](../misc/standard-template-library.md)