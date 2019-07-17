---
title: '&lt;system_error&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 5cf6a455beb5654ef65f7411db4783a32c71d625
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246215"
---
# <a name="ltsystemerrorgt-operators"></a>&lt;system_error&gt; 运算符

## <a name="op_eq_eq"></a> 运算符 = =

测试运算符左侧的对象是否等于右侧的对象。

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);

bool operator==(const error_condition& left,
    const error_condition& right);
```

### <a name="parameters"></a>参数

*左侧*\
要测试是否相等的对象。

*右侧*\
要测试是否相等的对象。

### <a name="return-value"></a>返回值

如果对象相等，则为 **true**；如果对象不相等，则为 **false**。

### <a name="remarks"></a>备注

该函数返回 `left.category() == right.category() && left.value() == right.value()`。

## <a name="op_neq"></a> 运算符 ！ =

测试运算符左侧的对象是否不等于右侧的对象。

```cpp
bool operator!=(const error_code& left, const error_condition& right);
bool operator!=(const error_condition& left, const error_code& right);
bool operator!=(const error_code& left, const error_code& right);
bool operator!=(const error_condition& left, const error_condition& right);
```

### <a name="parameters"></a>参数

*左侧*\
要测试是否不相等的对象。

*右侧*\
要测试是否不相等的对象。

### <a name="return-value"></a>返回值

**true**如果在传递的对象*左*是否不等于传入的对象*右*; 否则为**false**。

### <a name="remarks"></a>备注

该函数返回 `!(left == right)`。

## <a name="op_lt"></a> 运算符&lt;

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

### <a name="parameters"></a>参数

*左侧*\
要比较的对象。

*右侧*\
要比较的对象。

### <a name="return-value"></a>返回值

**true**如果在传递的对象*左*小于传入的对象*右*;否则为**false**。

### <a name="remarks"></a>备注

该函数测试错误顺序。

## <a name="op_ostream"></a> 运算符&lt;&lt;

```cpp
template <class charT, class traits> 
    basic_ostream<charT, traits>& operator<<(basic_ostream<charT, traits>& os, const error_code& ec);
```
