---
title: '&lt;set&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.<set>
- std::<set>
- <set>
dev_langs:
- C++
helpviewer_keywords:
- set header
ms.assetid: 43cb1ab2-6383-48cf-8bdc-2b96d7203596
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
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: 1295a8c71464b7cc9d204c807c3492000b73ffa1
ms.lasthandoff: 02/24/2017

---
# <a name="ltsetgt"></a>&lt;set&gt;
定义容器模板类 set 和 multiset 及其支持的模板。  
  
## <a name="syntax"></a>语法  
  
```  
#include <set>  
  
```  
  
## <a name="members"></a>成员  
  
### <a name="operators"></a>运算符  
  
|Set 版本|Multiset 版本|描述|  
|-----------------|----------------------|-----------------|  
|[operator!= (set)](../standard-library/set-operators.md#operator_neq)|[operator!= (multiset)](../standard-library/set-operators.md#operator_neq)|测试运算符左侧的 set 或 multiset 对象是否不等于右侧的 set 或 multiset 对象。|  
|[operator< (set)](../standard-library/set-operators.md#operator_lt_)|[operator< (multiset)](../standard-library/set-operators.md#operator_lt_)|测试运算符左侧的 set 或 multiset 对象是否小于右侧的 set 或 multiset 对象。|  
|[operator<= (set)](../standard-library/set-operators.md#operator_lt__eq)|[operator\<= (multiset)](../standard-library/set-operators.md#operator_lt__eq)|测试运算符左侧的 set 或 multiset 对象是否小于或等于右侧的 set 或 multiset 对象。|  
|[operator== (set)](../standard-library/set-operators.md#operator_eq_eq)|[operator== (multiset)](../standard-library/set-operators.md#operator_eq_eq)|测试运算符左侧的 set 或 multiset 对象是否等于右侧的 set 或 multiset 对象。|  
|[operator> (set)](../standard-library/set-operators.md#operator_gt_)|[operator> (multiset)](../standard-library/set-operators.md#operator_gt_)|测试运算符左侧的 set 或 multiset 对象是否大于右侧的 set 或 multiset 对象。|  
|[operator>= (set)](../standard-library/set-operators.md#operator_gt__eq)|[operator>= (multiset)](../standard-library/set-operators.md#operator_gt__eq)|测试运算符左侧的 set 或 multiset 对象是否大于或等于右侧的 set 或 multiset 对象。|  
  
### <a name="specialized-template-functions"></a>专用化模板函数  
  
|Set 版本|Multiset 版本|描述|  
|-----------------|----------------------|-----------------|  
|[swap](../standard-library/set-functions.md#swap)|[swap](../standard-library/set-functions.md#swap)|交换两个集或多个集的元素。|  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[set 类](../standard-library/set-class.md)|用于存储和检索集合中的数据，此集合中包含的元素值是唯一的，并且用作数据自动排序所依据的关键字值。|  
|[multiset 类](../standard-library/multiset-class.md)|用于存储和检索集合中的数据，此集合中包含的元素值不必是唯一的，并且可用作数据自动排序所依据的关键字值。|  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)




