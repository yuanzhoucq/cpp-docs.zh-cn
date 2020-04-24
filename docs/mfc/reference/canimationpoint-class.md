---
title: CAnimationPoint 类
ms.date: 11/04/2016
f1_keywords:
- CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetX
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetY
- AFXANIMATIONCONTROLLER/CAnimationPoint::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_xValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_yValue
helpviewer_keywords:
- CAnimationPoint [MFC], CAnimationPoint
- CAnimationPoint [MFC], AddTransition
- CAnimationPoint [MFC], GetDefaultValue
- CAnimationPoint [MFC], GetValue
- CAnimationPoint [MFC], GetX
- CAnimationPoint [MFC], GetY
- CAnimationPoint [MFC], SetDefaultValue
- CAnimationPoint [MFC], GetAnimationVariableList
- CAnimationPoint [MFC], m_xValue
- CAnimationPoint [MFC], m_yValue
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
ms.openlocfilehash: fcdd07efb46c97d27a9f1349c297688b5705f176
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755152"
---
# <a name="canimationpoint-class"></a>CAnimationPoint 类

实现可对点坐标进行动画处理的点功能。

## <a name="syntax"></a>语法

```
class CAnimationPoint : public CAnimationBaseObject;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[动画点：动画点](#canimationpoint)|已重载。 构造 CAnimationPoint 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[动画点：：添加转换](#addtransition)|添加 X 和 Y 坐标的过渡。|
|[动画点：获取默认值](#getdefaultvalue)|返回 X 和 Y 坐标的默认值。|
|[动画点：获取价值](#getvalue)|返回当前值。|
|[动画点：GetX](#getx)|提供 X 坐标对 CAnimation 变量的访问。|
|[动画点：获取 Y](#gety)|提供对 Y 坐标的 CAnimation 变量的访问。|
|[动画点：：设置默认值](#setdefaultvalue)|设置默认值。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[动画点：：获取动画变量列表](#getanimationvariablelist)|将封装的动画变量放入列表中。 （覆盖[动画基础对象：获取动画变量列表](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[动画点：：运算符 CPoint](#operator_cpoint)|将 C动画点转换为 CPoint。|
|[动画点：：操作员*](#operator_eq)|将 ptSrc 分配给 C 动画点。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[动画点：m_xValue](#m_xvalue)|表示动画点的 X 坐标的封装动画变量。|
|[动画点：m_yValue](#m_yvalue)|表示动画点的 Y 坐标的封装动画变量。|

## <a name="remarks"></a>备注

CAnimationPoint 类封装了两个 CAnimationvariable 对象，可以在应用程序中表示一个点。 例如，可以使用此类为屏幕上任何对象的位置（如文本字符串、圆圈、点等）设置动画。 要在应用程序中使用此类，只需实例化此类的对象，请使用 CAnimationController：：addAnimationObject 将其添加到动画控制器，并调用 AddTransition，以便应用于 X 和/或 Y 坐标的每个转换。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[动画基础对象](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="canimationpointaddtransition"></a><a name="addtransition"></a>动画点：：添加转换

添加 X 和 Y 坐标的过渡。

```cpp
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>参数

*pX转换*<br/>
X 坐标的转换指针。

*pY转换*<br/>
Y 坐标的转换指针。

### <a name="remarks"></a>备注

调用此函数以将指定的过渡添加到要应用于 X 和 Y 坐标的动画变量的内部过渡列表中。 添加转换时，不会立即应用这些转换并存储在内部列表中。 当您调用 CAnimationController：：AnimateGroup 时，将应用转换（添加到特定值的情节提要中）。 如果不需要将转换应用于其中一个坐标，则可以传递 NULL。

## <a name="canimationpointcanimationpoint"></a><a name="canimationpoint"></a>动画点：动画点

构造 CAnimationPoint 对象。

```
CAnimationPoint();

CAnimationPoint(
    const CPoint& ptDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>参数

*ptDefault*<br/>
指定默认点坐标。

*n集团ID*<br/>
指定组 ID。

*nObjectID*<br/>
指定对象 ID。

*dwUserData*<br/>
指定用户定义的数据。

### <a name="remarks"></a>备注

构造具有默认属性的 CAnimationPoint 对象：默认点坐标、组 ID 和对象 ID 设置为 0。

## <a name="canimationpointgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>动画点：：获取动画变量列表

将封装的动画变量放入列表中。

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>参数

*Lst*<br/>
当函数返回时，它包含指向表示 X 和 Y 坐标的两个 CAnimation 变量对象的指针。

## <a name="canimationpointgetdefaultvalue"></a><a name="getdefaultvalue"></a>动画点：获取默认值

返回 X 和 Y 坐标的默认值。

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>返回值

包含默认值的点。

### <a name="remarks"></a>备注

调用此函数以检索以前由构造函数或 SetDefaultValue 设置的默认值。

## <a name="canimationpointgetvalue"></a><a name="getvalue"></a>动画点：获取价值

返回当前值。

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>参数

*ptValue*<br/>
输出。 当此方法返回时，包含当前值。

### <a name="return-value"></a>返回值

TRUE，如果成功检索当前值;如果成功检索当前值，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

调用此函数以检索动画点的当前值。 如果此方法失败或 X 和 Y 坐标的基础 COM 对象尚未初始化，则 ptValue 包含默认值，该值以前在构造函数或 SetDefaultValue 中设置。

## <a name="canimationpointgetx"></a><a name="getx"></a>动画点：GetX

提供 X 坐标对 CAnimation 变量的访问。

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>返回值

表示 X 坐标的封装 CAnimation 变量的引用。

### <a name="remarks"></a>备注

可以调用此方法以直接访问表示 X 坐标的基础 C动画变量。

## <a name="canimationpointgety"></a><a name="gety"></a>动画点：获取 Y

提供对 Y 坐标的 CAnimation 变量的访问。

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>返回值

表示 Y 坐标的封装 CAnimation 变量的引用。

### <a name="remarks"></a>备注

可以调用此方法以直接访问表示 Y 坐标的基础 C动画变量。

## <a name="canimationpointm_xvalue"></a><a name="m_xvalue"></a>动画点：m_xValue

表示动画点的 X 坐标的封装动画变量。

```
CAnimationVariable m_xValue;
```

## <a name="canimationpointm_yvalue"></a><a name="m_yvalue"></a>动画点：m_yValue

表示动画点的 Y 坐标的封装动画变量。

```
CAnimationVariable m_yValue;
```

## <a name="canimationpointoperator-cpoint"></a><a name="operator_cpoint"></a>动画点：：运算符 CPoint

将 C动画点转换为 CPoint。

```
operator CPoint();
```

### <a name="return-value"></a>返回值

CAnimationPoint 作为 CPoint 的当前值。

### <a name="remarks"></a>备注

此功能在内部调用 GetValue。 如果由于某种原因 GetValue 失败，则返回的点将包含 X 和 Y 坐标的默认值。

## <a name="canimationpointoperator"></a><a name="operator_eq"></a>动画点：：操作员*

将 ptSrc 分配给 C 动画点。

```cpp
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>参数

*ptSrc*<br/>
指 CPoint 或 POINT。

### <a name="remarks"></a>备注

将 ptSrc 分配给 C 动画点。 建议在动画启动之前执行此操作，因为此运算符调用 SetDefaultValue，如果已创建 X 和 Y 坐标，则重新创建 X 和 Y 坐标的基础 COM 对象。 如果将此动画对象订阅到事件（Value已更改或整数值更改），则需要重新启用这些事件。

## <a name="canimationpointsetdefaultvalue"></a><a name="setdefaultvalue"></a>动画点：：设置默认值

设置默认值。

```cpp
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>参数

*ptDefault*<br/>
指定默认点值。

### <a name="remarks"></a>备注

使用此函数可为动画对象设置默认值。 此方法将默认值分配给动画点的 X 和 Y 坐标。 它还会重新创建基础 COM 对象（如果已创建）。 如果将此动画对象订阅到事件（Value已更改或整数值更改），则需要重新启用这些事件。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
