---
title: ATL 运算符
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: 8c15daa1d2b12c58323ef5ef75559a2ab911ad93
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319226"
---
# <a name="atl-operators"></a>ATL 运算符

本节包含 ATL 全局运算符的参考主题。

|操作员|说明|
|--------------|-----------------|
|[运算符 |](#operator_eq_eq)|比较两`CSid`个对象`SID`或结构以表示相等。|
|[操作员 ！]](#operator_neq)|比较两`CSid`个对象`SID`或结构的不等式。|
|[运算符<](#operator_lt)|测试运算符左侧`CSid`的对象或`SID`结构是否小于右侧`CSid`的对象或`SID`结构（对于C++标准库兼容性）。|
|[运算符>](#operator_gt)|测试运算符左侧`CSid`的对象或`SID`结构是否大于右侧`CSid`的对象或`SID`结构（对于C++标准库兼容性）。|
|[操作员<|](#operator_lt__eq)|测试运算符左侧`CSid`的对象或`SID`结构是否小于或等于右侧`CSid`的对象或`SID`结构（对于C++标准库兼容性）。|
|[操作员>|](#operator_gt__eq)|测试运算符左侧`CSid`的对象或`SID`结构是否大于或等于右侧`CSid`的对象或`SID`结构（C++标准库兼容性）。|

## <a name="requirements"></a>要求

**标题：** atlsecurity.h.

## <a name="operator-"></a><a name="operator_eq_eq"></a>运算符 |

比较`CSid`对象或`SID`（安全标识符）结构以获得相等性。

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较`CSid`的第一`SID`个对象或结构。

rhs**<br/>
要比较`CSid`的第二`SID`个对象或结构。

### <a name="return-value"></a>返回值

如果对象相等，则返回 TRUE，如果对象不相等，则返回 FALSE。

## <a name="operator-"></a><a name="operator_neq"></a>操作员 ！]

比较`CSid`对象或`SID`（安全标识符）结构的不等式。

```
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较`CSid`的第一`SID`个对象或结构。

rhs**<br/>
要比较`CSid`的第二`SID`个对象或结构。

### <a name="return-value"></a>返回值

如果对象不相等，则返回 TRUE;如果对象相等，则返回 FALSE。

## <a name="operator-"></a><a name="operator_lt"></a>运算符<

测试运算符左侧`CSid`的对象或`SID`结构是否小于右侧`CSid`的对象或`SID`结构（对于C++标准库兼容性）。

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较`CSid`的第一`SID`个对象或结构。

rhs**<br/>
要比较`CSid`的第二`SID`个对象或结构。

### <a name="return-value"></a>返回值

如果*lhs*对象的地址小于*rhs*对象的地址，则返回 TRUE，否则为 FALSE。

### <a name="remarks"></a>备注

此运算符作用于`CSid`对象或`SID`结构的地址，并实现该运算符是为了提供与C++标准库集合类的兼容性。

## <a name="operator-"></a><a name="operator_gt"></a>运算符>

测试运算符左侧`CSid`的对象或`SID`结构是否大于右侧`CSid`的对象或`SID`结构（对于C++标准库兼容性）。

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较`CSid`的第一`SID`个对象或结构。

rhs**<br/>
要比较`CSid`的第二`SID`个对象或结构。

### <a name="return-value"></a>返回值

如果*lhs*的地址大于*rhs*的地址，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

此运算符作用于`CSid`对象或`SID`结构的地址，并实现该运算符是为了提供与C++标准库集合类的兼容性。

## <a name="operator-"></a><a name="operator_lt__eq"></a>操作员<|

测试运算符左侧`CSid`的对象或`SID`结构是否小于或等于右侧`CSid`的对象或`SID`结构（对于C++标准库兼容性）。

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较`CSid`的第一`SID`个对象或结构。

rhs**<br/>
要比较`CSid`的第二`SID`个对象或结构。

### <a name="return-value"></a>返回值

如果*lhs*的地址小于或等于*rhs*的地址，则返回 TRUE，否则。

### <a name="remarks"></a>备注

此运算符作用于`CSid`对象或`SID`结构的地址，并实现该运算符是为了提供与C++标准库集合类的兼容性。

## <a name="operator-"></a><a name="operator_gt__eq"></a>操作员>|

测试运算符左侧`CSid`的对象或`SID`结构是否大于或等于右侧`CSid`的对象或`SID`结构（C++标准库兼容性）。

```
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较`CSid`的第一`SID`个对象或结构。

rhs**<br/>
要比较`CSid`的第二`SID`个对象或结构。

### <a name="return-value"></a>返回值

如果*lhs*的地址大于或等于*rhs*的地址，则返回 TRUE，否则。

### <a name="remarks"></a>备注

此运算符作用于`CSid`对象或`SID`结构的地址，并实现该运算符是为了提供与C++标准库集合类的兼容性。
