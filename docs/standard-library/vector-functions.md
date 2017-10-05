---
title: "&lt;vector&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
caps.latest.revision: 10
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: 239ac662d19e3d0aa788e830557c28bc84835828
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="ltvectorgt-functions"></a>&lt;vector&gt; 函数

  
##  <a name="swap"></a>swap  
 交换两个向量的元素。  
  
```  
template <class Type, class Allocator>  
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 提供要交换的元素的矢量，或其元素将要与矢量 `left` 的元素进行交换的矢量。  
  
 `left`  
 一个矢量，其元素将与矢量 `right` 的元素进行交换。  
  
### <a name="remarks"></a>备注  
 模板函数是一种算法专用于要执行该成员函数的容器类向量`left`。 [vector:: swap](../standard-library/vector-class.md) *(右*)。 这些是由编译器进行的函数模板部分排序的实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 在算法类中，模板函数的通用版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 将按分配工作，是一个缓慢操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。  
  
### <a name="example"></a>示例  
  有关使用 `swap` 的模板版本的示例，请参阅成员函数 [vector::swap](../standard-library/vector-class.md) 的代码示例。  
  
## <a name="see-also"></a>另请参阅  
 [\<vector>](../standard-library/vector.md)


