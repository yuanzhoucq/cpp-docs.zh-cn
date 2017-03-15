---
title: "&lt;forward_list&gt; 运算符 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
caps.latest.revision: 11
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: a560de0a7587b5552fc663bdd2b44734a66b5f73
ms.lasthandoff: 02/24/2017

---
# <a name="ltforwardlistgt-operators"></a>&lt;forward_list&gt; 运算符
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;=](#operator_lt__eq)|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>  operator==  
 测试运算符左侧的转发列表对象是否等于右侧的转发列表对象。  
  
```
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`left`|一个 `forward_list` 类型的对象。|  
|`right`|一个 `forward_list` 类型的对象。|  
  
### <a name="remarks"></a>备注  
 该模板函数重载 `operator==` 以比较模板类 `forward_list` 的两个对象。 该函数返回 `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`。  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>  operator!=  
 测试运算符左侧的转发列表对象是否不等于右侧的转发列表对象。  
  
```
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`left`|一个 `forward_list` 类型的对象。|  
|`right`|一个 `forward_list` 类型的对象。|  
  
### <a name="return-value"></a>返回值  
 如果列表不相等，则为 **true**；如果列表相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 此模板函数返回 `!(left == right)`。  
  
##  <a name="a-nameoperatorlta--operatorlt"></a><a name="operator_lt_"></a>  operator&lt;  
 测试运算符左侧的转发列表对象是否小于右侧的转发列表对象。  
  
```
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`left`|一个 `forward_list` 类型的对象。|  
|`right`|一个 `forward_list` 类型的对象。|  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的列表小于但不等于运算符右侧的列表，则为 `true`，否则为 `false`。  
  
### <a name="remarks"></a>备注  
 该模板函数重载 `operator<` 以比较模板类 `forward_list` 的两个对象。 该函数返回 `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`。  
  
##  <a name="a-nameoperatorlteqa--operatorlt"></a><a name="operator_lt__eq"></a>  operator&lt;=  
 测试运算符左侧的转发列表对象是否小于或等于右侧的转发列表对象。  
  
```
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`left`|一个 `forward_list` 类型的对象。|  
|`right`|一个 `forward_list` 类型的对象。|  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的列表小于或等于运算符右侧的列表，则为 `true`，否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此模板函数返回 `!(right < left)`。  
  
##  <a name="a-nameoperatorgta--operatorgt"></a><a name="operator_gt_"></a>  operator&gt;  
 测试运算符左侧的转发列表对象是否大于右侧的转发列表对象。  
  
```
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`left`|一个 `forward_list` 类型的对象。|  
|`right`|一个 `forward_list` 类型的对象。|  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的列表大于运算符右侧的列表，则为 `true`，否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此模板函数返回 `right < left`。  
  
##  <a name="a-nameoperatorgteqa--operatorgt"></a><a name="operator_gt__eq"></a>  operator&gt;=  
 测试运算符左侧的转发列表对象是否大于或等于右侧的转发列表对象。  
  
```
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`left`|一个 `forward_list` 类型的对象。|  
|`right`|一个 `forward_list` 类型的对象。|  
  
### <a name="return-value"></a>返回值  
 如果运算符左侧的转发列表大于或等于运算符右侧的转发列表，则为 `true`，否则为 `false`。  
  
### <a name="remarks"></a>备注  
 此模板函数返回 `!(left < right)`。  
  
## <a name="see-also"></a>另请参阅  
 [<forward_list>](../standard-library/forward-list.md)




