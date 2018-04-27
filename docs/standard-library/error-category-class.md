---
title: error_category 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- system_error/std::error_category
- system_error/std::error_category::value_type
- system_error/std::error_category::default_error_condition
- system_error/std::error_category::equivalent
- system_error/std::error_category::message
- system_error/std::error_category::name
dev_langs:
- C++
helpviewer_keywords:
- std::error_category
- std::error_category::value_type
- std::error_category::default_error_condition
- std::error_category::equivalent
- std::error_category::message
- std::error_category::name
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
caps.latest.revision: 15
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 21e17cb951273cf1a920867154a503f02f4cd760
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="errorcategory-class"></a>error_category 类

表示描述错误代码类别的对象的抽象、公用基。

## <a name="syntax"></a>语法

```cpp
class error_category;
```

## <a name="remarks"></a>备注

两个预定义的对象实现 `error_category`：[generic_category](../standard-library/system-error-functions.md#generic_category) 和 [system_category](../standard-library/system-error-functions.md#system_category)。

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[value_type](#value_type)|表示存储的错误代码值的类型。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[default_error_condition](#default_error_condition)|存储错误条件对象的错误代码值。|
|[equivalent](#equivalent)|返回指定错误对象是否相等的值。|
|[message](#message)|返回指定错误代码的名称。|
|[name](#name)|返回类别名称。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator==](#op_eq_eq)|测试各 `error_category` 对象是否相等。|
|[operator!=](#op_neq)|测试各 `error_category` 对象是否不相等。|
|[operator<](#op_lt)|测试 [error_category](../standard-library/error-category-class.md) 对象是否小于要比较的传入 `error_category` 对象。|

## <a name="requirements"></a>要求

**标头：** \<system_error>

**命名空间：** std

## <a name="default_error_condition"></a>  error_category::default_error_condition

存储错误条件对象的错误代码值。

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`_Errval`|要存储在 [error_condition](../standard-library/error-condition-class.md) 中的错误代码值。|

### <a name="return-value"></a>返回值

返回 `error_condition(_Errval, *this)`。

### <a name="remarks"></a>备注

## <a name="equivalent"></a>  error_category::equivalent

返回指定错误对象是否相等的值。

```cpp
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

## <a name="message"></a>  error_category::message

返回指定错误代码的名称。

```cpp
virtual string message(error_code::value_type val) const = 0;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`val`|要描述的错误代码值。|

### <a name="return-value"></a>返回值

为类别返回错误代码 `val` 的描述性名称。

### <a name="remarks"></a>备注

## <a name="name"></a>  error_category::name

返回类别名称。

```cpp
virtual const char *name() const = 0;
```

### <a name="return-value"></a>返回值

返回作为以 null 结尾的字节字符串的类别名称。

### <a name="remarks"></a>备注

## <a name="op_eq_eq"></a>  error_category::operator==

测试各 `error_category` 对象是否相等。

```cpp
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

## <a name="op_neq"></a>  error_category::operator!=

测试各 `error_category` 对象是否不相等。

```cpp
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

## <a name="op_lt"></a>  error_category::operator&lt;

测试 [error_category](../standard-library/error-category-class.md) 对象是否小于要比较的传入 `error_category` 对象。

```cpp
bool operator<(const error_category& right) const;
```

### <a name="parameters"></a>参数

|参数|描述|
|---------------|-----------------|
|`right`|要比较的 `error_category` 对象。|

### <a name="return-value"></a>返回值

如果 `error_category` 对象小于要比较的传入对象 `error_category`，则为 **true**；否则为 **false**。

### <a name="remarks"></a>备注

该成员运算符将返回 `this < &right`。

## <a name="value_type"></a>  error_category::value_type

表示存储的错误代码值的类型。

```cpp
typedef int value_type;
```

### <a name="remarks"></a>备注

此类型定义是 `int` 的同义词。

## <a name="see-also"></a>请参阅

[<system_error>](../standard-library/system-error.md)<br/>
