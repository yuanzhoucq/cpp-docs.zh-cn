---
title: "&lt;system_error&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: []
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
caps.latest.revision: 11
manager: ghogen
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: d5d69831f5157fab1914351de06adf050b74cc93
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="ltsystemerrorgt-operators"></a>&lt;system_error&gt; 运算符
||||  
|-|-|-|  
|[operator!=](#op_neq)|[operator&lt;](#op_lt)|[operator==](#op_eq_eq)|  
  
##  <a name="op_eq_eq"></a>operator==  
 测试运算符左侧的对象是否等于右侧的对象。  
  
```
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`left`|要测试是否相等的对象。|  
|`right`|要测试是否相等的对象。|  
  
### <a name="return-value"></a>返回值  
 如果对象相等，则为 **true**；如果对象不相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 该函数返回 `left.category() == right.category() && left.value() == right.value()`。  
  
##  <a name="op_neq"></a>operator!=  
 测试运算符左侧的对象是否不等于右侧的对象。  
  
```
bool operator!=(const error_code& left,
    const error_condition& right);

bool operator!=(const error_condition& left,
    const error_code& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`left`|要测试是否不相等的对象。|  
|`right`|要测试是否不相等的对象。|  
  
### <a name="return-value"></a>返回值  
 如果 `right` 中传入的对象不等于 `left` 中传入的对象，则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 该函数返回 `!(left == right)`。  
  
##  <a name="op_lt"></a>operator&lt;  
 测试一个对象是否小于要比较的传入对象。  
  
```
template <class _Enum>  
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type right);

template <class _Enum>  
inline bool operator<(
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type left, _Enum right);

template <class _Enum>  
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type right);

template <class _Enum>  
inline bool operator<(
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type left, _Enum right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`left`|要比较的对象。|  
|`right`|要比较的对象。|  
  
### <a name="return-value"></a>返回值  
 如果 `left` 中传入的对象小于 `right` 中传入的对象，则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 该函数测试错误顺序。  
  
## <a name="see-also"></a>另请参阅  
 [<system_error>](../standard-library/system-error.md)




