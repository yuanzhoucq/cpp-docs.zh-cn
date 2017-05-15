---
title: '&lt;vector&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <vector>
- std.<vector>
- std::<vector>
dev_langs:
- C++
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 77c13a5f8d813bbeaa0dae2307769a575bb22fa8
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="ltvectorgt"></a>&lt;vector&gt;
定义容器模板类矢量和几个支持模板。  
  
 `vector` 是将给定类型的元素组织到线性序列中的容器。 它使用户可以快速随机访问任何元素，并动态添加到序列和动态从序列中删除。 `vector` 是随机访问性能超出限制时的首选序列容器。  
  
 有关类 `vector` 的详细信息，请参阅 [vector 类](../standard-library/vector-class.md)。 有关专业化 `vector<bool>` 的信息，请参阅 [vector\<bool> 类](../standard-library/vector-bool-class.md)。  
  
## <a name="syntax"></a>语法  
  
```  
namespace std {  
template <class Type, class Allocator>  
class vector;  
template <class Allocator>  
class vector<bool>;  
 
template <class Allocator>  
struct hash<vector<bool, Allocator>>;  
 // TEMPLATE FUNCTIONS  
template <class Type, class Allocator>  
bool operator== (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator!= (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator<(
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator> (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator<= (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
bool operator>= (
    const vector<Type, Allocator>& left,  
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>  
void swap (
    vector<Type, Allocator>& left,  
    vector<Type, Allocator>& right);

}  // namespace std  
```  
  
#### <a name="parameters"></a>参数  
 类型  
 向量中所存储的数据类型的模板参数。  
  
 分配器  
 负责分配和释放内存的已存储分配器对象的模板参数。  
  
 `left`  
 比较操作中的第一个（左）向量  
  
 `right`  
 比较操作中的第二个（右）向量。  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator! =](../standard-library/vector-operators.md#op_neq)|测试运算符左侧的向量对象是否等于右侧的向量对象。|  
|[operator<](../standard-library/vector-operators.md#op_lt)|测试运算符左侧的向量对象是否小于右侧的向量对象。|  
|[operator\<=](../standard-library/vector-operators.md#op_gt_eq)|测试运算符左侧的向量对象是否小于或等于右侧的向量对象。|  
|[operator==](../standard-library/vector-operators.md#op_eq_eq)|测试运算符左侧的向量对象是否等于右侧的向量对象。|  
|[operator>](../standard-library/vector-operators.md#op_gt)|测试运算符左侧的向量对象是否大于右侧的向量对象。|  
|[operator>=](../standard-library/vector-operators.md#op_gt_eq)|测试运算符左侧的向量对象是否大于或等于右侧的向量对象。|  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[vector 类](../standard-library/vector-class.md)|序列容器的一个模板类，这些容器按线性排列方式来排列给定类型的元素，并且允许快速随机访问任何元素。|  
  
### <a name="specializations"></a>专用化  
  
|||  
|-|-|  
|[vector\<bool> 类](../standard-library/vector-bool-class.md)|模板类向量的一个完全专有化，针对类型 `bool` 的元素，且带有专有化所使用的基本类型的分配器。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<vector>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)


