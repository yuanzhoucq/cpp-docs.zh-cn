---
title: "&lt;allocators&gt; 运算符 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 6185bc74c530d6327d0ac37a5425a7653ba36841
ms.lasthandoff: 02/24/2017

---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; 运算符
|||  
|-|-|  
|[operator!=](#operator_neq)|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>  operator!=  
 测试指定类的分配器对象之间是否不相等。  
  
```
template <class Type, class Sync>  
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`left`|要测试是否不相等的其中一个分配器对象。|  
|`right`|要测试是否不相等的其中一个分配器对象。|  
  
### <a name="return-value"></a>返回值  
 如果分配器对象不相等，则为 **true**；如果分配器对象相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 模板运算符返回 `!(left == right)`。  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>  operator==  
 测试指定类的分配器对象之间是否相等。  
  
```
template <class Type, class Sync>  
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`left`|要测试是否相等的其中一个分配器对象。|  
|`right`|要测试是否相等的其中一个分配器对象。|  
  
### <a name="return-value"></a>返回值  
 如果分配器对象相等，则为 **true**；如果分配器对象不相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 此模板运算符返回 `left.equals(right)`。  
  
## <a name="see-also"></a>另请参阅  
 [\<allocators>](../standard-library/allocators-header.md)




