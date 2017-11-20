---
title: "error_condition 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- system_error/std::error_condition
- system_error/std::error_condition::value_type
- system_error/std::error_condition::assign
- system_error/std::error_condition::category
- system_error/std::error_condition::clear
- system_error/std::error_condition::message
- system_error/std::error_condition::operator bool
dev_langs: C++
helpviewer_keywords:
- std::error_condition
- std::error_condition::value_type
- std::error_condition::assign
- std::error_condition::category
- std::error_condition::clear
- std::error_condition::message
- 
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c8109db3a6607abd1792485c93a59795d432f824
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="errorcondition-class"></a>error_condition 类
表示用户定义的错误代码。  
  
## <a name="syntax"></a>语法  
  
```
class error_condition;
```  
  
## <a name="remarks"></a>备注  
 `error_condition` 类型的对象存储错误代码值和指向对象的指针，该对象表示所报告的用户定义的错误所使用的错误代码[类别](../standard-library/error-category-class.md)。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[error_condition](#error_condition)|构造 `error_condition` 类型的对象。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[value_type](#value_type)|表示存储的错误代码值的类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[assign](#assign)|向错误条件分配错误代码值和类别。|  
|[category](#category)|返回错误类别。|  
|[clear](#clear)|清除错误代码值和类别。|  
|[message](#message)|返回错误代码的名称。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator==](#op_eq_eq)|测试各 `error_condition` 对象是否相等。|  
|[operator!=](#op_neq)|测试各 `error_condition` 对象是否不相等。|  
|[operator<](#op_lt)|测试 `error_condition` 对象是否小于要比较的传入对象 `error_code`。|  
|[operator=](#op_eq)|向 `error_condition` 对象分配新的枚举值。|  
|[operator bool](#op_bool)|转换 `error_condition` 类型的变量。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<system_error>  
  
 **命名空间：** std  
  
##  <a name="assign"></a>  error_condition::assign  
 向错误条件分配错误代码值和类别。  
  
```
void assign(value_type val, const error_category& _Cat);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`val`|要存储在 `error_code` 中的错误代码值。|  
|`_Cat`|要存储在 `error_code` 中的错误类别。|  
  
### <a name="remarks"></a>备注  
 此成员函数存储 `val` 作为错误代码值和指向 `_Cat` 的指针。  
  
##  <a name="category"></a>  error_condition::category  
 返回错误类别。  
  
```
const error_category& category() const;
```  
  
### <a name="return-value"></a>返回值  
 对存储的错误类别的引用  
  
### <a name="remarks"></a>备注  
  
##  <a name="clear"></a>  error_condition::clear  
 清除错误代码值和类别。  
  
```
clear();
```  
  
### <a name="remarks"></a>备注  
 此成员函数存储零错误代码值和指向 [generic_category](../standard-library/system-error-functions.md#generic_category) 对象的指针。  
  
##  <a name="error_condition"></a>  error_condition::error_condition  
 构造 `error_condition` 类型的对象。  
  
```
error_condition();

error_condition(value_type val, const error_category& _Cat);

template <class _Enum>
error_condition(_Enum _Errcode,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_code>::type* = 0);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`val`|要存储在 `error_condition` 中的错误代码值。|  
|`_Cat`|要存储在 `error_condition` 中的错误类别。|  
|`_Errcode`|要存储在 `error_condition` 中的枚举值。|  
  
### <a name="remarks"></a>备注  
 第一个构造函数存储零错误代码值和指向 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指针。  
  
 第二个构造函数存储 `val` 作为错误代码值和指向 [error_category](http://msdn.microsoft.com/en-us/6fe57a15-63a1-4e79-8af4-6738e43e19c8) 的指针。  
  
 第三个构造函数存储 `(value_type)_Errcode` 作为错误代码值和指向 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指针。  
  
##  <a name="message"></a>  error_condition::message  
 返回错误代码的名称。  
  
```
string message() const;
```  
  
### <a name="return-value"></a>返回值  
 表示错误代码名称的 `string`。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 `category().message(value())`。  
  
##  <a name="op_eq_eq"></a>  error_condition::operator==  
 测试各 `error_condition` 对象是否相等。  
  
```
bool operator==(const error_condition& right) const;
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`right`|要测试是否相等的对象。|  
  
### <a name="return-value"></a>返回值  
 如果对象相等，则为 **true**；如果对象不相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 该成员运算符将返回 `category() == right.category() && value == right.value()`。  
  
##  <a name="op_neq"></a>  error_condition::operator!=  
 测试各 `error_condition` 对象是否不相等。  
  
```
bool operator!=(const error_condition& right) const;
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`right`|要测试是否不相等的对象。|  
  
### <a name="return-value"></a>返回值  
 如果 `error_condition` 对象不等于 `right` 中的传入对象 `error_condition`，则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 该成员运算符将返回 `!(*this == right)`。  
  
##  <a name="op_lt"></a>  error_condition::operator&lt;  
 测试 `error_condition` 对象是否小于要比较的传入对象 `error_code`。  
  
```
bool operator<(const error_condition& right) const;
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`right`|要比较的 `error_condition` 对象。|  
  
### <a name="return-value"></a>返回值  
 如果 `error_condition` 对象小于要比较的传入对象 `error_condition`，则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 该成员运算符将返回 `category() < right.category() || category() == right.category() && value < right.value()`。  
  
##  <a name="op_eq"></a>  error_condition::operator=  
 向 `error_condition` 对象分配新的枚举值。  
  
```
template <class _Enum>
error_condition(_Enum error,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_condition>::type&
 operator=(Enum _Errcode);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`_Errcode`|要向 `error_condition` 对象分配的枚举值。|  
  
### <a name="return-value"></a>返回值  
 对正在通过成员函数向其分配新枚举值的 `error_condition` 对象的引用。  
  
### <a name="remarks"></a>备注  
 成员运算符存储 `(value_type)error` 作为错误代码值和指向 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指针。 它将返回 `*this`。  
  
##  <a name="op_bool"></a>  error_condition::operator bool  
 转换 `error_condition` 类型的变量。  
  
```
explicit operator bool() const;
```  
  
### <a name="return-value"></a>返回值  
 `error_condition` 对象的布尔值。  
  
### <a name="remarks"></a>备注  
 仅在[值](#value)不等于零时，此运算符才返回可转换为 `true` 的值。 返回类型只能转换为 `bool`，而不能转换为 `void *` 或其他已知的标量类型。  
  
##  <a name="value"></a>  error_condition::value  
 返回存储的错误代码值。  
  
```
value_type value() const;
```  
  
### <a name="return-value"></a>返回值  
 [value_type](#value_type) 类型的已存储错误代码值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="value_type"></a>  error_condition::value_type  
 表示存储的错误代码值的类型。  
  
```
typedef int value_type;
```  
  
### <a name="remarks"></a>备注  
 该类型定义是 `int` 的同义词。  
  
## <a name="see-also"></a>另请参阅  
 [error_category 类](../standard-library/error-category-class.md)   
 [<system_error>](../standard-library/system-error.md)



