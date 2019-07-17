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
ms.openlocfilehash: 308fa1a2309ddfda1a02fe6a687360185c1e7c6e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245850"
---
# <a name="errorcategory-class"></a>error_category 类

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

## <a name="members"></a>成员

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
|message[](#message)|返回指定错误代码的名称。|
|[name](#name)|返回类别名称。|
|[system_category](#system)||

### <a name="operators"></a>运算符

|||
|-|-|
|[operator=](#op_as)||
|[operator==](#op_eq_eq)|测试各 `error_category` 对象是否相等。|
|[operator!=](#op_neq)|测试各 `error_category` 对象是否不相等。|
|[operator<](#op_lt)|测试 [error_category](../standard-library/error-category-class.md) 对象是否小于要比较的传入 `error_category` 对象。|

## <a name="default_error_condition"></a> default_error_condition

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

### <a name="equivalent"></a> 等效项

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

*（_c)* \
要比较的 [error_code](../standard-library/error-code-class.md) 对象。

#### <a name="return-value"></a>返回值

**true**如果类别和值相等; 否则为**false**。

#### <a name="remarks"></a>备注

第一个成员函数返回 `*this == _Cond.category() && _Cond.value() == _Errval`。

第二个成员函数返回 `*this == _Code.category() && _Code.value() == _Errval`。

### <a name="generic"></a> generic_category

```cpp
const error_category& generic_category();
```

### <a name="message"></a> 消息

返回指定错误代码的名称。

```cpp
virtual string message(error_code::value_type val) const = 0;
```

#### <a name="parameters"></a>参数

*val*\
要描述的错误代码值。

#### <a name="return-value"></a>返回值

返回的错误代码的描述性名称*val*的类别。

#### <a name="remarks"></a>备注

### <a name="name"></a> 名称

返回类别名称。

```cpp
virtual const char *name() const = 0;
```

#### <a name="return-value"></a>返回值

返回作为以 null 结尾的字节字符串的类别名称。

### <a name="op_as"></a> 运算符 =

```cpp
error_category& operator=(const error_category&) = delete;
```


### <a name="op_eq_eq"></a> 运算符 = =

测试各 `error_category` 对象是否相等。

```cpp
bool operator==(const error_category& right) const;
```

#### <a name="parameters"></a>参数

*右侧*\
要测试是否相等的对象。

#### <a name="return-value"></a>返回值

如果对象相等，则为 **true**；如果对象不相等，则为 **false**。

#### <a name="remarks"></a>备注

此成员运算符将返回 `this == &right`。

### <a name="op_neq"></a> 运算符 ！ =

测试各 `error_category` 对象是否不相等。

```cpp
bool operator!=(const error_category& right) const;
```

#### <a name="parameters"></a>参数

*右侧*\
要测试是否不相等的对象。

#### <a name="return-value"></a>返回值

**true**如果`error_category`对象是否不等于`error_category`传入的对象*右*; 否则为**false**。

#### <a name="remarks"></a>备注

该成员运算符将返回 `(!*this == right)`。

### <a name="op_lt"></a> 运算符&lt;

测试 [error_category](../standard-library/error-category-class.md) 对象是否小于要比较的传入 `error_category` 对象。

```cpp
bool operator<(const error_category& right) const;
```

#### <a name="parameters"></a>参数

*右侧*\
要比较的 `error_category` 对象。

#### <a name="return-value"></a>返回值

如果 `error_category` 对象小于要比较的传入对象 `error_category`，则为 **true**；否则为 **false**。

#### <a name="remarks"></a>备注

该成员运算符将返回 `this < &right`。

### <a name="system"></a> system_category

```cpp
const error_category& system_category();
```

### <a name="value_type"></a> value_type

表示存储的错误代码值的类型。

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>备注

此类型定义是的同义词**int**。
