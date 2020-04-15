---
title: CAnimationColor 类
ms.date: 11/04/2016
f1_keywords:
- CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationColor::GetB
- AFXANIMATIONCONTROLLER/CAnimationColor::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetG
- AFXANIMATIONCONTROLLER/CAnimationColor::GetR
- AFXANIMATIONCONTROLLER/CAnimationColor::GetValue
- AFXANIMATIONCONTROLLER/CAnimationColor::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationColor::m_bValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_gValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_rValue
helpviewer_keywords:
- CAnimationColor [MFC], CAnimationColor
- CAnimationColor [MFC], AddTransition
- CAnimationColor [MFC], GetB
- CAnimationColor [MFC], GetDefaultValue
- CAnimationColor [MFC], GetG
- CAnimationColor [MFC], GetR
- CAnimationColor [MFC], GetValue
- CAnimationColor [MFC], SetDefaultValue
- CAnimationColor [MFC], GetAnimationVariableList
- CAnimationColor [MFC], m_bValue
- CAnimationColor [MFC], m_gValue
- CAnimationColor [MFC], m_rValue
ms.assetid: 88bfabd4-efeb-4652-87e8-304253d8e48c
ms.openlocfilehash: 5940cce6d55b95d8e1bac103cacc0bc828c213de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371110"
---
# <a name="canimationcolor-class"></a>CAnimationColor 类

实现可对颜色的红色、绿色和蓝色分量进行动画处理的颜色功能。

## <a name="syntax"></a>语法

```
class CAnimationColor : public CAnimationBaseObject;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[动画颜色：：动画颜色](#canimationcolor)|已重载。 构造动画颜色对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[动画颜色：：添加转换](#addtransition)|添加红色、绿色和蓝色组件的过渡。|
|[动画颜色：获取B](#getb)|提供对表示蓝色组件的 CAnimation 变量的访问。|
|[动画颜色：获取默认值](#getdefaultvalue)|返回颜色组件的默认值。|
|[动画颜色：获取G](#getg)|提供对表示绿色组件的 CAnimation 变量的访问。|
|[动画颜色：GetR](#getr)|提供对表示红色组件的 CAnimation 变量的访问。|
|[动画颜色：获取价值](#getvalue)|返回当前值。|
|[动画颜色：：设置默认值](#setdefaultvalue)|设置默认值。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[动画颜色：：获取动画变量列表](#getanimationvariablelist)|将封装的动画变量放入列表中。 （覆盖[动画基础对象：获取动画变量列表](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[动画颜色：：运算符 COLORREF](#operator_colorref)||
|[动画颜色：：运算符*](#operator_eq)|将颜色分配给 CAnimationColor。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[动画颜色：：m_bValue](#m_bvalue)|表示动画颜色的蓝色分量的封装动画变量。|
|[动画颜色：m_gValue](#m_gvalue)|表示动画颜色的绿色分量的封装动画变量。|
|[动画颜色：：m_rValue](#m_rvalue)|表示动画颜色的红色分量的封装动画变量。|

## <a name="remarks"></a>备注

CAnimationColor 类封装了三个 CAnimationVariable 对象，可以在应用程序中表示颜色。 例如，可以使用此类对屏幕上任何对象的颜色（如文本颜色、背景颜色等）进行动画处理。 要在应用程序中使用此类，只需实例化此类的对象，请使用 CAnimationController：：addAnimationObject 将其添加到动画控制器，并调用 AddTransition，以便应用于红色、绿色和蓝色组件的每个转换。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[动画基础对象](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationColor`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="canimationcoloraddtransition"></a><a name="addtransition"></a>动画颜色：：添加转换

添加红色、绿色和蓝色组件的过渡。

```
void AddTransition(
    CBaseTransition* pRTransition,
    CBaseTransition* pGTransition,
    CBaseTransition* pBTransition);
```

### <a name="parameters"></a>参数

*pR 转换*<br/>
红色组件的转换。

*pG 转换*<br/>
绿色组件的转换。

*pB 转换*<br/>
蓝色组件的转换。

### <a name="remarks"></a>备注

调用此函数以将指定的过渡添加到要应用于表示颜色分量的动画变量的内部过渡列表中。 添加转换时，不会立即应用这些转换并存储在内部列表中。 当您调用 CAnimationController：：AnimateGroup 时，将应用转换（添加到特定值的情节提要中）。 如果不需要对其中一个颜色分量应用过渡，则可以传递 NULL。

## <a name="canimationcolorcanimationcolor"></a><a name="canimationcolor"></a>动画颜色：：动画颜色

构造 C动画颜色对象。

```
CAnimationColor();

CAnimationColor(
    COLORREF color,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>参数

*颜色*<br/>
指定默认颜色。

*n集团ID*<br/>
指定组 ID。

*nObjectID*<br/>
指定对象 ID。

*dwUserData*<br/>
指定用户定义的数据。

### <a name="remarks"></a>备注

对象构造的默认值为红色、绿色、蓝色、对象 ID 和组 ID，该值将设置为 0。 可以使用 SetDefaultValue 和 SetID 在运行时稍后更改它们。

## <a name="canimationcolorgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>动画颜色：：获取动画变量列表

将封装的动画变量放入列表中。

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```

### <a name="parameters"></a>参数

*Lst*<br/>
当函数返回时，它包含指向表示红色、绿色和蓝色组件的三个 CAnimation 变量对象的指针。

## <a name="canimationcolorgetb"></a><a name="getb"></a>动画颜色：获取B

提供对表示蓝色组件的 CAnimation 变量的访问。

```
CAnimationVariable& GetB();
```

### <a name="return-value"></a>返回值

表示蓝色组件的封装 CAnimation 变量的引用。

### <a name="remarks"></a>备注

您可以调用此方法来直接访问表示 Blue 组件的基础 C动画变量。

## <a name="canimationcolorgetdefaultvalue"></a><a name="getdefaultvalue"></a>动画颜色：获取默认值

返回颜色组件的默认值。

```
COLORREF GetDefaultValue();
```

### <a name="return-value"></a>返回值

包含 RGB 组件默认值的 COLORREF 值。

### <a name="remarks"></a>备注

调用此函数以检索以前由构造函数或 SetDefaultValue 设置的默认值。

## <a name="canimationcolorgetg"></a><a name="getg"></a>动画颜色：获取G

提供对表示绿色组件的 CAnimation 变量的访问。

```
CAnimationVariable& GetG();
```

### <a name="return-value"></a>返回值

表示绿色组件的封装 CAnimation 变量的引用。

### <a name="remarks"></a>备注

您可以调用此方法来直接访问表示绿色组件的基础 C动画变量。

## <a name="canimationcolorgetr"></a><a name="getr"></a>动画颜色：GetR

提供对表示红色组件的 CAnimation 变量的访问。

```
CAnimationVariable& GetR();
```

### <a name="return-value"></a>返回值

表示红色分量的封装 CAnimation 的引用。

### <a name="remarks"></a>备注

您可以调用此方法来直接访问表示红色组件的基础 C动画变量。

## <a name="canimationcolorgetvalue"></a><a name="getvalue"></a>动画颜色：获取价值

返回当前值。

```
BOOL GetValue(COLORREF& color);
```

### <a name="parameters"></a>参数

*颜色*<br/>
输出。 当此方法返回时，包含当前值。

### <a name="return-value"></a>返回值

TRUE，如果成功检索当前值;如果成功检索当前值，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

调用此函数以检索动画颜色的当前值。 如果此方法失败或颜色组件的基础 COM 对象尚未初始化，则颜色包含默认值，该值以前在构造函数或 SetDefaultValue 中设置。

## <a name="canimationcolorm_bvalue"></a><a name="m_bvalue"></a>动画颜色：：m_bValue

表示动画颜色的蓝色分量的封装动画变量。

```
CAnimationVariable m_bValue;
```

## <a name="canimationcolorm_gvalue"></a><a name="m_gvalue"></a>动画颜色：m_gValue

表示动画颜色的绿色分量的封装动画变量。

```
CAnimationVariable m_gValue;
```

## <a name="canimationcolorm_rvalue"></a><a name="m_rvalue"></a>动画颜色：：m_rValue

表示动画颜色的红色分量的封装动画变量。

```
CAnimationVariable m_rValue;
```

## <a name="canimationcoloroperator-colorref"></a><a name="operator_colorref"></a>动画颜色：：运算符 COLORREF

```
operator COLORREF();
```

### <a name="return-value"></a>返回值

## <a name="canimationcoloroperator"></a><a name="operator_eq"></a>动画颜色：：运算符*

将颜色分配给 CAnimationColor。

```
void operator=(COLORREF color);
```

### <a name="parameters"></a>参数

*颜色*<br/>
指定新值动画颜色。

### <a name="remarks"></a>备注

建议在动画启动之前执行此操作，因为此运算符称为 SetDefaultValue，如果已创建颜色组件，则重新创建颜色组件的基础 COM 对象。 如果将此动画对象订阅到事件（Value已更改或整数值更改），则需要重新启用这些事件。

## <a name="canimationcolorsetdefaultvalue"></a><a name="setdefaultvalue"></a>动画颜色：：设置默认值

设置默认值。

```
void SetDefaultValue(COLORREF color);
```

### <a name="parameters"></a>参数

*颜色*<br/>
为红色、绿色和蓝色组件指定新的默认值。

### <a name="remarks"></a>备注

使用此函数可为动画对象设置默认值。 此方法将默认值分配给动画颜色的颜色组件。 它还会重新创建基础 COM 对象（如果已创建）。 如果将此动画对象订阅到事件（Value已更改或整数值更改），则需要重新启用这些事件。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
