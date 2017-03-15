---
title: "&lt;vector&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
caps.latest.revision: 10
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: bb62c0c4e5b2965438539b17ec5a2c465e647ed7
ms.lasthandoff: 02/24/2017

---
# <a name="ltvectorgt-functions"></a>&lt;vector&gt; 函数

  
##  <a name="a-nameswapa--swap"></a><a name="swap"></a>swap  
 交换两个向量的元素。  
  
```  
template <class Type, class Allocator>  
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
 ` right`  
 提供要交换的元素的矢量，或其元素将要与矢量 ` left` 的元素进行交换的矢量。  
  
 ` left`  
 一个矢量，其元素将与矢量 ` right` 的元素进行交换。  
  
### <a name="remarks"></a>备注  
 模板函数专用于容器类矢量的算法，用以执行成员函数 ` left.` [vector::swap](../standard-library/vector-class.md) ( right)。 这些是由编译器进行的函数模板部分排序的实例。 模板函数以此种方式重载时，模板与函数调用的匹配并不唯一，随后编译器会选择此模板函数的最专用化版本。 在算法类中，模板函数的通用版本 **template** \< **class T**> **void swap**( **T&**, **T&**) 将按分配工作，是一个缓慢操作。 每个容器中的专用化版本速度快很多，因为专用化版本可适用于容器类的内部表示形式。  
  
### <a name="example"></a>示例  
  有关使用 `swap` 的模板版本的示例，请参阅成员函数 [vector::swap](../standard-library/vector-class.md) 的代码示例。  
  
## <a name="see-also"></a>另请参阅  
 [\<vector>](../standard-library/vector.md)


