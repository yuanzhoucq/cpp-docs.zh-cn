---
title: "&lt;map&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
caps.latest.revision: 6
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: d322b318ac4206c5bc27b81299190d129548ef9f
ms.lasthandoff: 02/24/2017

---
# <a name="ltmapgt-functions"></a>&lt;map&gt; 函数
|||  
|-|-|  
|[swap (map)](#swap)|[swap (multimap)](#swap_multimap)|  
  
##  <a name="a-nameswapmultimapa--swap--map"></a><a name="swap_multimap"></a>swap (map)
 交换两个映射的元素。  
  
```  
template <class key, class T, class _Pr, class _Alloc>  
void swap(
    map<Key, Traits, Compare, Alloctor>& left,  
    map<Key, Traits, Compare, Alloctor>& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 提供要交换的元素的映射，或其元素将与映射 ` left` 的元素交换的映射。  
  
 ` left`  
 其元素将与映射 ` right` 的元素进行交换的映射。  
  
### <a name="remarks"></a>备注  
 模板函数是专用于容器类映射的算法，用以执行成员函数 ` left.`[swap](../standard-library/map-class.md#map__swap)*( right*)。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 在算法类中，模板函数的通用版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 将按分配工作，是一个缓慢操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。  
  
### <a name="example"></a>示例  
  有关使用 `swap` 的模板版本的示例，请参阅成员函数 [map::swap](../standard-library/map-class.md#map__swap) 的代码示例。  
  
##  <a name="a-nameswapa--swap--multimap"></a><a name="swap"></a>swap (multimap)
 交换两个多重映射的元素。  
  
```  
template <class key, class T, class _Pr, class _Alloc>  
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,  
    multimap<Key, Traits, Compare, Alloctor>& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 多重映射提供要交换的元素或其元素要与多重映射 ` left` 的元素进行交换。  
  
 ` left`  
 其元素要与多重映射 ` right` 的元素进行交换的多重映射。  
  
### <a name="remarks"></a>备注  
 模板函数是专用于容器类映射的算法，用以在容器类多重映射上执行成员函数 ` left.`[swap](../standard-library/multimap-class.md#multimap__swap) ( ` right`)。 这是由编译器进行的函数模板偏序实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 在算法类中，模板函数的通用版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 将按分配工作，是一个缓慢操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。  
  
### <a name="example"></a>示例  
  有关使用 `swap` 的模板版本的示例，请参阅成员函数 [multimap::swap](../standard-library/multimap-class.md#multimap__swap) 的代码示例。  
  
## <a name="see-also"></a>另请参阅  
 [\<map>](../standard-library/map.md)

