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
ms.openlocfilehash: 15f06d2fa3478570d2f784879a13e7b68515e746
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271263"
---
# <a name="canimationpoint-class"></a>CAnimationPoint 类

实现可对点坐标进行动画处理的点功能。

## <a name="syntax"></a>语法

```
class CAnimationPoint : public CAnimationBaseObject;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAnimationPoint::CAnimationPoint](#canimationpoint)|已重载。 构造 CAnimationPoint 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAnimationPoint::AddTransition](#addtransition)|添加转换的 X 和 Y 坐标。|
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|返回默认值的 X 和 Y 坐标。|
|[CAnimationPoint::GetValue](#getvalue)|返回当前值。|
|[CAnimationPoint::GetX](#getx)|提供访问权限的 CAnimationVariable X 坐标。|
|[CAnimationPoint::GetY](#gety)|提供对 CAnimationVariable Y 坐标的访问。|
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|设置默认值。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|将封装的动画变量放入列表。 (重写[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。)|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CAnimationPoint::operator CPoint](#operator_cpoint)|转换为 CPoint CAnimationPoint。|
|[CAnimationPoint::operator=](#operator_eq)|将 ptSrc 分配给 CAnimationPoint。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CAnimationPoint::m_xValue](#m_xvalue)|封装的动画变量表示 X 坐标的动画点。|
|[CAnimationPoint::m_yValue](#m_yvalue)|封装的动画变量，表示动画点的 Y 坐标。|

## <a name="remarks"></a>备注

CAnimationPoint 类封装两个 CAnimationVariable 对象，并可以表示在应用程序中的点。 例如，可以使用此类进行动画处理 （例如文本字符串、 圆形、 点等） 在屏幕上的任何对象的位置。 若要使用此类应用程序中，只需实例化此类的对象、 将其添加到动画控制器使用 CAnimationController::AddAnimationObject 和调用每个转换下要应用于 X 和/或 Y 坐标。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationPoint::AddTransition

添加转换的 X 和 Y 坐标。

```
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>参数

*pXTransition*<br/>
X 坐标转换为指针。

*pYTransition*<br/>
指向转换 Y 坐标。

### <a name="remarks"></a>备注

调用此函数可指定的转换添加到内部列表的转换将应用于动画变量的 X 和 Y 坐标。 添加转换，它们不会立即应用并存储在内部列表。 转换应用 （已添加到情节提要的特定值） 当你调用 CAnimationController::AnimateGroup。 如果不需要将转换应用到一个坐标，则可以传递 NULL。

##  <a name="canimationpoint"></a>  CAnimationPoint::CAnimationPoint

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

*nGroupID*<br/>
指定组 id。

*nObjectID*<br/>
指定对象 id。

*dwUserData*<br/>
指定用户定义的数据。

### <a name="remarks"></a>备注

构造 CAnimationPoint 对象使用默认属性： 默认值为点坐标，组 ID 和对象 ID 设置为 0。

##  <a name="getanimationvariablelist"></a>  CAnimationPoint::GetAnimationVariableList

将封装的动画变量放入列表。

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>参数

*lst*<br/>
当函数返回时，它包含两个 CAnimationVariable 表示的对象的 X 和 Y 坐标的指针。

##  <a name="getdefaultvalue"></a>  CAnimationPoint::GetDefaultValue

返回默认值的 X 和 Y 坐标。

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>返回值

点包含默认值。

### <a name="remarks"></a>备注

调用此函数检索以前已由构造函数或 SetDefaultValue 设置的默认值。

##  <a name="getvalue"></a>  CAnimationPoint::GetValue

返回当前值。

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>参数

*ptValue*<br/>
输出。 此方法返回时包含的当前值。

### <a name="return-value"></a>返回值

已成功检索当前值; 如果为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

调用此函数可检索当前动画点的值。 如果此方法失败或基础 COM 对象的 X 和 Y 坐标尚未初始化，ptValue 包含构造函数中或通过 SetDefaultValue 以前设置的默认值。

##  <a name="getx"></a>  CAnimationPoint::GetX

提供访问权限的 CAnimationVariable X 坐标。

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>返回值

对封装 CAnimationVariable 表示 X 坐标。

### <a name="remarks"></a>备注

可以调用此方法以获取直接访问基础 CAnimationVariable 表示 X 坐标。

##  <a name="gety"></a>  CAnimationPoint::GetY

提供对 CAnimationVariable Y 坐标的访问。

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>返回值

对封装 CAnimationVariable 表示 Y 坐标的引用。

### <a name="remarks"></a>备注

可以调用此方法以获取直接访问基础 CAnimationVariable 表示 Y 坐标。

##  <a name="m_xvalue"></a>  CAnimationPoint::m_xValue

封装的动画变量表示 X 坐标的动画点。

```
CAnimationVariable m_xValue;
```

##  <a name="m_yvalue"></a>  CAnimationPoint::m_yValue

封装的动画变量，表示动画点的 Y 坐标。

```
CAnimationVariable m_yValue;
```

##  <a name="operator_cpoint"></a>  CAnimationPoint::operator CPoint

转换为 CPoint CAnimationPoint。

```
operator CPoint();
```

### <a name="return-value"></a>返回值

CAnimationPoint CPoint 作为当前值。

### <a name="remarks"></a>备注

此函数在内部调用 GetValue。 如果出于某种原因 GetValue 失败，则返回的点将包含默认值，x 和 Y 坐标。

##  <a name="operator_eq"></a>  CAnimationPoint::operator=

将 ptSrc 分配给 CAnimationPoint。

```
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>参数

*ptSrc*<br/>
是指 CPoint 或点。

### <a name="remarks"></a>备注

将 ptSrc 分配给 CAnimationPoint。 建议执行，动画开始之前，因为此运算符会调用 SetDefaultValue，这将重新创建基础 COM 对象的 X 和 Y 坐标表示如果已创建。 如果你订阅事件 （ValueChanged 或 IntegerValueChanged） 此动画对象，您需要重新启用这些事件。

##  <a name="setdefaultvalue"></a>  CAnimationPoint::SetDefaultValue

设置默认值。

```
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>参数

*ptDefault*<br/>
指定默认点值。

### <a name="remarks"></a>备注

此函数用于将默认值设置为动画对象。 此方法分配默认值分配给动画点的 X 和 Y 坐标。 它还重新创建底层的 COM 对象，如果已创建。 如果你订阅事件 （ValueChanged 或 IntegerValueChanged） 此动画对象，您需要重新启用这些事件。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
