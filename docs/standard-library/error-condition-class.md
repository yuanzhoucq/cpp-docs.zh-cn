---
title: error_condition 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- system_error/std::error_condition
- system_error/std::error_condition::value_type
- system_error/std::error_condition::assign
- system_error/std::error_condition::category
- system_error/std::error_condition::clear
- system_error/std::error_condition::message
- system_error/std::error_condition::operator bool
dev_langs:
- C++
helpviewer_keywords:
- std::error_condition
- std::error_condition::value_type
- std::error_condition::assign
- std::error_condition::category
- std::error_condition::clear
- std::error_condition::message
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d93ebf1bdc679c27d79392bf75576f47e8844a27
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709626"
---
# <a name="errorcondition-class"></a>error_condition 类

表示用户定义的错误代码。

## <a name="syntax"></a>语法

```cpp
class error_condition;
```

## <a name="remarks"></a>备注

`error_condition` 类型的对象存储错误代码值和指向对象的指针，该对象表示所报告的用户定义的错误所使用的错误代码[类别](../standard-library/error-category-class.md)。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[error_condition](#error_condition)|构造 `error_condition` 类型的对象。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[value_type](#value_type)|表示存储的错误代码值的类型。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[assign](#assign)|向错误条件分配错误代码值和类别。|
|[category](#category)|返回错误类别。|
|[clear](#clear)|清除错误代码值和类别。|
|[message](#message)|返回错误代码的名称。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator==](#op_eq_eq)|测试各 `error_condition` 对象是否相等。|
|[operator!=](#op_neq)|测试各 `error_condition` 对象是否不相等。|
|[operator<](#op_lt)|测试 `error_condition` 对象是否小于要比较的传入对象 `error_code`。|
|[operator=](#op_eq)|向 `error_condition` 对象分配新的枚举值。|
|[operator bool](#op_bool)|转换 `error_condition` 类型的变量。|

## <a name="requirements"></a>要求

**标头：** \<system_error>

**命名空间：** std

## <a name="assign"></a>  error_condition::assign

向错误条件分配错误代码值和类别。

```cpp
void assign(value_type val, const error_category& _Cat);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*val*|要存储在 `error_code` 中的错误代码值。|
|*则*|要存储在 `error_code` 中的错误类别。|

### <a name="remarks"></a>备注

此成员函数存储*val*作为错误代码值和指向*则*。

## <a name="category"></a>  error_condition::category

返回错误类别。

```cpp
const error_category& category() const;
```

### <a name="return-value"></a>返回值

对存储的错误类别的引用

### <a name="remarks"></a>备注

## <a name="clear"></a>  error_condition::clear

清除错误代码值和类别。

```cpp
clear();
```

### <a name="remarks"></a>备注

此成员函数存储零错误代码值和指向 [generic_category](../standard-library/system-error-functions.md#generic_category) 对象的指针。

## <a name="error_condition"></a>  error_condition::error_condition

构造 `error_condition` 类型的对象。

```cpp
error_condition();

error_condition(value_type val, const error_category& _Cat);

template <class _Enum>
error_condition(_Enum _Errcode,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_code>::type* = 0);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*val*|要存储在 `error_condition` 中的错误代码值。|
|*则*|要存储在 `error_condition` 中的错误类别。|
|*_Errcode*|要存储在 `error_condition` 中的枚举值。|

### <a name="remarks"></a>备注

第一个构造函数存储零错误代码值和指向 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指针。

第二个构造函数存储*val*作为错误代码值和指向[error_category](../standard-library/error-category-class.md)。

第三个构造函数存储 `(value_type)_Errcode` 作为错误代码值和指向 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指针。

## <a name="message"></a>  error_condition::message

返回错误代码的名称。

```cpp
string message() const;
```

### <a name="return-value"></a>返回值

表示错误代码名称的 `string`。

### <a name="remarks"></a>备注

此成员函数返回 `category().message(value())`。

## <a name="op_eq_eq"></a>  error_condition::operator==

测试各 `error_condition` 对象是否相等。

```cpp
bool operator==(const error_condition& right) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*right*|要测试是否相等的对象。|

### <a name="return-value"></a>返回值

如果对象相等，则为 **true**；如果对象不相等，则为 **false**。

### <a name="remarks"></a>备注

该成员运算符将返回 `category() == right.category() && value == right.value()`。

## <a name="op_neq"></a>  error_condition::operator!=

测试各 `error_condition` 对象是否不相等。

```cpp
bool operator!=(const error_condition& right) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*right*|要测试是否不相等的对象。|

### <a name="return-value"></a>返回值

**true**如果`error_condition`对象是否不等于`error_condition`传入的对象*右*; 否则为**false**。

### <a name="remarks"></a>备注

该成员运算符将返回 `!(*this == right)`。

## <a name="op_lt"></a>  error_condition::operator&lt;

测试 `error_condition` 对象是否小于要比较的传入对象 `error_code`。

```cpp
bool operator<(const error_condition& right) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*right*|要比较的 `error_condition` 对象。|

### <a name="return-value"></a>返回值

如果 `error_condition` 对象小于要比较的传入对象 `error_condition`，则为 **true**；否则为 **false**。

### <a name="remarks"></a>备注

该成员运算符将返回 `category() < right.category() || category() == right.category() && value < right.value()`。

## <a name="op_eq"></a>  error_condition::operator=

向 `error_condition` 对象分配新的枚举值。

```cpp
template <class _Enum>
error_condition(_Enum error,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_condition>::type&
    operator=(Enum _Errcode);
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|*_Errcode*|要向 `error_condition` 对象分配的枚举值。|

### <a name="return-value"></a>返回值

对正在通过成员函数向其分配新枚举值的 `error_condition` 对象的引用。

### <a name="remarks"></a>备注

成员运算符存储 `(value_type)error` 作为错误代码值和指向 [generic_category](../standard-library/system-error-functions.md#generic_category) 的指针。 它将返回 `*this`。

## <a name="op_bool"></a>  error_condition::operator bool

转换 `error_condition` 类型的变量。

```cpp
explicit operator bool() const;
```

### <a name="return-value"></a>返回值

`error_condition` 对象的布尔值。

### <a name="remarks"></a>备注

该运算符将返回一个值可转换为 **，则返回 true**仅当[值](#value)不等于零。 返回类型是转换仅为**bool**不为`void *`或其他已知的标量类型。

## <a name="value"></a>  error_condition::value

返回存储的错误代码值。

```cpp
value_type value() const;
```

### <a name="return-value"></a>返回值

[value_type](#value_type) 类型的已存储错误代码值。

### <a name="remarks"></a>备注

## <a name="value_type"></a>  error_condition::value_type

表示存储的错误代码值的类型。

```cpp
typedef int value_type;
```

### <a name="remarks"></a>备注

类型定义是的同义词**int**。

## <a name="see-also"></a>请参阅

[error_category 类](../standard-library/error-category-class.md)<br/>
[<system_error>](../standard-library/system-error.md)<br/>
