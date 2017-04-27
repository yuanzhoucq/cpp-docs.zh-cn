---
title: "&lt;hash_map&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
caps.latest.revision: 9
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: 6c11e1f90ce05aa3a4dc22ce31bed104ef0fa795
ms.lasthandoff: 02/24/2017

---
# <a name="lthashmapgt-functions"></a>&lt;hash_map&gt; 函数
|||  
|-|-|  
|[swap](#swap)|[swap (hash_map)](#swap__hash_map_)|  
  
##  <a name="swap__hash_map_"></a>swap (hash_map)  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_map 类](../standard-library/unordered-map-class.md)。  
  
 交换两个 hash_map 的元素。  
  
```
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 其元素将与映射 `left` 的元素进行交换的 hash_map。  
  
 `left`  
 其元素将与映射 `right` 的元素进行交换的 hash_map。  
  
### <a name="remarks"></a>备注  
 模板函数是容器类 hash_map 上专用化的算法，用以执行成员函数 `left.`[swap](../standard-library/basic-ios-class.md#basic_ios__swap)*(right*)。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 在算法头文件中，模板函数的通用版本（**模板 \<class T> void swap(T&, T&)**）按分配工作，是一种慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
##  <a name="swap"></a>swap  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_multimap 类](../standard-library/unordered-multimap-class.md)。  
  
 交换两个 hash_multimap 的元素。  
  
```
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 其元素要与映射 `left` 的元素进行交换的 hash_multimap。  
  
 `left`  
 其元素要与映射 `right` 的元素进行交换的 hash_multimap。  
  
### <a name="remarks"></a>备注  
 模板函数是容器类 hash_multimap 上专用化的算法，用以执行成员函数 `left.`[swap](../standard-library/hash-multimap-class.md#hash_multimap__swap)*(right*`)`。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 在算法头文件中，模板函数的通用版本（**模板 \<class T> void swap(T&, T&)**）按分配工作，是一种慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
## <a name="see-also"></a>另请参阅  
 [<hash_map>](../standard-library/hash-map.md)




