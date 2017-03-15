---
title: "&lt;hash_set&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 557a0162-3728-4537-97dc-f9f6cc7ece94
caps.latest.revision: 7
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 1238f4a4e75f13ccd660554de8c49646549bc2cc
ms.lasthandoff: 02/24/2017

---
# <a name="lthashsetgt-functions"></a>&lt;hash_set&gt; 函数
|||  
|-|-|  
|[swap](#swap)|[swap (hash_multiset)](#swap__hash_multiset_)|  
  
##  <a name="a-nameswapa--swap"></a><a name="swap"></a>swap  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 交换两个 hash_set 的元素。  
  
```
void swap(
    hash_set <Key, Traits, Allocator>& left,
    hash_set <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 提供要交换的元素的 hash_set 或其元素要与 hash_set `left` 的元素进行交换的 hash_set。  
  
 `left`  
 其元素将与 hash_set `right` 的元素进行交换的 hash_set。  
  
### <a name="remarks"></a>备注  
 `swap` 模板函数是容器类 hash_set 上专用化的算法，用以执行成员函数 `left``.`[swap](../standard-library/hash-set-class.md#hash_set__swap)( `right`)。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 模板函数的通用版本   
  
 **template \<class T> void swap(T&, T&),**   
  
 在此算法中，类按赋值进行工作，这是一种慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关使用 `swap` 的模板版本的示例，请参阅成员类 [hash_set::swap](../standard-library/hash-set-class.md#hash_set__swap) 的代码示例。  
  
##  <a name="a-nameswaphashmultiseta--swap-hashmultiset"></a><a name="swap__hash_multiset_"></a>swap (hash_multiset)  
  
> [!NOTE]
>  此 API 已废弃不用。 替代项为 [unordered_set 类](../standard-library/unordered-set-class.md)。  
  
 交换两个 hash_multiset 的元素。  
  
```
void swap(hash_multiset <Key, Traits, Allocator>& left, hash_multiset <Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 提供要交换的元素的 hash_multiset 或其元素要与 hash_multiset `left` 的元素进行交换的 hash_multiset。  
  
 `left`  
 其元素将与 hash_multiset `right` 的元素进行交换的 hash_multiset。  
  
### <a name="remarks"></a>备注  
 `swap` 模板函数是容器类 hash_multiset 上专用化的算法，用以执行成员函数 `left``.`[swap](../standard-library/hash-multiset-class.md#hash_multiset__swap)( `right`)。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 模板函数的通用版本   
  
 **template \<class T> void swap(T&, T&),**   
  
 在此算法中，类按赋值进行工作，这是一种慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
### <a name="example"></a>示例  
  有关使用 `swap` 的模板版本的示例，请参阅成员类 [hash_multiset::swap](../standard-library/hash-multiset-class.md#hash_multiset__swap) 的代码示例。  
  
## <a name="see-also"></a>另请参阅  
 [<hash_set>](../standard-library/hash-set.md)




