---
title: error_category 类
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_category
- system_error/std::error_category::value_type
- system_error/std::error_category::default_error_condition
- system_error/std::error_category::equivalent
- system_error/std::error_category::message
- system_error/std::error_category::name
helpviewer_keywords:
- std::error_category
- std::error_category::value_type
- std::error_category::default_error_condition
- std::error_category::equivalent
- std::error_category::message
- std::error_category::name
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
ms.openlocfilehash: 3ed2eceb60c2efa78181faea58a256b0e35d489f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076613"
---
# <a name="error_category-class"></a>error_category 类

表示描述错误代码类别的对象的抽象、公用基。

## <a name="syntax"></a>语法

```cpp
class error_category;

constexpr error_category() noexcept;
virtual ~error_category();
error_category(const error_category&) = delete
```

## <a name="remarks"></a>备注

两个预定义的对象实现 `error_category`：[generic_category](../standard-library/system-error-functions.md#generic_category) 和 [system_category](../standard-library/system-error-functions.md#system_category)。

## <a name="members"></a>Members

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[value_type](#value_type)|表示存储的错误代码值的类型。|

### <a name="functions"></a>函数

|||
|-|-|
|[default_error_condition](#default_error_condition)|存储错误条件对象的错误代码值。|
|[equivalent](#equivalent)|返回指定错误对象是否相等的值。|
|[generic_category](#generic)||
|[message](#message)|返回指定错误代码的名称。|
|[name](#name)|返回类别名称。|
|[system_category](#system)||

### <a name="operators"></a>运算符

|||
|-|-|
|[operator=](#op_as)||
|[operator==](#op_eq_eq)|测试各 `error_category` 对象是否相等。|
|[operator!=](#op_neq)|测试各 `error_category` 对象是否不相等。|
|[operator<](#op_lt)|测试 [error_category](../standard-library/error-category-class.md) 对象是否小于要比较的传入 `error_category` 对象。|

## <a name="default_error_condition"></a><a name="default_error_condition"></a>default_error_condition

存储错误条件对象的错误代码值。

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>参数

*_Errval*\
要存储在 [error_condition](../standard-library/error-condition-class.md) 中的错误代码值。

### <a name="return-value"></a>返回值

返回 `error_condition(_Errval, *this)`。

### <a name="remarks"></a>备注

### <a name="equivalent"></a><a name="equivalent"></a>项

返回指定错误对象是否相等的值。

```cpp
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```

#### <a name="parameters"></a>参数

*_Errval*\
要比较的错误代码值。

*_Cond*\
要比较的 [error_condition](../standard-library/error-condition-class.md) 对象。

*_Code*\
要比较的 [error_code](../standard-library/error-code-class.md) 对象。

#### <a name="return-value"></a>返回值

如果类别和值相等，则**为 true** ;否则**为 false**。

#### <a name="remarks"></a>备注

第一个成员函数返回 `*this == _Cond.category() && _Cond.value() == _Errval`。

第二个成员函数返回 `*this == _Code.category() && _Code.value() == _Errval`。

### <a name="generic_category"></a><a name="generic"></a>generic_category

```cpp
const error_category& generic_category();
```

### <a name="message"></a><a name="message"></a>消息

返回指定错误代码的名称。

```cpp
virtual string message(error_code::value_type val) const = 0;
```

#### <a name="parameters"></a>参数

*val*\
要描述的错误代码值。

#### <a name="return-value"></a>返回值

返回类别的错误代码*val*的描述性名称。

#### <a name="remarks"></a>备注

### <a name="name"></a><a name="name"></a>路径名

返回类别名称。

```cpp
virtual const char *name() const = 0;
```

#### <a name="return-value"></a>返回值

返回作为以 null 结尾的字节字符串的类别名称。

### <a name="operator"></a><a name="op_as"></a>operator =

```cpp
error_category& operator=(const error_category&) = delete;
```

### <a name="operator"></a><a name="op_eq_eq"></a>operator = =

测试各 `error_category` 对象是否相等。

```cpp
bool operator==(const error_category& right) const;
```

#### <a name="parameters"></a>参数

*right*\
要测试是否相等的对象。

#### <a name="return-value"></a>返回值

如果对象相等，则为 **true**；如果对象不相等，则为 **false**。

#### <a name="remarks"></a>备注

此成员运算符将返回 `this == &right`。

### <a name="operator"></a><a name="op_neq"></a>operator！ =

测试各 `error_category` 对象是否不相等。

```cpp
bool operator!=(const error_category& right) const;
```

#### <a name="parameters"></a>参数

*right*\
要测试是否不相等的对象。

#### <a name="return-value"></a>返回值

如果 `error_category` 对象与*右*传递的 `error_category` 对象不相等，**则为 true** ;否则**为 false**。

#### <a name="remarks"></a>备注

该成员运算符将返回 `(!*this == right)`。

### <a name="operatorlt"></a><a name="op_lt"></a> 运算符&lt;

测试 [error_category](../standard-library/error-category-class.md) 对象是否小于要比较的传入 `error_category` 对象。

```cpp
bool operator<(const error_category& right) const;
```

#### <a name="parameters"></a>参数

*right*\
要比较的 `error_category` 对象。

#### <a name="return-value"></a>返回值

如果 `error_category` 对象小于要比较的传入对象 `error_category`，则为 **true**；否则为 **false**。

#### <a name="remarks"></a>备注

该成员运算符将返回 `this < &right`。

### <a name="system_category"></a><a name="system"></a>system_category

```cpp
const error_category& system_category();
```

### <a name="value_type"></a><a name="value_type"></a> value_type

表示存储的错误代码值的类型。

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>备注

此类型定义是**int**的同义词。
