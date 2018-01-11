---
title: '&lt;map&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: <map>
dev_langs: C++
helpviewer_keywords: map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6256f5a900872f967c8ea4c069098bd8eeeb733d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ltmapgt"></a>&lt;map&gt;
定义容器模板类 map 和 multimap 及其支持的模板。  
  
## <a name="syntax"></a>语法  
  
```  
#include <map>  
  
```  
  
## <a name="members"></a>成员  
  
### <a name="operators"></a>运算符  
  
|Map 版本|Multimap 版本|描述|  
|-----------------|----------------------|-----------------|  
|[operator!= (map)](../standard-library/map-operators.md#op_neq)|[operator!= (multimap)](../standard-library/map-operators.md#op_neq)|测试运算符左侧和右侧的 map 或 multimap 对象是否不相等。|  
|[operator< (map)](../standard-library/map-operators.md#op_eq_eq)|[operator< (multimap)](../standard-library/map-operators.md#op_eq_eq)|测试运算符左侧的 map 或 multimap 对象是否小于右侧的 map 或 multimap 对象。|  
|[operator<= (map)](../standard-library/map-operators.md#op_lt)|[operator\<= (multimap)](../standard-library/map-operators.md#op_lt)|测试运算符左侧的 map 或 multimap 对象是否小于或等于右侧的 map 或 multimap 对象。|  
|[operator== (map)](../standard-library/map-operators.md#op_eq_eq)|[operator== (multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|测试运算符左侧和右侧的 map 或 multimap 对象是否相等。|  
|[operator> (map)](../standard-library/map-operators.md#op_gt)|[operator> (multimap)](../standard-library/map-operators.md#op_gt_multimap)|测试运算符左侧的 map 或 multimap 对象是否大于右侧的 map 或 multimap 对象。|  
|[operator>= (map)](../standard-library/map-operators.md#op_gt_eq)|[operator>= (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|测试运算符左侧的 map 或 multimap 对象是否大于或等于右侧的 map 或 multimap 对象。|  
  
### <a name="specialized-template-functions"></a>专用化模板函数  
  
|Map 版本|Multimap 版本|描述|  
|-----------------|----------------------|-----------------|  
|[swap (map)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap_multimap)|交换两个 map 或 multimap 的元素。|  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[value_compare 类](../standard-library/value-compare-class-map.md)|提供一个函数对象，它能通过比较其键的值来比较映射的元素，以确定其在映射中的相对顺序。|  
|[map 类](../standard-library/map-class.md)|用于存储和检索集合中的数据，此集合中每个元素都有用于自动排列数据的唯一键。|  
|[multimap 类](../standard-library/multimap-class.md)|用于存储和检索集合中的数据，此集合中每个元素都有一个用于自动排列数据的键，且这些键不需要具有唯一值。|  
  
## <a name="see-also"></a>请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)



