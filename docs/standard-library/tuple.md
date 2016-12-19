---
title: "&lt; 元组 &gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<tuple>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tuple 标头 [TR1]"
ms.assetid: e4ef5c2d-318b-44f6-8bce-fce4ecd796a3
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt; 元组 &gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义的模板 `tuple` 其实例保存的不同类型的对象。  
  
## <a name="syntax"></a>语法  
  
```  
#include <tuple>  
```  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[元组](../standard-library/tuple-class.md)|包装元素的固定长度序列。|  
|[tuple_element 类](../standard-library/tuple-element-class-tuple.md)|包装的 `tuple` 类型的元素。|  
|[tuple_size 类](../standard-library/tuple-size-class-tuple.md)|包装 `tuple` 元素计数。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[运算符 = =](../Topic/%3Ctuple%3E%20operators.md#operator_eq_eq)|比较 `tuple` 对象，相等|  
|[运算符 ！ =](../Topic/%3Ctuple%3E%20operators.md#operator_neq)|比较 `tuple` 对象，不等于|  
|[运算符 <](../Topic/%3Ctuple%3E%20operators.md#operator_lt_)|比较 `tuple` 对象，小于|  
|[运算符 < =](../Topic/%3Ctuple%3E%20operators.md#operator_lt__eq)|比较 `tuple` 对象，小于或等于|  
|[运算符 >](../Topic/%3Ctuple%3E%20operators.md#operator_gt_)|比较 `tuple` 对象，大于|  
|[运算符 > =](../Topic/%3Ctuple%3E%20operators.md#operator_gt__eq)|比较 `tuple` 对象，大于或等于|  
  
### <a name="functions"></a>函数  
  
|||  
|-|-|  
|[获取](../Topic/%3Ctuple%3E%20functions.md#get_function)|从 `tuple` 对象获取一个元素。|  
|[make_tuple](../Topic/%3Ctuple%3E%20functions.md#make_tuple_function)|使 `tuple` 从元素值。|  
|[平分](../Topic/%3Ctuple%3E%20functions.md#tie_function)|使 `tuple` 从元素引用。|  
  
## <a name="see-also"></a>请参阅  
 [\< 数组>](../standard-library/array.md)

