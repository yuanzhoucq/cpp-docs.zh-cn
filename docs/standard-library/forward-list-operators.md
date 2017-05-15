---
title: "&lt;forward_list&gt; 运算符 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
caps.latest.revision: 11
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: ddf548e760d723bff19b58ac8dfe6ec60acdbbcc
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="ltforwardlistgt-operators"></a>&lt;forward_list&gt; 运算符
||||  
|-|-|-|  
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;=](#op_lt_eq)|[operator==](#op_eq_eq)|  
  
##  <a name="op_eq_eq"></a>  operator==  
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
  
##  <a name="op_neq"></a>  operator!=  
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
  
##  <a name="op_lt"></a>  operator&lt;  
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
  
##  <a name="op_lt_eq"></a>  operator&lt;=  
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
  
##  <a name="op_gt"></a>  operator&gt;  
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
  
##  <a name="op_gt_eq"></a>  operator&gt;=  
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




