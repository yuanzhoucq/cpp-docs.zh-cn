---
title: '&lt;forward_list&gt; 运算符'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::operator!=
- forward_list/std::operator==
- forward_list/std::operatoroperator&gt;
- forward_list/std::operatoroperator&gt=;
- forward_list/std::operatoroperator&lt;
- forward_list/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (forward_list)
- std::operator== (forward_list)
- std::operatoroperator&gt; (forward_list)
- std::operatoroperator&gt=; (forward_list)
- std::operatoroperator&lt; (forward_list)
- std::operatoroperator&lt;= (forward_list)
ms.openlocfilehash: 1ddfb56c7ff68ec10c7bb56af3495e4042acb83c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427085"
---
# <a name="ltforward_listgt-operators"></a>&lt;forward_list&gt; 运算符

## <a name="op_eq_eq"></a>operator = =

测试运算符左侧的转发列表对象是否等于右侧的转发列表对象。

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左*\
一个 `forward_list` 类型的对象。

*right*\
一个 `forward_list` 类型的对象。

### <a name="remarks"></a>备注

此模板函数重载 `operator==` 比较类模板 `forward_list`的两个对象。 该函数返回 `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`。

## <a name="op_neq"></a>operator！ =

测试运算符左侧的转发列表对象是否不等于右侧的转发列表对象。

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左*\
一个 `forward_list` 类型的对象。

*right*\
一个 `forward_list` 类型的对象。

### <a name="return-value"></a>返回值

如果列表不相等，则为 **true**；如果列表相等，则为 **false**。

### <a name="remarks"></a>备注

此模板函数返回 `!(left == right)`。

## <a name="op_lt"></a> 运算符&lt;

测试运算符左侧的转发列表对象是否小于右侧的转发列表对象。

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左*\
一个 `forward_list` 类型的对象。

*right*\
一个 `forward_list` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的列表小于但不等于运算符右侧的列表，则为 **true**，否则为 **false**。

### <a name="remarks"></a>备注

此模板函数重载 `operator<` 比较类模板 `forward_list`的两个对象。 该函数返回 `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`。

## <a name="op_lt_eq"></a>操作员&lt;=

测试运算符左侧的转发列表对象是否小于或等于右侧的转发列表对象。

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左*\
一个 `forward_list` 类型的对象。

*right*\
一个 `forward_list` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的列表小于或等于运算符右侧的列表，则为 **true**，否则为 **false**。

### <a name="remarks"></a>备注

此模板函数返回 `!(right < left)`。

## <a name="op_gt"></a> 运算符&gt;

测试运算符左侧的转发列表对象是否大于右侧的转发列表对象。

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左*\
一个 `forward_list` 类型的对象。

*right*\
一个 `forward_list` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的列表大于右侧的列表，则为 **true**，否则为 **false**。

### <a name="remarks"></a>备注

此模板函数返回 `right < left`。

## <a name="op_gt_eq"></a>操作员&gt;=

测试运算符左侧的转发列表对象是否大于或等于右侧的转发列表对象。

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>parameters

*左*\
一个 `forward_list` 类型的对象。

*right*\
一个 `forward_list` 类型的对象。

### <a name="return-value"></a>返回值

如果运算符左侧的转发列表大于或等于运算符右侧的转发列表，**则为 true** ; 否则为。否则**为 false**。

### <a name="remarks"></a>备注

此模板函数返回 `!(left < right)`。
