---
title: "error_code 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- error_code
- system_error/std::error_code
- system_error/std::error_code::value_type
- system_error/std::error_code::assign
- system_error/std::error_code::category
- system_error/std::error_code::clear
- system_error/std::error_code::default_error_condition
- system_error/std::error_code::message
- system_error/std::error_code::operator bool
dev_langs:
- C++
helpviewer_keywords:
- error_code class
ms.assetid: c09b4a96-cb14-4281-a319-63543f9b2b4a
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.openlocfilehash: 4959d72feaae22cb31a5bc7b6f6aa1b5f5b8be02
ms.lasthandoff: 02/24/2017

---
# <a name="errorcode-class"></a>error_code 类
表示特定于实现的低级别系统错误。  
  
## <a name="syntax"></a>语法  
  
```
class error_code;
```  
  
## <a name="remarks"></a>备注  
 `error_code` 类类型的对象存储错误代码值和指向对象的指针，该对象表示描述所报告的低级别系统错误的错误代码[类别](../standard-library/error-category-class.md)。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[error_code](#error_code__error_code)|构造 `error_code` 类型的对象。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[value_type](#error_code__value_type)|表示存储的错误代码值的类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[assign](#error_code__assign)|向错误代码分配错误代码值和类别。|  
|[category](#error_code__category)|返回错误类别。|  
|[clear](#error_code__clear)|清除错误代码值和类别。|  
|[default_error_condition](#error_code__default_error_condition)|返回默认的错误条件。|  
|[message](#error_code__message)|返回错误代码的名称。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator==](#error_code__operator_eq_eq)|测试各 `error_code` 对象是否相等。|  
|[operator!=](#error_code__operator_neq)|测试各 `error_code` 对象是否不相等。|  
|[operator<](#error_code__operator_lt_)|测试 `error_code` 对象是否小于要比较的传入对象 `error_code`。|  
|[operator=](#error_code__operator_eq)|向 `error_code` 对象分配新的枚举值。|  
|[operator bool](#error_code__operator_bool)|转换 `error_code` 类型的变量。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<system_error>  
  
 **命名空间：** std  
  
##  <a name="error_code__assign"></a>  error_code::assign  
 向错误代码分配错误代码值和类别。  
  
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
  
##  <a name="error_code__category"></a>  error_code::category  
 返回错误类别。  
  
```
const error_category& category() const;
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="error_code__clear"></a>  error_code::clear  
 清除错误代码值和类别。  
  
```
clear();
```  
  
### <a name="remarks"></a>备注  
 此成员函数存储零错误代码值和指向 [generic_category](../standard-library/system-error-functions.md#generic_category) 对象的指针。  
  
##  <a name="error_code__default_error_condition"></a>  error_code::default_error_condition  
 返回默认的错误条件。  
  
```
error_condition default_error_condition() const;
```  
  
### <a name="return-value"></a>返回值  
 [default_error_condition](../standard-library/error-category-class.md#error_category__default_error_condition) 指定的 [error_condition](../standard-library/error-condition-class.md)。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 `category().default_error_condition(value())`。  
  
##  <a name="error_code__error_code"></a>  error_code::error_code  
 构造 `error_code` 类型的对象。  
  
```
error_code();

error_code(value_type val, const error_category& _Cat);

template <class _Enum>
error_code(_Enum _Errcode,
    typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type* = 0);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`val`|要存储在 `error_code` 中的错误代码值。|  
|`_Cat`|要存储在 `error_code` 中的错误类别。|  
|`_Errcode`|要存储在 `error_code` 中的枚举值。|  
  
### <a name="remarks"></a>备注  
 第一个构造函数存储零错误代码值和指向 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指针。  
  
 第二个构造函数存储 `val` 作为错误代码值和指向 [error_category](http://msdn.microsoft.com/en-us/6fe57a15-63a1-4e79-8af4-6738e43e19c8) 的指针。  
  
 第三个构造函数存储 `(value_type)_Errcode` 作为错误代码值和指向 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指针。  
  
##  <a name="error_code__message"></a>  error_code::message  
 返回错误代码的名称。  
  
```
string message() const;
```  
  
### <a name="return-value"></a>返回值  
 表示错误代码名称的 `string`。  
  
### <a name="remarks"></a>备注  
 此成员函数返回 `category().message(value())`。  
  
##  <a name="error_code__operator_eq_eq"></a>  error_code::operator==  
 测试各 `error_code` 对象是否相等。  
  
```
bool operator==(const error_code& right) const;
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`right`|要测试是否相等的对象。|  
  
### <a name="return-value"></a>返回值  
 如果对象相等，则为 **true**；如果对象不相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 该成员运算符将返回 `category() == right.category() && value == right.value()`。  
  
##  <a name="error_code__operator_neq"></a>  error_code::operator!=  
 测试各 `error_code` 对象是否不相等。  
  
```
bool operator!=(const error_code& right) const;
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`right`|要测试是否不相等的对象。|  
  
### <a name="return-value"></a>返回值  
 如果 `error_code` 对象不等于 `right` 中的传入对象 `error_code`，则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 该成员运算符将返回 `!(*this == right)`。  
  
##  <a name="error_code__operator_lt_"></a>  error_code::operator&lt;  
 测试 [error_code](http://msdn.microsoft.com/en-us/09c6ef90-b6f8-430a-b584-e168716c7e31) 对象是否小于要比较的传入 `error_code` 对象。  
  
```
bool operator<(const error_code& right) const;
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`right`|要比较的 error_code 对象。|  
  
### <a name="return-value"></a>返回值  
 如果 `error_code` 对象小于要比较的传入对象 `error_code`，则为 **true**；否则为 **false**。  
  
### <a name="remarks"></a>备注  
 该成员运算符将返回 `category() < right.category() || category() == right.category() && value < right.value()`。  
  
##  <a name="error_code__operator_eq"></a>  error_code::operator=  
 向 [error_code](http://msdn.microsoft.com/en-us/09c6ef90-b6f8-430a-b584-e168716c7e31) 对象分配新的枚举值。  
  
```
template <class _Enum>
typename enable_if<is_error_code_enum<_Enum>::value,
    error_code>::type&
 operator=(_Enum _Errcode);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`_Errcode`|要向 `error_code` 对象分配的枚举值。|  
  
### <a name="return-value"></a>返回值  
 对正在通过成员函数向其分配新枚举值的 `error_code` 对象的引用。  
  
### <a name="remarks"></a>备注  
 成员运算符存储 `(value_type)_Errcode` 作为错误代码值和指向 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指针。 它将返回 `*this`。  
  
##  <a name="error_code__operator_bool"></a>  error_code::operator bool  
 转换 `error_code` 类型的变量。  
  
```
explicit operator bool() const;
```  
  
### <a name="return-value"></a>返回值  
 `error_code` 对象的布尔值。  
  
### <a name="remarks"></a>备注  
 仅在[值](#error_code__value)不等于零时，此运算符才返回可转换为 `true` 的值。 返回类型只能转换为 `bool`，而不能转换为 `void *` 或其他已知的标量类型。  
  
##  <a name="error_code__value"></a>  error_code::value  
 返回存储的错误代码值。  
  
```
value_type value() const;
```  
  
### <a name="return-value"></a>返回值  
 [value_type](#error_code__value_type) 类型的已存储错误代码值。  
  
### <a name="remarks"></a>备注  
  
##  <a name="error_code__value_type"></a>  error_code::value_type  
 表示存储的错误代码值的类型。  
  
```
typedef int value_type;
```  
  
### <a name="remarks"></a>备注  
 此类型定义是 `int` 的同义词。  
  
## <a name="see-also"></a>另请参阅  
 [error_category 类](../standard-library/error-category-class.md)   
 [<system_error>](../standard-library/system-error.md)




