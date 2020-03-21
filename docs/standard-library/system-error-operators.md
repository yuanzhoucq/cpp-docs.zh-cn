---
title: '&lt;system_error&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 8631cae146a311f1890583900b564471d5a80958
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076263"
---
# <a name="ltsystem_errorgt-operators"></a>&lt;system_error&gt; 运算符

## <a name="operator"></a><a name="op_eq_eq"></a>operator = =

测试运算符左侧的对象是否等于右侧的对象。

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);

bool operator==(const error_condition& left,
    const error_condition& right);
```

### <a name="parameters"></a>parameters

*左*\
要测试是否相等的对象。

*right*\
要测试是否相等的对象。

### <a name="return-value"></a>返回值

如果对象相等，则为 **true**；如果对象不相等，则为 **false**。

### <a name="remarks"></a>备注

该函数返回 `left.category() == right.category() && left.value() == right.value()`。

## <a name="operator"></a><a name="op_neq"></a>operator！ =

测试运算符左侧的对象是否不等于右侧的对象。

```cpp
bool operator!=(const error_code& left, const error_condition& right);
bool operator!=(const error_condition& left, const error_code& right);
bool operator!=(const error_code& left, const error_code& right);
bool operator!=(const error_condition& left, const error_condition& right);
```

### <a name="parameters"></a>parameters

*左*\
要测试是否不相等的对象。

*right*\
要测试是否不相等的对象。

### <a name="return-value"></a>返回值

如果*左侧*传递的对象不等于*右侧*传递的对象，**则为 true** ;否则**为 false**。

### <a name="remarks"></a>备注

该函数返回 `!(left == right)`。

## <a name="operatorlt"></a><a name="op_lt"></a> 运算符&lt;

测试一个对象是否小于要比较的传入对象。

```cpp
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

### <a name="parameters"></a>parameters

*左*\
要比较的对象。

*right*\
要比较的对象。

### <a name="return-value"></a>返回值

如果*左侧*传入的对象小于*向右*传递的对象，**则为 true** ;否则**为 false**。

### <a name="remarks"></a>备注

该函数测试错误顺序。

## <a name="operatorltlt"></a><a name="op_ostream"></a>操作员&lt;&lt;

```cpp
template <class charT, class traits>
    basic_ostream<charT, traits>& operator<<(basic_ostream<charT, traits>& os, const error_code& ec);
```
