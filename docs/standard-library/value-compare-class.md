---
title: "value_compare 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- value_compare
dev_langs:
- C++
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
caps.latest.revision: 20
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
translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: c82ae35feadcf1f28af47d3f055e854f7bcf6a34
ms.lasthandoff: 02/24/2017

---
# <a name="valuecompare-class"></a>value_compare 类
提供一个函数对象，该对象能通过比较 hash_map 元素的键值来比较这些元素，以确定其在 hash_map 中的相对顺序。  
  
## <a name="syntax"></a>语法  
  
```
class value_compare
 : std::public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(
    const value_type& left,
    const value_type& right) const
 {
    return (comp(left.first, right.first));

 }
protected:
    value_compare(const key_compare& c) : comp (c) { }
    key_compare comp;
};
```  
  
## <a name="remarks"></a>备注  
 辅助类构造包含的相应元素的键之间的比较将引发一种比较条件，这种比较条件由 hash_map 包含的整个元素的 **value_types** 之间的 value_compare 提供。 成员函数运算符使用 value_compare 提供的函数对象中存储的 `key_compare` 类型的 **comp** 对象，用于比较两个元素的排序键组件。  
  
 对于 hash_set 和 hash_multiset（二者均为键值与元素值完全相同的简单容器），value_compare 等效于 `key_compare`；对于 hash_map 和 hash_multimap，它们则不相等，因为类型 `pair` 元素的值与元素的键值不完全相同。  
  
 在 Visual C++ .NET 2003 中，[<hash_map>](../standard-library/hash-map.md) 和 [<hash_set>](../standard-library/hash-set.md) 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
## <a name="example"></a>示例  
 有关如何声明和使用 value_compare 的示例，请参阅 [hash_map::value_comp](../standard-library/hash-map-class.md#hash_map__value_comp) 的示例。  
  
## <a name="requirements"></a>要求  
 **标头：**\<hash_map>  
  
 **命名空间：** stdext  
  
## <a name="see-also"></a>另请参阅  
 [binary_function 结构](../standard-library/binary-function-struct.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)




