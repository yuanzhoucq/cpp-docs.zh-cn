---
title: "initializer_list Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# initializer_list Class
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供访问元素数组的权限，其中数组的每个成员均具有指定的类型。  
  
## 语法  
  
```cpp  
template<  
    class Type >  
    class initializer_list  
```  
  
#### 参数  
  
|参数|描述|  
|--------|--------|  
|`_Elem`|要在 `initializer_list` 中存储的元素数据类型。|  
|`_First`|指向 `initializer_list` 的第一个元素的指针。|  
|`_Last`|指向 `initializer_list` 的最后一个元素的指针。|  
  
## 备注  
 使用大括号内的初始值设定项列表可构造 `initializer_list`。  
  
```cpp  
initializer_list<int> i1{ 1, 2, 3, 4 };  
```  
  
 每当函数签名需要 `initializer_list` 时，编译器将具有同类元素的大括号内的初始值设定项列表转换为 `initializer_list`。  有关使用 `initializer_list` 的详细信息，请参阅[统一安装和委派构造函数](../cpp/uniform-initialization-and-delegating-constructors.md)  
  
### 构造函数  
  
|||  
|-|-|  
|[initializer\_list](../Topic/forward_list::forward_list.md)|构造 `initializer_list` 类型的对象。|  
  
### Typedef  
  
|||  
|-|-|  
|value\_type|`initializer_list` 中元素的类型。|  
|引用|一个类型，它提供对 `initializer_list` 中元素的引用。|  
|const\_reference|一个类型，它提供对 `initializer_list` 中元素的常量引用。|  
|size\_type|一个类型，它表示 `initializer_list` 中元素的数目。|  
|iterator|一个类型，它为 `initializer_list` 提供迭代器。|  
|const\_iterator|一个类型，它为 `initializer_list` 提供常量迭代器。|  
  
### 成员函数  
  
|||  
|-|-|  
|[begin](../Topic/initializer_list::begin.md)|返回指向 `initializer_list` 中第一个元素的指针。|  
|[end](../Topic/initializer_list::end.md)|返回指向 `initializer_list` 中最后一个元素之后的元素的指针。|  
|[size](../Topic/initializer_list::size.md)|返回 `initializer_list` 中的元素数量。|  
  
## 要求  
 **标头：**\<initializer\_list\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<forward\_list\>](../standard-library/forward-list.md)