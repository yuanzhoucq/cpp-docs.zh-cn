---
title: "&lt;forward_list&gt; 函数 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- forward_list/std::swap
ms.assetid: 0d6bc656-7049-4651-a4bd-c9a805e47756
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: ce66354d2377e52043830925c3f4f880de996663
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ltforwardlistgt-functions"></a>&lt;forward_list&gt; 函数
||  
|-|  
|[swap](#swap)|  
  
##  <a name="swap"></a> swap  
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
  
## <a name="see-also"></a>请参阅  
 [<forward_list>](../standard-library/forward-list.md)



