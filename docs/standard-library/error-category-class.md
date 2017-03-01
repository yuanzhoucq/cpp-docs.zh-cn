---
title: "error_category 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::error_category
- system_error/std::error_category
- error_category
- std.error_category
dev_langs:
- C++
helpviewer_keywords:
- error_category class
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: 7700ffce8b04f9caad33c08f03f0585c29a43efd
ms.lasthandoff: 02/24/2017

---
# <a name="errorcategory-class"></a>error_category 类
表示描述错误代码类别的对象的抽象、公用基。  
  
## <a name="syntax"></a>语法  
  
```
class error_category;
```  
  
## <a name="remarks"></a>备注  
 两个预定义的对象实现 `error_category`：[generic_category](../standard-library/system-error-functions.md#generic_category) 和 [system_category](../standard-library/system-error-functions.md#system_category)。  
  
### <a name="typedefs"></a>TypeDefs  
  
|||  
|-|-|  
|[value_type](#error_category__value_type)|表示存储的错误代码值的类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[default_error_condition](#error_category__default_error_condition)|存储错误条件对象的错误代码值。|  
|[equivalent](#error_category__equivalent)|返回指定错误对象是否相等的值。|  
|[message](#error_category__message)|返回指定错误代码的名称。|  
|[name](#error_category__name)|返回类别名称。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator==](#error_category__operator_eq_eq)|测试各 `error_category` 对象是否相等。|  
|[operator!=](#error_category__operator_neq)|测试各 `error_category` 对象是否不相等。|  
|[operator<](#error_category__operator_lt_)|测试 [error_category](../standard-library/error-category-class.md) 对象是否小于要比较的传入 `error_category` 对象。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<system_error>  
  
 **命名空间：** std  
  
##  <a name="a-nameerrorcategorydefaulterrorconditiona--errorcategorydefaulterrorcondition"></a><a name="error_category__default_error_condition"></a>  error_category::default_error_condition  
 存储错误条件对象的错误代码值。  
  
```
virtual error_condition default_error_condition(int _Errval) const;
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`_Errval`|要存储在 [error_condition](../standard-library/error-condition-class.md) 中的错误代码值。|  
  
### <a name="return-value"></a>返回值  
 返回 `error_condition(_Errval, *this)`。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameerrorcategoryequivalenta--errorcategoryequivalent"></a><a name="error_category__equivalent"></a>  error_category::equivalent  
 返回指定错误对象是否相等的值。  
  
```
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`_Errval`|要比较的错误代码值。|  
|`_Cond`|要比较的 [error_condition](../standard-library/error-condition-class.md) 对象。|  
|`_Code`|要比较的 [error_code](../standard-library/error-code-class.md) 对象。|  
  
### <a name="return-value"></a>返回值  
 如果类别和值相等则为 `true`；否则为 `false`。  
  
### <a name="remarks"></a>备注  
 第一个成员函数返回 `*this == _Cond.category() && _Cond.value() == _Errval`。  
  
 第二个成员函数返回 `*this == _Code.category() && _Code.value() == _Errval`。  
  
##  <a name="a-nameerrorcategorymessagea--errorcategorymessage"></a><a name="error_category__message"></a>  error_category::message  
 返回指定错误代码的名称。  
  
```
virtual string message(error_code::value_type val) const = 0;
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`val`|要描述的错误代码值。|  
  
### <a name="return-value"></a>返回值  
 为类别返回错误代码 `val` 的描述性名称。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameerrorcategorynamea--errorcategoryname"></a><a name="error_category__name"></a>  error_category::name  
 返回类别名称。  
  
```
virtual const char *name() const = 0;
```  
  
### <a name="return-value"></a>返回值  
 返回作为以 null 结尾的字节字符串的类别名称。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameerrorcategoryoperatoreqeqa--errorcategoryoperator"></a><a name="error_category__operator_eq_eq"></a>  error_category::operator==  
 测试各 `error_category` 对象是否相等。  
  
```
bool operator==(const error_category& right) const;
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`right`|要测试是否相等的对象。|  
  
### <a name="return-value"></a>返回值  
 如果对象相等，则为 **true**；如果对象不相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 此成员运算符将返回 `this == &right`。  
  
##  <a name="a-nameerrorcategoryoperatorneqa--errorcategoryoperator"></a><a name="error_category__operator_neq"></a>  error_category::operator!=  
 测试各 `error_category` 对象是否不相等。  
  
```
bool operator!=(const error_category& right) const;
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`right`|要测试是否不相等的对象。|  
  
### <a name="return-value"></a>返回值  
 如果 `error_category` 对象不等于 `right` 中的传入对象 `error_category`，则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 该成员运算符将返回 `(!*this == right)`。  
  
##  <a name="a-nameerrorcategoryoperatorlta--errorcategoryoperatorlt"></a><a name="error_category__operator_lt_"></a>  error_category::operator&lt;  
 测试 [error_category](../standard-library/error-category-class.md) 对象是否小于要比较的传入 `error_category` 对象。  
  
```
bool operator<(const error_category& right) const;
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`right`|要比较的 `error_category` 对象。|  
  
### <a name="return-value"></a>返回值  
 如果 `error_category` 对象小于要比较的传入对象 `error_category`，则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 该成员运算符将返回 `this < &right`。  
  
##  <a name="a-nameerrorcategoryvaluetypea--errorcategoryvaluetype"></a><a name="error_category__value_type"></a>  error_category::value_type  
 表示存储的错误代码值的类型。  
  
```
typedef int value_type;
```  
  
### <a name="remarks"></a>备注  
 此类型定义是 `int` 的同义词。  
  
## <a name="see-also"></a>另请参阅  
 [<system_error>](../standard-library/system-error.md)




