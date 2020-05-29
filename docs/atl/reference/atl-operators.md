---
title: ATL 运算符
ms.date: 11/04/2016
helpviewer_keywords:
- operators [ATL]
ms.assetid: 58ccd252-2869-45ee-8a5c-3ca40ee7f8a2
ms.openlocfilehash: fe5363d3d05123c17e45254898e2210797400022
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168847"
---
# <a name="atl-operators"></a>ATL 运算符

本部分包含 ATL 全局运算符的参考主题。

|运算符|说明|
|--------------|-----------------|
|[operator = =](#operator_eq_eq)|比较两`CSid`个对象`SID`或结构是否相等。|
|[operator！ =](#operator_neq)|比较两`CSid`个对象`SID`或结构是否不相等。|
|[运算符 <](#operator_lt)|测试运算符左侧`CSid`的对象`SID`或结构是否小于右侧的`CSid`对象或`SID`结构（适用于 c + + 标准库兼容性）。|
|[运算符 >](#operator_gt)|测试运算符左侧`CSid`的对象`SID`或结构是否大于右侧的`CSid`对象或`SID`结构（适用于 c + + 标准库兼容性）。|
|[运算符 <=](#operator_lt__eq)|测试运算符左侧`CSid`的对象`SID`或结构是否小于或等于右侧的`CSid`对象或`SID`结构（适用于 c + + 标准库兼容性）。|
|[运算符 >=](#operator_gt__eq)|测试运算符左侧`CSid`的对象`SID`或结构是否大于或等于右侧的`CSid`对象或`SID`结构（适用于 c + + 标准库兼容性）。|

## <a name="requirements"></a>要求

**标头：** atlsecurity.h。

## <a name="operator-"></a><a name="operator_eq_eq"></a>operator = =

比较`CSid`对象或`SID` （安全标识符）结构是否相等。

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较`CSid`的第`SID`一个对象或结构。

rhs**<br/>
要比较`CSid`的第`SID`二个对象或结构。

### <a name="return-value"></a>返回值

如果对象相等，则返回 TRUE，否则返回 FALSE。

## <a name="operator-"></a><a name="operator_neq"></a>operator！ =

比较`CSid`对象或`SID` （安全标识符）结构是否不相等。

```cpp
bool operator==(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较`CSid`的第`SID`一个对象或结构。

rhs**<br/>
要比较`CSid`的第`SID`二个对象或结构。

### <a name="return-value"></a>返回值

如果对象不相等，则返回 TRUE，否则返回 FALSE。

## <a name="operator-"></a><a name="operator_lt"></a>运算符 <

测试运算符左侧`CSid`的对象`SID`或结构是否小于右侧的`CSid`对象或`SID`结构（适用于 c + + 标准库兼容性）。

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较`CSid`的第`SID`一个对象或结构。

rhs**<br/>
要比较`CSid`的第`SID`二个对象或结构。

### <a name="return-value"></a>返回值

如果*lhs*对象的地址小于*rhs*对象的地址，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

此运算符作用于`CSid`对象或`SID`结构的地址，并实现以提供与 c + + 标准库集合类的兼容性。

## <a name="operator-"></a><a name="operator_gt"></a>运算符 >

测试运算符左侧`CSid`的对象`SID`或结构是否大于右侧的`CSid`对象或`SID`结构（适用于 c + + 标准库兼容性）。

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较`CSid`的第`SID`一个对象或结构。

rhs**<br/>
要比较`CSid`的第`SID`二个对象或结构。

### <a name="return-value"></a>返回值

如果*lhs*的地址大于*rhs*的地址，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

此运算符作用于`CSid`对象或`SID`结构的地址，并实现以提供与 c + + 标准库集合类的兼容性。

## <a name="operator-"></a><a name="operator_lt__eq"></a>运算符 <=

测试运算符左侧`CSid`的对象`SID`或结构是否小于或等于右侧的`CSid`对象或`SID`结构（适用于 c + + 标准库兼容性）。

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较`CSid`的第`SID`一个对象或结构。

rhs**<br/>
要比较`CSid`的第`SID`二个对象或结构。

### <a name="return-value"></a>返回值

如果*lhs*的地址小于或等于*rhs*的地址，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

此运算符作用于`CSid`对象或`SID`结构的地址，并实现以提供与 c + + 标准库集合类的兼容性。

## <a name="operator-"></a><a name="operator_gt__eq"></a>运算符 >=

测试运算符左侧`CSid`的对象`SID`或结构是否大于或等于右侧的`CSid`对象或`SID`结构（适用于 c + + 标准库兼容性）。

```cpp
bool operator<(const CSid& lhs, const CSid& rhs) throw();
```

### <a name="parameters"></a>参数

*lhs*<br/>
要比较`CSid`的第`SID`一个对象或结构。

rhs**<br/>
要比较`CSid`的第`SID`二个对象或结构。

### <a name="return-value"></a>返回值

如果*lhs*的地址大于或等于*rhs*的地址，则返回 TRUE，否则返回 FALSE。

### <a name="remarks"></a>备注

此运算符作用于`CSid`对象或`SID`结构的地址，并实现以提供与 c + + 标准库集合类的兼容性。
