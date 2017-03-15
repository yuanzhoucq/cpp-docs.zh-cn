---
title: '&lt;utility&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <utility>
- utility/std::<utility>
- std.<utility>
- std::<utility>
dev_langs:
- C++
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
caps.latest.revision: 18
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
ms.sourcegitcommit: 41b445ceeeb1f37ee9873cb55f62d30d480d8718
ms.openlocfilehash: 67792e92a4a8336c025249a5d1322d00360a62c5
ms.lasthandoff: 02/24/2017

---
# <a name="ltutilitygt"></a>&lt;utility&gt;
定义有助于构造和管理对象对的 C++ 标准库类型、函数和运算符，这些项在每次需要将两个对象视为单个对象时都非常有用。  
  
## <a name="syntax"></a>语法  
  
```  
#include <utility>  
  
```  
  
## <a name="remarks"></a>备注  
 对广泛用于 C++ 标准库中。 对于各种函数，需要将这些对用作参数和返回值，而对于 [map 类](../standard-library/map-class.md)和 [multimap 类](../standard-library/multimap-class.md)等容器，则需将其用作元素类型。 \<map> 将自动包括 \<utility> 标头以帮助管理其键/值对类型元素。  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|一个包装 `pair` 元素的类型的类。|  
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|一个包装 `pair` 元素计数的类。|  
  
### <a name="functions"></a>函数  
  
|||  
|-|-|  
|[forward](../standard-library/utility-functions.md#forward)|保留参数的引用类型（`lvalue` 或 `rvalue`），使其不被完美转发掩盖。|  
|[get](../standard-library/utility-functions.md#get)|一个从 `pair` 对象获取元素的函数。|  
|[make_pair](../standard-library/utility-functions.md#make_pair)|一个模板帮助程序函数，用于构造类型 `pair` 的对象，其中组件类型基于作为参数传递的数据类型。|  
|[move](../standard-library/utility-functions.md#move)|将传入的参数作为 `rvalue` 引用返回。|  
|[swap](../standard-library/utility-functions.md#swap)|交换两个 `pair` 对象的元素。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator!=](../standard-library/utility-operators.md#operator_neq)|测试运算符左侧和右侧的 pair 对象是否不相等。|  
|[operator==](../standard-library/utility-operators.md#operator_eq_eq)|测试运算符左侧和右侧的 pair 对象是否相等。|  
|[operator<](../standard-library/utility-operators.md#operator_lt_)|测试运算符左侧的 pair 对象是否小于右侧的 pair 对象。|  
|[operator\<=](../standard-library/utility-operators.md#operator_lt__eq)|测试运算符左侧的 pair 对象是否小于或等于右侧的 pair 对象。|  
|[operator>](../standard-library/utility-operators.md#operator_gt_)|测试运算符左侧的 pair 对象是否大于右侧的 pair 对象。|  
|[operator>=](../standard-library/utility-operators.md#operator_gt__eq)|测试运算符左侧的 pair 对象是否大于或等于右侧的 pair 对象。|  
  
### <a name="structs"></a>结构  
  
|||  
|-|-|  
|[identity](../standard-library/identity-structure.md)||  
|[pair](../standard-library/pair-structure.md)|一种类型，它提供了将两个对象视为单个对象的功能。|  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




