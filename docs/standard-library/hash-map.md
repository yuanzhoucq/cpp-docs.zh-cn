---
title: '&lt;hash_map&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.<hash_map>
- <hash_map>
- std::<hash_map>
dev_langs:
- C++
helpviewer_keywords:
- hash_map header
ms.assetid: 0765708a-a668-42a2-9800-654c857bdcc2
caps.latest.revision: 27
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 3f9a4705d946831ddee15116676fde9e433288f7
ms.lasthandoff: 02/24/2017

---
# <a name="lthashmapgt"></a>&lt;hash_map&gt;
> [!NOTE]
>  此标头已废弃不用。 替代项为 [<unordered_map>](../standard-library/unordered-map.md)。  
  
 定义容器模板类 hash_map 和 hash_multimap 及其支持的模板。  
  
 在 Visual C++ .NET 2003 中，<hash_map> 和 <hash_set> 头文件的成员不再出现在 std 命名空间中，而是移入了 stdext 命名空间。 有关详细信息，请参见 [stdext 命名空间](../standard-library/stdext-namespace.md)。  
  
## <a name="syntax"></a>语法  
  
```  
#include <hash_map>  
  
```  
  
### <a name="operators"></a>运算符  
  
|Hash_map 版本|Hash_multimap 版本|描述|  
|-----------------------|----------------------------|-----------------|  
|[operator!= (hash_map)](../standard-library/hash-map-operators.md#operator_neq__hash_map_)|[operator!= (hash_multimap)](../standard-library/hash-map-operators.md#operator_neq)|测试运算符左侧和右侧的 hash_map 或 hash_multimap 对象是否不相等。|  
|[operator== (hash_map)](http://msdn.microsoft.com/en-us/f933cb1c-934d-43f5-aa9e-0b325eb95b85)|[operator== (hash_multimap)](http://msdn.microsoft.com/en-us/3fa378b1-0250-4e3f-a130-dc14103fc5e9)|测试运算符左侧和右侧的 hash_map 或 hash_multimap 对象是否相等。|  
  
### <a name="specialized-template-functions"></a>专用化模板函数  
  
|Hash_map 版本|Hash_multimap 版本|说明|  
|-----------------------|----------------------------|-----------------|  
|[swap (hash_map)](../standard-library/hash-map-class.md#hash_map__swap)|[swap (hash_multimap)](../standard-library/hash-multimap-class.md#hash_multimap__swap)|交换两个 hash_map 或 hash_multimap 的元素。|  
  
### <a name="classes"></a>类  
  
|||  
|-|-|  
|[hash_compare 类](../standard-library/hash-compare-class.md)|描述了一个对象，任何哈希关联容器（hash_map、hash_multimap、hash_set 或 hash_multiset）都可将该对象用作默认的 **Traits** 参数对象，以对其所包含的元素进行排序和哈希处理。|  
|[value_compare 类](../standard-library/value-compare-class.md)|提供一个函数对象，该对象能通过比较 hash_map 元素的键值来比较这些元素，以确定其在 hash_map 中的相对顺序。|  
|[hash_map 类](../standard-library/hash-map-class.md)|用于存储和快速检索集合中的数据，集合中的每个元素都是具有排序键和关联数据值的元素对，而排序键的值是唯一的。|  
|[hash_multimap 类](../standard-library/hash-multimap-class.md)|用于存储和快速检索集合中的数据，集合中的每个元素都是具有排序键和关联数据值的元素对，而排序键的值不需要具有唯一性。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<hash_map>  
  
 **命名空间：** stdext  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [C++ 标准库中的线程安全性](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)




