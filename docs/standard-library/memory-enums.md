---
title: "&lt;memory&gt; 枚举 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::pointer_safety
ms.assetid: b9be0a7b-0beb-40b2-8183-911de371c6b9
caps.latest.revision: 11
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: d2f3cf1ec90c7caff5bb3a100d45d69a4a35e01a
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="ltmemorygt-enums"></a>&lt;memory&gt; 枚举
||  
|-|  
|[pointer_safety](#pointer_safety)|  
  
##  <a name="pointer_safety"></a>pointer_safety 枚举  
 由 `get_pointer_safety` 返回的可能值的枚举。  
  
class pointer_safety { relaxed, preferred, strict };  
  
### <a name="remarks"></a>备注  
 作用域 `enum` 定义可以由 `get_pointer_safety``()` 返回的值：  
  
 `relaxed` -- 未安全派生的指针（显然是指向声明或分配对象的指针）将视为与安全派生的指针相同。  
  
 `preferred` -- 与以前一样，但不应取消引用未安全派生的指针。  
  
 `strict` -- 未安全派生的指针可能视为与安全派生的指针不同。  
  
## <a name="see-also"></a>另请参阅  
 [\<memory>](../standard-library/memory.md)




