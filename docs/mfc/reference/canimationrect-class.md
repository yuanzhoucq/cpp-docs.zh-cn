---
title: CAnimationRect 类
ms.date: 11/04/2016
f1_keywords:
- CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationRect::GetBottom
- AFXANIMATIONCONTROLLER/CAnimationRect::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetLeft
- AFXANIMATIONCONTROLLER/CAnimationRect::GetRight
- AFXANIMATIONCONTROLLER/CAnimationRect::GetTop
- AFXANIMATIONCONTROLLER/CAnimationRect::GetValue
- AFXANIMATIONCONTROLLER/CAnimationRect::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bFixedSize
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bottomValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_leftValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_rightValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_szInitial
- AFXANIMATIONCONTROLLER/CAnimationRect::m_topValue
helpviewer_keywords:
- CAnimationRect [MFC], CAnimationRect
- CAnimationRect [MFC], AddTransition
- CAnimationRect [MFC], GetBottom
- CAnimationRect [MFC], GetDefaultValue
- CAnimationRect [MFC], GetLeft
- CAnimationRect [MFC], GetRight
- CAnimationRect [MFC], GetTop
- CAnimationRect [MFC], GetValue
- CAnimationRect [MFC], SetDefaultValue
- CAnimationRect [MFC], GetAnimationVariableList
- CAnimationRect [MFC], m_bFixedSize
- CAnimationRect [MFC], m_bottomValue
- CAnimationRect [MFC], m_leftValue
- CAnimationRect [MFC], m_rightValue
- CAnimationRect [MFC], m_szInitial
- CAnimationRect [MFC], m_topValue
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
ms.openlocfilehash: 273ea2b548d35722ebf937d2db2b589fef5e69fa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755134"
---
# <a name="canimationrect-class"></a>CAnimationRect 类

实现可对矩形边进行动画处理的矩形功能。

## <a name="syntax"></a>语法

```
class CAnimationRect : public CAnimationBaseObject;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[动画重器：：动画Rect](#canimationrect)|已重载。 构造动画矩形对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[动画重器：：添加转换](#addtransition)|添加左、上、右和下坐标的过渡。|
|[动画重器：：获取底部](#getbottom)|提供对表示底部坐标的 CAnimation 变量的访问。|
|[动画重： ：获取默认值](#getdefaultvalue)|返回矩形边界的默认值。|
|[动画重器：：获取左](#getleft)|提供对表示左坐标的 CAnimation 变量的访问。|
|[动画重： ：获得正确](#getright)|提供对表示正确坐标的 CAnimation 变量的访问。|
|[动画重器：：获取顶部](#gettop)|提供对表示顶部坐标的 CAnimation 变量的访问。|
|[动画重器：：获取价值](#getvalue)|返回当前值。|
|[动画重定：：设置默认值](#setdefaultvalue)|设置默认值。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[动画重： ：获取动画变量列表](#getanimationvariablelist)|将封装的动画变量放入列表中。 （覆盖[动画基础对象：获取动画变量列表](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[动画重器：：操作员 RECT](#operator_rect)|将 C 动画 Rect 转换为 RECT。|
|[动画重器：：运算符*](#operator_eq)|将矩形分配给 CAnimationRect。|

### <a name="public-data-members"></a>公共数据成员

|名称|说明|
|----------|-----------------|
|[动画：：m_bFixedSize](#m_bfixedsize)|指定矩形是否具有固定大小。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[动画重器：：m_bottomValue](#m_bottomvalue)|表示动画矩形底部边界的封装动画变量。|
|[动画：：m_leftValue](#m_leftvalue)|表示动画矩形左边界的封装动画变量。|
|[动画重器：：m_rightValue](#m_rightvalue)|表示动画矩形右边界的封装动画变量。|
|[动画重器：：m_szInitial](#m_szinitial)|指定动画矩形的初始大小。|
|[动画重器：：m_topValue](#m_topvalue)|表示动画矩形的"顶部"边界的封装动画变量。|

## <a name="remarks"></a>备注

CAnimationRect 类封装了四个 CAnimationvariable 对象，可以在应用程序中表示一个矩形。 要在应用程序中使用此类，只需实例化此类的对象，请使用 CAnimationController：：addAnimationObject 将其添加到动画控制器，并调用 AddTransition，以便应用于左、右上和下坐标的每个转换。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[动画基础对象](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="canimationrectaddtransition"></a><a name="addtransition"></a>动画重器：：添加转换

添加左、上、右和下坐标的过渡。

```cpp
void AddTransition(
    CBaseTransition* pLeftTransition,
    CBaseTransition* pTopTransition,
    CBaseTransition* pRightTransition,
    CBaseTransition* pBottomTransition);
```

### <a name="parameters"></a>参数

*p 左转换*<br/>
指定左侧的过渡。

*p 上过渡*<br/>
指定顶部的过渡。

*pRight 转换*<br/>
指定右侧的过渡。

*p底转换*<br/>
指定下边的过渡。

### <a name="remarks"></a>备注

调用此函数以将指定的过渡添加到要应用于每个矩形边的动画变量的内部过渡列表中。 添加转换时，不会立即应用这些转换并存储在内部列表中。 当您调用 CAnimationController：：AnimateGroup 时，将应用转换（添加到特定值的情节提要中）。 如果不需要对矩形的一个边应用过渡，则可以传递 NULL。

## <a name="canimationrectcanimationrect"></a><a name="canimationrect"></a>动画重器：：动画Rect

构造 CAnimationRect 对象。

```
CAnimationRect();

CAnimationRect(
    const CRect& rect,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    const CPoint& pt,
    const CSize& sz,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    int nLeft,
    int nTop,
    int nRight,
    int nBottom,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>参数

*矩形*<br/>
指定默认矩形。

*n集团ID*<br/>
指定组 ID。

*nObjectID*<br/>
指定对象 ID。

*dwUserData*<br/>
指定用户定义的数据。

*pt*<br/>
左上角的坐标。

*深圳*<br/>
矩形的大小。

*n 左*<br/>
指定左绑定的坐标。

*nTop*<br/>
指定上绑定的坐标。

*nRight*<br/>
指定右绑定的坐标。

*n下角*<br/>
指定下绑定的坐标。

### <a name="remarks"></a>备注

对象构造的默认值为左、上、右和下，对象 ID 和组 ID，将设置为 0。 可以使用 SetDefaultValue 和 SetID 在运行时稍后更改它们。

## <a name="canimationrectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>动画重： ：获取动画变量列表

将封装的动画变量放入列表中。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>参数

*Lst*<br/>
当函数返回时，它包含指向表示矩形坐标的四个 CAnimation 变量对象的指针。

## <a name="canimationrectgetbottom"></a><a name="getbottom"></a>动画重器：：获取底部

提供对表示底部坐标的 CAnimation 变量的访问。

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>返回值

表示底部坐标的封装 CAnimation 变量的引用。

### <a name="remarks"></a>备注

您可以调用此方法来直接访问表示底部坐标的基础 C动画变量。

## <a name="canimationrectgetdefaultvalue"></a><a name="getdefaultvalue"></a>动画重： ：获取默认值

返回矩形边界的默认值。

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>返回值

包含左、右、上和下默认值的 CRect 值。

### <a name="remarks"></a>备注

调用此函数以检索以前由构造函数或 SetDefaultValue 设置的默认值。

## <a name="canimationrectgetleft"></a><a name="getleft"></a>动画重器：：获取左

提供对表示左坐标的 CAnimation 变量的访问。

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>返回值

表示左坐标的封装 CAnimation 变量的引用。

### <a name="remarks"></a>备注

您可以调用此方法以直接访问表示左侧坐标的基础 C动画变量。

## <a name="canimationrectgetright"></a><a name="getright"></a>动画重： ：获得正确

提供对表示正确坐标的 CAnimation 变量的访问。

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>返回值

对表示正确坐标的封装的 CAnimation 的引用。

### <a name="remarks"></a>备注

您可以调用此方法来直接访问表示正确坐标的基础 C动画变量。

## <a name="canimationrectgettop"></a><a name="gettop"></a>动画重器：：获取顶部

提供对表示顶部坐标的 CAnimation 变量的访问。

```
CAnimationVariable& GetTop();
```

### <a name="return-value"></a>返回值

表示顶部坐标的封装 CAnimation 变量的引用。

### <a name="remarks"></a>备注

您可以调用此方法来直接访问表示顶部坐标的基础 C动画变量。

## <a name="canimationrectgetvalue"></a><a name="getvalue"></a>动画重器：：获取价值

返回当前值。

```
BOOL GetValue(CRect& rect);
```

### <a name="parameters"></a>参数

*矩形*<br/>
输出。 当此方法返回时，包含当前值。

### <a name="return-value"></a>返回值

TRUE，如果成功检索当前值;如果成功检索当前值，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

调用此函数以检索动画矩形的当前值。 如果此方法失败或左、上、右和下的基础 COM 对象尚未初始化，则 rect 包含默认值，该值以前在构造函数或 SetDefaultValue 中设置。

## <a name="canimationrectm_bfixedsize"></a><a name="m_bfixedsize"></a>动画：：m_bFixedSize

指定矩形是否具有固定大小。

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>备注

如果此成员为 true，则矩形的大小是固定的，并且每次根据固定大小移动左上角时都会重新计算右和下值。 将此值设置为 TRUE 以轻松地在屏幕上移动矩形。 在这种情况下，将忽略应用于右坐标和底部坐标的过渡。 当您构造对象和/或调用 SetDefaultValue 时，大小存储在内部。 默认情况下，此成员设置为 FALSE。

## <a name="canimationrectm_bottomvalue"></a><a name="m_bottomvalue"></a>动画重器：：m_bottomValue

表示动画矩形底部边界的封装动画变量。

```
CAnimationVariable m_bottomValue;
```

## <a name="canimationrectm_leftvalue"></a><a name="m_leftvalue"></a>动画：：m_leftValue

表示动画矩形左边界的封装动画变量。

```
CAnimationVariable m_leftValue;
```

## <a name="canimationrectm_rightvalue"></a><a name="m_rightvalue"></a>动画重器：：m_rightValue

表示动画矩形右边界的封装动画变量。

```
CAnimationVariable m_rightValue;
```

## <a name="canimationrectm_szinitial"></a><a name="m_szinitial"></a>动画重器：：m_szInitial

指定动画矩形的初始大小。

```
CSize m_szInitial;
```

## <a name="canimationrectm_topvalue"></a><a name="m_topvalue"></a>动画重器：：m_topValue

表示动画矩形的"顶部"边界的封装动画变量。

```
CAnimationVariable m_topValue;
```

## <a name="canimationrectoperator-rect"></a><a name="operator_rect"></a>动画重器：：操作员 RECT

将 C 动画 Rect 转换为 RECT。

```
operator RECT();
```

### <a name="return-value"></a>返回值

动画矩形作为 RECT 的当前值。

### <a name="remarks"></a>备注

此功能在内部调用 GetValue。 如果由于某种原因 GetValue 失败，则返回的 RECT 将包含所有矩形坐标的默认值。

## <a name="canimationrectoperator"></a><a name="operator_eq"></a>动画重器：：运算符*

将矩形分配给 CAnimationRect。

```cpp
void operator=(const RECT& rect);
```

### <a name="parameters"></a>参数

*矩形*<br/>
动画矩形的新值。

### <a name="remarks"></a>备注

建议在动画启动之前执行此操作，因为此运算符称为 SetDefaultValue，如果已创建颜色组件，则重新创建颜色组件的基础 COM 对象。 如果将此动画对象订阅到事件（Value已更改或整数值更改），则需要重新启用这些事件。

## <a name="canimationrectsetdefaultvalue"></a><a name="setdefaultvalue"></a>动画重定：：设置默认值

设置默认值。

```cpp
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>参数

*矩形*<br/>
为左、上、右和下指定新的默认值。

### <a name="remarks"></a>备注

使用此函数可为动画对象设置默认值。 此方法将默认值分配给矩形的边界。 它还会重新创建基础 COM 对象（如果已创建）。 如果将此动画对象订阅到事件（Value已更改或整数值更改），则需要重新启用这些事件。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
