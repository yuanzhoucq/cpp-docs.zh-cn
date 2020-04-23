---
title: CAnimationSize 类
ms.date: 11/04/2016
f1_keywords:
- CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCX
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCY
- AFXANIMATIONCONTROLLER/CAnimationSize::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetValue
- AFXANIMATIONCONTROLLER/CAnimationSize::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cxValue
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cyValue
helpviewer_keywords:
- CAnimationSize [MFC], CAnimationSize
- CAnimationSize [MFC], AddTransition
- CAnimationSize [MFC], GetCX
- CAnimationSize [MFC], GetCY
- CAnimationSize [MFC], GetDefaultValue
- CAnimationSize [MFC], GetValue
- CAnimationSize [MFC], SetDefaultValue
- CAnimationSize [MFC], GetAnimationVariableList
- CAnimationSize [MFC], m_cxValue
- CAnimationSize [MFC], m_cyValue
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
ms.openlocfilehash: 1f4a5b8b52d8bd37d1ed83618e7451dd85f84c32
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755114"
---
# <a name="canimationsize-class"></a>CAnimationSize 类

实现可对大小对象的维度进行动画处理的大小对象功能。

## <a name="syntax"></a>语法

```
class CAnimationSize : public CAnimationBaseObject;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[动画大小：动画大小](#canimationsize)|已重载。 构造动画大小对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[动画大小：：添加转换](#addtransition)|添加宽度和高度的过渡。|
|[动画大小：获取CX](#getcx)|提供对表示宽度的"动画变量"的访问。|
|[动画大小：获取](#getcy)|提供对表示高度的 CAnimation 变量的访问。|
|[动画大小：获取默认值](#getdefaultvalue)|返回"宽度"和"高度"的默认值。|
|[动画大小：获取价值](#getvalue)|返回当前值。|
|[动画大小：设置默认值](#setdefaultvalue)|设置默认值。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[动画大小：获取动画变量列表](#getanimationvariablelist)|将封装的动画变量放入列表中。 （覆盖[动画基础对象：获取动画变量列表](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。|

### <a name="public-operators"></a>公共运算符

|名称|说明|
|----------|-----------------|
|[动画大小：：运算符 CSize](#operator_csize)|将"动画大小"转换为"CSize"。|
|[动画大小：：操作员*](#operator_eq)|将 szSrc 分配给 CAnimationSize。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[动画大小：：m_cxValue](#m_cxvalue)|表示动画大小宽度的封装动画变量。|
|[动画大小：：m_cyValue](#m_cyvalue)|表示动画大小高度的封装动画变量。|

## <a name="remarks"></a>备注

CAnimationSize 类封装了两个 CAnimationvariable 对象，可以在应用程序中表示大小。 例如，可以使用此类为屏幕上任何二维对象的大小（如矩形、控件等）设置动画。 要在应用程序中使用此类，只需实例化此类的对象，请使用 CAnimationController：：addAnimationObject 将其添加到动画控制器，并调用要应用于宽度和/或高度的每个转换的 AddTransition。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[动画基础对象](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationSize`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="canimationsizeaddtransition"></a><a name="addtransition"></a>动画大小：：添加转换

添加宽度和高度的过渡。

```cpp
void AddTransition(
    CBaseTransition* pCXTransition,
    CBaseTransition* pCYTransition);
```

### <a name="parameters"></a>参数

*pCX 转换*<br/>
指向宽度过渡的指针。

*pCY 转换*<br/>
指向高度过渡的指针。

### <a name="remarks"></a>备注

调用此函数以将指定的过渡添加到要应用于"宽度"和"高"的动画变量的内部过渡列表中。 添加转换时，不会立即应用这些转换并存储在内部列表中。 当您调用 CAnimationController：：AnimateGroup 时，将应用转换（添加到特定值的情节提要中）。 如果不需要将转换应用于其中一个维度，则可以传递 NULL。

## <a name="canimationsizecanimationsize"></a><a name="canimationsize"></a>动画大小：动画大小

构造动画大小对象。

```
CAnimationSize();

CAnimationSize(
    const CSize& szDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>参数

*szDefault*<br/>
指定默认大小。

*n集团ID*<br/>
指定组 ID。

*nObjectID*<br/>
指定对象 ID。

*dwUserData*<br/>
指定用户定义的数据。

### <a name="remarks"></a>备注

对象构造的默认值为宽度、高度、对象 ID 和组 ID，该值将设置为 0。 可以使用 SetDefaultValue 和 SetID 在运行时稍后更改它们。

## <a name="canimationsizegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>动画大小：获取动画变量列表

将封装的动画变量放入列表中。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>参数

*Lst*<br/>
当函数返回时，它包含指向表示宽度和高度的两个 CAnimation 变量对象的指针。

## <a name="canimationsizegetcx"></a><a name="getcx"></a>动画大小：获取CX

提供对表示宽度的"动画变量"的访问。

```
CAnimationVariable& GetCX();
```

### <a name="return-value"></a>返回值

对表示宽度的封装的 C动画变量的引用。

### <a name="remarks"></a>备注

可以调用此方法来直接访问表示宽度的基础 C动画变量。

## <a name="canimationsizegetcy"></a><a name="getcy"></a>动画大小：获取

提供对表示高度的 CAnimation 变量的访问。

```
CAnimationVariable& GetCY();
```

### <a name="return-value"></a>返回值

对表示高度的封装的 C动画变量的引用。

### <a name="remarks"></a>备注

可以调用此方法来直接访问表示高度的基础 C动画变量。

## <a name="canimationsizegetdefaultvalue"></a><a name="getdefaultvalue"></a>动画大小：获取默认值

返回"宽度"和"高度"的默认值。

```
CSize GetDefaultValue();
```

### <a name="return-value"></a>返回值

包含默认值的 CSize 对象。

### <a name="remarks"></a>备注

调用此函数以检索以前由构造函数或 SetDefaultValue 设置的默认值。

## <a name="canimationsizegetvalue"></a><a name="getvalue"></a>动画大小：获取价值

返回当前值。

```
BOOL GetValue(CSize& szValue);
```

### <a name="parameters"></a>参数

*szValue*<br/>
输出。 当此方法返回时，包含当前值。

### <a name="return-value"></a>返回值

TRUE，如果成功检索当前值;如果成功检索当前值，则为 TRUE。否则 FALSE。

### <a name="remarks"></a>备注

调用此函数以检索动画大小的当前值。 如果此方法失败或"宽度和大小"的基础 COM 对象尚未初始化，szValue 包含默认值，该默认值以前在构造函数或 SetDefaultValue 中设置。

## <a name="canimationsizem_cxvalue"></a><a name="m_cxvalue"></a>动画大小：：m_cxValue

表示动画大小宽度的封装动画变量。

```
CAnimationVariable m_cxValue;
```

## <a name="canimationsizem_cyvalue"></a><a name="m_cyvalue"></a>动画大小：：m_cyValue

表示动画大小高度的封装动画变量。

```
CAnimationVariable m_cyValue;
```

## <a name="canimationsizeoperator-csize"></a><a name="operator_csize"></a>动画大小：：运算符 CSize

将"动画大小"转换为"CSize"。

```
operator CSize();
```

### <a name="return-value"></a>返回值

动画大小的当前值为"大小"。

### <a name="remarks"></a>备注

此功能在内部调用 GetValue。 如果由于某种原因 GetValue 失败，则返回的大小将包含"宽度"和"高度"的默认值。

## <a name="canimationsizeoperator"></a><a name="operator_eq"></a>动画大小：：操作员*

将 szSrc 分配给 CAnimationSize。

```cpp
void operator=(const CSize& szSrc);
```

### <a name="parameters"></a>参数

*什施尔克*<br/>
指"大小"或"大小"。

### <a name="remarks"></a>备注

将 szSrc 分配给 CAnimationSize。 建议在动画启动之前执行此操作，因为此运算符称为 SetDefaultValue，如果已创建"宽度"和"高度"，则重新创建宽度和高度的基础 COM 对象。 如果将此动画对象订阅到事件（Value已更改或整数值更改），则需要重新启用这些事件。

## <a name="canimationsizesetdefaultvalue"></a><a name="setdefaultvalue"></a>动画大小：设置默认值

设置默认值。

```cpp
void SetDefaultValue(const CSize& szDefault);
```

### <a name="parameters"></a>参数

*szDefault*<br/>
指定新的默认大小。

### <a name="remarks"></a>备注

使用此函数可为动画对象设置默认值。 此方法将默认值分配给动画大小的宽度和高度。 它还会重新创建基础 COM 对象（如果已创建）。 如果将此动画对象订阅到事件（Value已更改或整数值更改），则需要重新启用这些事件。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
