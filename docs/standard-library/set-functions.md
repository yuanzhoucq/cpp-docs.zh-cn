---
title: "&lt;set&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
caps.latest.revision: 7
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: fb2b30dc58b7ba65dd13a07cec8456ea4adeb5e1
ms.lasthandoff: 02/24/2017

---
# <a name="ltsetgt-functions"></a>&lt;set&gt; 函数
|||  
|-|-|  
|[swap (map)](#swap)|[swap (multiset)](#swap_multiset)|  
  
##  <a name="a-nameswapa--swap--map"></a><a name="swap"></a>swap (map)
 交换两个集的元素。  
  
```
template <class Key, class Traits, class Allocator>  
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 提供要交换元素的集，或其元素将与集 `left` 的元素交换的集。  
  
 `left`  
 其元素将与集 `right` 的元素交换的集。  
  
### <a name="remarks"></a>备注  
 模板函数是容器类上专用化的算法，用以执行成员函数 `left``.`[swap](../standard-library/set-class.md#set__swap)( `right`)。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 模板函数的通用版本  
  
 `template` \< **classT**> **void swap**( **T&**, **T&**)  
  
 在此算法中，类按赋值进行工作，这是一种慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。  
  
### <a name="example"></a>示例  
  有关使用 `swap` 模板函数的示例，请参阅成员类 [set::swap](../standard-library/set-class.md#set__swap) 的代码示例。  
  
##  <a name="a-nameswapmultiseta--swap--multiset"></a><a name="swap_multiset"></a>  swap (multiset)
 交换两个多重集的元素。  
  
```
template <class Key, class Traits, class Allocator>  
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 多重集提供要交换的元素或其元素要与多重集 `left` 的元素进行交换的多重集。  
  
 `left`  
 其元素将与多重集 `right` 的元素进行交换的多重集。  
  
### <a name="remarks"></a>备注  
 模板函数是容器类多重集上专用化的算法，用以执行成员函数 `left``.`[swap](../standard-library/multiset-class.md#multiset__swap)(`right`)。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 模板函数的通用版本  
  
 `template` \< **classT**> **void swap**( **T&**, **T&**)  
  
 在此算法中，类按赋值进行工作，这是一种慢速操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。  
  
### <a name="example"></a>示例  
  有关使用 `swap` 的模板函数的示例，请参阅成员类 [multiset::swap](../standard-library/multiset-class.md#multiset__swap) 的代码示例。  
  
## <a name="see-also"></a>另请参阅  
 [\<set>](../standard-library/set.md)




