---
title: "&lt;forward_list&gt; 函数 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: b1c8cbb3a8dbbf7f6c14400f531e7ab40a2c84f6
ms.lasthandoff: 02/24/2017

---
# <a name="ltforwardlistgt-functions"></a>&lt;forward_list&gt; 函数
||  
|-|  
|[swap](#swap)|  
  
##  <a name="a-nameswapa--swap"></a><a name="swap"></a> swap  
 交换两个转发列表的元素。  
  
```
void swap(
    forward_list <Type, Allocator>& left,
    forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`left`|一个 `forward_list` 类型的对象。|  
|`right`|一个 `forward_list` 类型的对象。|  
  
### <a name="remarks"></a>备注  
 该模板函数执行 `left.swap(right)`。  
  
## <a name="see-also"></a>另请参阅  
 [<forward_list>](../standard-library/forward-list.md)




