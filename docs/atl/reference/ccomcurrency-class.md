---
title: CComCurrency 类
ms.date: 11/04/2016
f1_keywords:
- CComCurrency
- ATLCUR/ATL::CComCurrency
- ATLCUR/ATL::CComCurrency::CComCurrency
- ATLCUR/ATL::CComCurrency::GetCurrencyPtr
- ATLCUR/ATL::CComCurrency::GetFraction
- ATLCUR/ATL::CComCurrency::GetInteger
- ATLCUR/ATL::CComCurrency::Round
- ATLCUR/ATL::CComCurrency::SetFraction
- ATLCUR/ATL::CComCurrency::SetInteger
- ATLCUR/ATL::CComCurrency::m_currency
helpviewer_keywords:
- CComCurrency class
ms.assetid: a1c3d10a-bba6-40cc-8bcf-aed9023c8a9e
ms.openlocfilehash: 541944e03e9caf6cba15612cf9e7cbbd239555ca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327946"
---
# <a name="ccomcurrency-class"></a>CComCurrency 类

`CComCurrency` 具有用于创建和管理 CURRENCY 对象的方法和运算符。

## <a name="syntax"></a>语法

```
class CComCurrency
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[CComCurrency::CComCurrency](#ccomcurrency)|`CComCurrency` 对象的构造函数。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[CCom货币：获取货币点](#getcurrencyptr)|返回 `m_currency` 数据成员的地址。|
|[CCom货币：获取分数](#getfraction)|调用此方法以返回 `CComCurrency` 对象的小数部分。|
|[CCom货币：获取Integer](#getinteger)|调用此方法以返回 `CComCurrency` 对象的整数部分。|
|[CComCurrency::Round](#round)|调用此方法以将 `CComCurrency` 对象舍入为最接近的整数值。|
|[CComCurrency::SetFraction](#setfraction)|调用此方法以设置 `CComCurrency` 对象的小数部分。|
|[CComCurrency::SetInteger](#setinteger)|调用此方法以设置 `CComCurrency` 对象的整数部分。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[CCom货币：：运算符 -](#operator_-)|此运算符用于对 `CComCurrency` 对象执行减法。|
|[CCom货币：：操作员！*](#operator_neq)|比较两个 `CComCurrency` 对象是否相等。|
|[CCom货币：：操作员 |](#operator_star)|此运算符用于对 `CComCurrency` 对象执行乘法。|
|[CCom货币：：操作员 |](#operator_star_eq)|此运算符用于对 `CComCurrency` 对象执行乘法并对它赋予结果。|
|[CComCurrency::operator /](#operator_div)|此运算符用于对 `CComCurrency` 对象执行除法。|
|[CCom货币：：操作员/*](#operator_div_eq)|此运算符用于对 `CComCurrency` 对象执行除法并对它赋予结果。|
|[CCom货币：：运算符 |](#operator_add)|此运算符用于对 `CComCurrency` 对象执行加法。|
|[CCom货币：：操作员 |](#operator_add_eq)|此运算符用于对 `CComCurrency` 对象执行加法并对它赋予结果。|
|[CCom货币：：操作员<](#operator_lt)|此运算符比较两个 `CComCurrency` 对象以确定较小者。|
|[CCom货币：：操作员<|](#operator_lt_eq)|此运算符比较两个 `CComCurrency` 对象以确定是否相等或较小者。|
|[CCom货币：：运算符 |](#operator_eq)|此运算符向 `CComCurrency` 对象赋予新值。|
|[CCom货币：：运算符 -*](#operator_-_eq)|此运算符用于对 `CComCurrency` 对象执行减法并对它赋予结果。|
|[CCom货币：：运算符 |](#operator_eq_eq)|此运算符比较两个 `CComCurrency` 对象是否相等。|
|[CCom货币：：操作员>](#operator_gt)|此运算符比较两个 `CComCurrency` 对象以确定较大者。|
|[CCom货币：：操作员>|](#operator_gt_eq)|此运算符比较两个 `CComCurrency` 对象以确定是否相等或较大者。|
|[CCom货币：：运营商货币](#operator_currency)|强制转换货币对象。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[CComCurrency::m_currency](#m_currency)|类实例创建的货币变量。|

## <a name="remarks"></a>备注

`CComCurrency` 是 CURRENCY 数据类型的包装。 CURRENCY 是作为按 10,000 缩放的 8 字节补码整数值实现的。 这产生了一个定点数数字，小数点左侧有 15 位数，右侧有 4 位数。 CURRENCY 数据类型对于涉及到货币的计算或精确度至关重要的所有定点数计算非常有用。

包装`CComCurrency`器实现此定点类型的算术、赋值和比较操作。 已选中受支持的应用程序，以控制定点计算过程中可能出现的舍入误差。

`CComCurrency` 对象以两个组件的形式提供对小数点两侧的数字的访问权限：一个整数组件，它存储小数点左侧的值；一个小数组件，它存储小数点右侧的值。 小数部分作为介于 -9999 (CY_MIN_FRACTION) 和 +9999 (CY_MAX_FRACTION) 之间的整数值存储在内部。 方法[CCom货币：GetFraction](#getfraction)返回按 10000 （CY_SCALE） 因子缩放的值。

指定`CComCurrency`对象的整数和小数分量时，请记住小数分量是范围 0 到 9999 中的数字。 在处理美元等在小数点后仅采用两个有效位数来表示金额的货币时，这一点非常有用。 即使不显示最后两位数字，也必须将它们考虑在内。

|“值”|可能的 CComCurrency 赋值|
|-----------|---------------------------------------|
|$10.50|CCom货币 （10，5000）*或*Ccom 货币 （10.50）|
|$10.05|CCom货币 （10，500）*或*CCom 货币 （10.05）|

值 CY_MIN_FRACTION、CY_MAX_FRACTION 和 CY_SCALE 是在 atlcur.h 中定义的。

## <a name="requirements"></a>要求

**标题：** atlcur.h

## <a name="ccomcurrencyccomcurrency"></a><a name="ccomcurrency"></a>CCom货币：Ccom货币

构造函数。

```
CComCurrency() throw();
CComCurrency(const CComCurrency& curSrc) throw();
CComCurrency(CURRENCY cySrc) throw();
CComCurrency(DECIMAL dSrc);
CComCurrency(ULONG ulSrc);
CComCurrency(USHORT usSrc);
CComCurrency(CHAR cSrc);
CComCurrency(DOUBLE dSrc);
CComCurrency(FLOAT fSrc);
CComCurrency(LONG lSrc);
CComCurrency(SHORT sSrc);
CComCurrency(BYTE bSrc);
CComCurrency(LONGLONG nInteger, SHORT nFraction);
explicit CComCurrency(LPDISPATCH pDispSrc);
explicit CComCurrency(const VARIANT& varSrc);
explicit CComCurrency(LPCWSTR szSrc);
explicit CComCurrency(LPCSTR szSrc);
```

### <a name="parameters"></a>参数

*库尔斯克*<br/>
一个现有的 `CComCurrency` 对象。

*西斯尔克*<br/>
货币类型的变量。

*bSrc*， *dSrc*， *fSrc*， *lSrc*， *ssrc*， *ulSrc， usSrc*<br/>
给成员变量`m_currency`的初始值。

*证监会*<br/>
包含给予成员变量`m_currency`的初始值的字符。

*nInteger*， *nfraction*<br/>
初始货币值的整数和小数分量。 有关详细信息，请参阅[CCom 货币](../../atl/reference/ccomcurrency-class.md)概述。

*pDispSrc*<br/>
指针`IDispatch`。

*varSrc*<br/>
VARIANT 类型的变量。 当前线程的区域设置用于执行转换。

*什施尔克*<br/>
包含初始值的 Unicode 或 ANSI 字符串。 当前线程的区域设置用于执行转换。

### <a name="remarks"></a>备注

构造函数设置[CComCurrency：：m_currency](#m_currency)的初始值，并接受各种数据类型，包括整数、字符串、浮点数、货币变量和其他`CComCurrency`对象。 如果未提供任何值，`m_currency`则设置为 0。

如果出现错误（如溢出），构造函数缺少空异常规范 **（throw（）** 调用`AtlThrow`，HRESULT 描述错误。

当使用浮点或双精度值分配值时，`CComCurrency(10.50)`注释等效`CComCurrency(10,5000)`于 而不是`CComCurrency(10,50)`。

## <a name="ccomcurrencygetcurrencyptr"></a><a name="getcurrencyptr"></a>CCom货币：获取货币点

返回 `m_currency` 数据成员的地址。

```
CURRENCY* GetCurrencyPtr() throw();
```

### <a name="return-value"></a>返回值

返回`m_currency`数据成员的地址

## <a name="ccomcurrencygetfraction"></a><a name="getfraction"></a>CCom货币：获取分数

调用此方法以返回`CComCurrency`对象的小数组件。

```
SHORT GetFraction() const;
```

### <a name="return-value"></a>返回值

返回`m_currency`数据成员的小数组件。

### <a name="remarks"></a>备注

小数分量是 -9999（CY_MIN_FRACTION）和 +9999 （CY_MAX_FRACTION） 之间的 4 位整数值。 `GetFraction`返回按 10000 （CY_SCALE） 缩放的此值。 CY_MIN_FRACTION、CY_MAX_FRACTION和CY_SCALE的值在 atlcur.h 中定义。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#50](../../atl/codesnippet/cpp/ccomcurrency-class_1.cpp)]

## <a name="ccomcurrencygetinteger"></a><a name="getinteger"></a>CCom货币：获取Integer

调用此方法获取`CComCurrency`对象的整数组件。

```
LONGLONG GetInteger() const;
```

### <a name="return-value"></a>返回值

返回数据成员的`m_currency`整数组件。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#51](../../atl/codesnippet/cpp/ccomcurrency-class_2.cpp)]

## <a name="ccomcurrencym_currency"></a><a name="m_currency"></a>CCom货币：：m_currency

货币数据成员。

```
CURRENCY m_currency;
```

### <a name="remarks"></a>备注

此成员持有由此类的方法访问和操作的货币。

## <a name="ccomcurrencyoperator--"></a><a name="operator_-"></a>CCom货币：：运算符 -

此运算符用于对 `CComCurrency` 对象执行减法。

```
CComCurrency operator-() const;
CComCurrency operator-(const CComCurrency& cur) const;
```

### <a name="parameters"></a>参数

*当前*<br/>
`CComCurrency` 对象。

### <a name="return-value"></a>返回值

返回表示`CComCurrency`减法结果的对象。 如果出现错误（如溢出），此操作员使用描述错误的 HRESULT`AtlThrow`调用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#55](../../atl/codesnippet/cpp/ccomcurrency-class_3.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_neq"></a>CCom货币：：操作员！*

此运算符比较两个对象为不等式。

```
bool operator!= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>参数

*当前*<br/>
要比较的 `CComCurrency` 对象。

### <a name="return-value"></a>返回值

如果要比较的项不等于对象，`CComCurrency`则返回 TRUE;否则，FALSE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#56](../../atl/codesnippet/cpp/ccomcurrency-class_4.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_star"></a>CCom货币：：操作员 |

此运算符用于对 `CComCurrency` 对象执行乘法。

```
CComCurrency operator*(long nOperand) const;
CComCurrency operator*(const CComCurrency& cur) const;
```

### <a name="parameters"></a>参数

*恩奥佩安*<br/>
乘数。

*当前*<br/>
用作`CComCurrency`乘数的对象。

### <a name="return-value"></a>返回值

返回表示`CComCurrency`乘法结果的对象。 如果出现错误（如溢出），此操作员使用描述错误的 HRESULT`AtlThrow`调用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#57](../../atl/codesnippet/cpp/ccomcurrency-class_5.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_star_eq"></a>CCom货币：：运算符\*=

此运算符用于对 `CComCurrency` 对象执行乘法并对它赋予结果。

```
const CComCurrency& operator*= (long nOperand);
const CComCurrency& operator*= (const CComCurrency& cur);
```

### <a name="parameters"></a>参数

*恩奥佩安*<br/>
乘数。

*当前*<br/>
用作`CComCurrency`乘数的对象。

### <a name="return-value"></a>返回值

返回更新`CComCurrency`的对象。 如果出现错误（如溢出），此操作员使用描述错误的 HRESULT`AtlThrow`调用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#58](../../atl/codesnippet/cpp/ccomcurrency-class_6.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_div"></a>CCom货币：：操作员/

此运算符用于对 `CComCurrency` 对象执行除法。

```
CComCurrency operator/(long nOperand) const;
```

### <a name="parameters"></a>参数

*恩奥佩安*<br/>
除数。

### <a name="return-value"></a>返回值

返回表示`CComCurrency`除法结果的对象。 如果分器为 0，则会发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#59](../../atl/codesnippet/cpp/ccomcurrency-class_7.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_div_eq"></a>CCom货币：：操作员/*

此运算符用于对 `CComCurrency` 对象执行除法并对它赋予结果。

```
const CComCurrency& operator/= (long nOperand);
```

### <a name="parameters"></a>参数

*恩奥佩安*<br/>
除数。

### <a name="return-value"></a>返回值

返回更新`CComCurrency`的对象。 如果分器为 0，则会发生断言失败。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#60](../../atl/codesnippet/cpp/ccomcurrency-class_8.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_add"></a>CCom货币：：运算符 |

此运算符用于对 `CComCurrency` 对象执行加法。

```
CComCurrency operator+(const CComCurrency& cur) const;
```

### <a name="parameters"></a>参数

*当前*<br/>
要`CComCurrency`添加到原始对象的对象。

### <a name="return-value"></a>返回值

返回表示`CComCurrency`添加结果的对象。 如果出现错误（如溢出），此操作员使用描述错误的 HRESULT`AtlThrow`调用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#61](../../atl/codesnippet/cpp/ccomcurrency-class_9.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_add_eq"></a>CCom货币：：操作员 |

此运算符用于对 `CComCurrency` 对象执行加法并对它赋予结果。

```
const CComCurrency& operator+= (const CComCurrency& cur);
```

### <a name="parameters"></a>参数

*当前*<br/>
`CComCurrency` 对象。

### <a name="return-value"></a>返回值

返回更新`CComCurrency`的对象。 如果出现错误（如溢出），此操作员使用描述错误的 HRESULT`AtlThrow`调用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#62](../../atl/codesnippet/cpp/ccomcurrency-class_10.cpp)]

## <a name="ccomcurrencyoperator-lt"></a><a name="operator_lt"></a>CCom货币：：运算符&lt;

此运算符比较两个 `CComCurrency` 对象以确定较小者。

```
bool operator<(const CComCurrency& cur) const;
```

### <a name="parameters"></a>参数

*当前*<br/>
`CComCurrency` 对象。

### <a name="return-value"></a>返回值

如果第一个对象小于第二个对象 FALSE，则返回 TRUE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#63](../../atl/codesnippet/cpp/ccomcurrency-class_11.cpp)]

## <a name="ccomcurrencyoperator-lt"></a><a name="operator_lt_eq"></a>CCom货币：：运算符&lt;=

此运算符比较两个 `CComCurrency` 对象以确定是否相等或较小者。

```
bool operator<= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>参数

*当前*<br/>
`CComCurrency` 对象。

### <a name="return-value"></a>返回值

如果第一个对象小于或等于第二个对象 FALSE，则返回 TRUE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#64](../../atl/codesnippet/cpp/ccomcurrency-class_12.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_eq"></a>CCom货币：：运算符 |

此运算符向 `CComCurrency` 对象赋予新值。

```
const CComCurrency& operator= (const CComCurrency& curSrc) throw();
const CComCurrency& operator= (CURRENCY cySrc) throw();
const CComCurrency& operator= (FLOAT fSrc);
const CComCurrency& operator= (SHORT sSrc);
const CComCurrency& operator= (LONG lSrc);
const CComCurrency& operator= (BYTE bSrc);
const CComCurrency& operator= (USHORT usSrc);
const CComCurrency& operator= (DOUBLE dSrc);
const CComCurrency& operator= (CHAR cSrc);
const CComCurrency& operator= (ULONG ulSrc);
const CComCurrency& operator= (DECIMAL dSrc);
```

### <a name="parameters"></a>参数

*库尔斯克*<br/>
`CComCurrency` 对象。

*西斯尔克*<br/>
货币类型的变量。

*sSrc，* *fSrc*， *lSrc*， *bSrc*， *usSrc*， *dSrc*， *csrc，* *ulSrc，* *dSrc*<br/>
要分配给`CComCurrency`对象的数值。

### <a name="return-value"></a>返回值

返回更新`CComCurrency`的对象。 如果出现错误（如溢出），此操作员使用描述错误的 HRESULT`AtlThrow`调用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#65](../../atl/codesnippet/cpp/ccomcurrency-class_13.cpp)]

## <a name="ccomcurrencyoperator--"></a><a name="operator_-_eq"></a>CCom货币：：运算符 -*

此运算符用于对 `CComCurrency` 对象执行减法并对它赋予结果。

```
const CComCurrency& operator-= (const CComCurrency& cur);
```

### <a name="parameters"></a>参数

*当前*<br/>
`CComCurrency` 对象。

### <a name="return-value"></a>返回值

返回更新`CComCurrency`的对象。 如果出现错误（如溢出），此操作员使用描述错误的 HRESULT`AtlThrow`调用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#66](../../atl/codesnippet/cpp/ccomcurrency-class_14.cpp)]

## <a name="ccomcurrencyoperator-"></a><a name="operator_eq_eq"></a>CCom货币：：运算符 |

此运算符比较两个 `CComCurrency` 对象是否相等。

```
bool operator== (const CComCurrency& cur) const;
```

### <a name="parameters"></a>参数

*当前*<br/>
要比较的 `CComCurrency` 对象。

### <a name="return-value"></a>返回值

如果对象相等（即两个对象`m_currency`中的数据成员（整数和小数）具有相同的值，则返回 TRUE），否则为 FALSE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#67](../../atl/codesnippet/cpp/ccomcurrency-class_15.cpp)]

## <a name="ccomcurrencyoperator-gt"></a><a name="operator_gt"></a>CCom货币：：运算符&gt;

此运算符比较两个 `CComCurrency` 对象以确定较大者。

```
bool operator>(const CComCurrency& cur) const;
```

### <a name="parameters"></a>参数

*当前*<br/>
`CComCurrency` 对象。

### <a name="return-value"></a>返回值

如果第一个对象大于第二个对象 FALSE，则返回 TRUE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#68](../../atl/codesnippet/cpp/ccomcurrency-class_16.cpp)]

## <a name="ccomcurrencyoperator-gt"></a><a name="operator_gt_eq"></a>CCom货币：：运算符&gt;=

此运算符比较两个 `CComCurrency` 对象以确定是否相等或较大者。

```
bool operator>= (const CComCurrency& cur) const;
```

### <a name="parameters"></a>参数

*当前*<br/>
`CComCurrency` 对象。

### <a name="return-value"></a>返回值

如果第一个对象大于或等于第二个对象 FALSE，则返回 TRUE。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#69](../../atl/codesnippet/cpp/ccomcurrency-class_17.cpp)]

## <a name="ccomcurrencyoperator-currency"></a><a name="operator_currency"></a>CCom货币：：运营商货币

这些运算符用于将`CComCurrency`对象转换为货币数据类型。

```
operator CURRENCY&() throw();
operator const CURRENCY&() const throw();
```

### <a name="return-value"></a>返回值

返回对货币对象的引用。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#70](../../atl/codesnippet/cpp/ccomcurrency-class_18.cpp)]

## <a name="ccomcurrencyround"></a><a name="round"></a>CCom货币：圆形

调用此方法将货币舍入到指定的小数位数。

```
HRESULT Roundint nDecimals);
```

### <a name="parameters"></a>参数

*n 十进制*<br/>
将在范围 0 到`m_currency`4 内舍入到的位数。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#52](../../atl/codesnippet/cpp/ccomcurrency-class_19.cpp)]

## <a name="ccomcurrencysetfraction"></a><a name="setfraction"></a>CCom货币：：设置分数

调用此方法以设置 `CComCurrency` 对象的小数部分。

```
HRESULT SetFraction(SHORT nFraction);
```

### <a name="parameters"></a>参数

*n分数*<br/>
要分配给`m_currency`数据成员的小数组件的值。 小数分量的符号必须与整数分量相同，并且值必须在 -9999 （CY_MIN_FRACTION） 到 +9999 （CY_MAX_FRACTION） 范围内。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#53](../../atl/codesnippet/cpp/ccomcurrency-class_20.cpp)]

## <a name="ccomcurrencysetinteger"></a><a name="setinteger"></a>CCom货币：：Setinteger

调用此方法以设置 `CComCurrency` 对象的整数部分。

```
HRESULT SetInteger(LONGLONG nInteger);
```

### <a name="parameters"></a>参数

*内特格*<br/>
要分配给`m_currency`数据成员的整数组件的值。 整数组件的符号必须与现有小数组件的符号匹配。

*nInteger*必须在CY_MIN_INTEGER范围内CY_MAX_INTEGER包含。 这些值在 atlcur.h 中定义。

### <a name="return-value"></a>返回值

返回成功S_OK，或失败时返回错误 HRESULT。

### <a name="example"></a>示例

[!code-cpp[NVC_ATL_Utilities#54](../../atl/codesnippet/cpp/ccomcurrency-class_21.cpp)]

## <a name="see-also"></a>另请参阅

[COleCurrency 类](../../mfc/reference/colecurrency-class.md)<br/>
[货币](/windows/win32/api/wtypes/ns-wtypes-cy~r1)<br/>
[类概述](../../atl/atl-class-overview.md)
