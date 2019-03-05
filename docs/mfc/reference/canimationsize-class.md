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
ms.openlocfilehash: f52016afe39da900dca4847d29beccb97d829b60
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258250"
---
# <a name="canimationsize-class"></a>CAnimationSize 类

实现可对大小对象的维度进行动画处理的大小对象功能。

## <a name="syntax"></a>语法

```
class CAnimationSize : public CAnimationBaseObject;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAnimationSize::CAnimationSize](#canimationsize)|已重载。 构造一个动画大小对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAnimationSize::AddTransition](#addtransition)|添加转换的宽度和高度。|
|[CAnimationSize::GetCX](#getcx)|提供访问权限 CAnimationVariable 表示宽度。|
|[CAnimationSize::GetCY](#getcy)|提供访问权限 CAnimationVariable 表示高度。|
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|返回默认值为宽度和高度。|
|[CAnimationSize::GetValue](#getvalue)|返回当前值。|
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|设置默认值。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|将封装的动画变量放入列表。 (重写[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist)。)|

### <a name="public-operators"></a>公共运算符

|名称|描述|
|----------|-----------------|
|[CAnimationSize::operator CSize](#operator_csize)|将一 CAnimationSize 转换为 CSize。|
|[CAnimationSize::operator=](#operator_eq)|将 szSrc 分配给 CAnimationSize。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CAnimationSize::m_cxValue](#m_cxvalue)|表示动画大小的宽度的封装的动画变量。|
|[CAnimationSize::m_cyValue](#m_cyvalue)|表示动画大小的高度的封装的动画变量。|

## <a name="remarks"></a>备注

CAnimationSize 类封装两个 CAnimationVariable 对象，并可以表示在应用程序中的大小。 例如，可以使用此类进行动画处理的任何两个大小在屏幕上的维对象 (如矩形，控制等)。 若要使用此类应用程序中，只需实例化此类的对象、 将其添加到动画控制器使用 CAnimationController::AddAnimationObject 和调用每个转换下要应用于宽度和/或高度。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationSize`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationSize::AddTransition

添加转换的宽度和高度。

```
void AddTransition(
    CBaseTransition* pCXTransition,
    CBaseTransition* pCYTransition);
```

### <a name="parameters"></a>参数

*pCXTransition*<br/>
指向宽度的转换的指针。

*pCYTransition*<br/>
指向转换高度的指针。

### <a name="remarks"></a>备注

调用此函数可指定的转换添加到转换将应用于动画变量的宽度和高度的内部列表。 添加转换，它们不会立即应用并存储在内部列表。 转换应用 （已添加到情节提要的特定值） 当你调用 CAnimationController::AnimateGroup。 如果不需要将转换应用到一个维度，则可以传递 NULL。

##  <a name="canimationsize"></a>  CAnimationSize::CAnimationSize

构造一个动画大小对象。

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

*nGroupID*<br/>
指定组 id。

*nObjectID*<br/>
指定对象 id。

*dwUserData*<br/>
指定用户定义的数据。

### <a name="remarks"></a>备注

对象使用的宽度、 高度，默认值构造的对象 ID 和组 ID，将设置为 0。 它们可以在运行时使用 SetDefaultValue SetID 以后更改。

##  <a name="getanimationvariablelist"></a>  CAnimationSize::GetAnimationVariableList

将封装的动画变量放入列表。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>参数

*lst*<br/>
该函数返回时，它包含指向表示宽度和高度的两个 CAnimationVariable 对象的指针。

##  <a name="getcx"></a>  CAnimationSize::GetCX

提供访问权限 CAnimationVariable 表示宽度。

```
CAnimationVariable& GetCX();
```

### <a name="return-value"></a>返回值

对封装 CAnimationVariable 表示宽度的引用。

### <a name="remarks"></a>备注

可以调用此方法以获取直接访问基础 CAnimationVariable 表示宽度。

##  <a name="getcy"></a>  CAnimationSize::GetCY

提供访问权限 CAnimationVariable 表示高度。

```
CAnimationVariable& GetCY();
```

### <a name="return-value"></a>返回值

对封装 CAnimationVariable 表示高度的引用。

### <a name="remarks"></a>备注

可以调用此方法以获取直接访问基础 CAnimationVariable 表示高度。

##  <a name="getdefaultvalue"></a>  CAnimationSize::GetDefaultValue

返回默认值为宽度和高度。

```
CSize GetDefaultValue();
```

### <a name="return-value"></a>返回值

CSize 对象，包含默认值。

### <a name="remarks"></a>备注

调用此函数检索以前已由构造函数或 SetDefaultValue 设置的默认值。

##  <a name="getvalue"></a>  CAnimationSize::GetValue

返回当前值。

```
BOOL GetValue(CSize& szValue);
```

### <a name="parameters"></a>参数

*szValue*<br/>
输出。 此方法返回时包含的当前值。

### <a name="return-value"></a>返回值

已成功检索当前值; 如果为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

调用此函数可检索当前动画大小的值。 如果此方法失败或尚未初始化基础 COM 对象的宽度和大小，szValue 包含构造函数中或通过 SetDefaultValue 以前设置的默认值。

##  <a name="m_cxvalue"></a>  CAnimationSize::m_cxValue

表示动画大小的宽度的封装的动画变量。

```
CAnimationVariable m_cxValue;
```

##  <a name="m_cyvalue"></a>  CAnimationSize::m_cyValue

表示动画大小的高度的封装的动画变量。

```
CAnimationVariable m_cyValue;
```

##  <a name="operator_csize"></a>  CAnimationSize::operator CSize

将一 CAnimationSize 转换为 CSize。

```
operator CSize();
```

### <a name="return-value"></a>返回值

与 CSize 动画大小的当前值。

### <a name="remarks"></a>备注

此函数在内部调用 GetValue。 如果出于某种原因 GetValue 失败，返回的大小将宽度和高度包含默认值。

##  <a name="operator_eq"></a>  CAnimationSize::operator=

将 szSrc 分配给 CAnimationSize。

```
void operator=(const CSize& szSrc);
```

### <a name="parameters"></a>参数

*szSrc*<br/>
是指 CSize 或大小。

### <a name="remarks"></a>备注

将 szSrc 分配给 CAnimationSize。 建议为此动画开始之前，原因是此运算符将调用 SetDefaultValue，宽度和高度为重新创建底层的 COM 对象，如果已创建。 如果你订阅事件 （ValueChanged 或 IntegerValueChanged） 此动画对象，您需要重新启用这些事件。

##  <a name="setdefaultvalue"></a>  CAnimationSize::SetDefaultValue

设置默认值。

```
void SetDefaultValue(const CSize& szDefault);
```

### <a name="parameters"></a>参数

*szDefault*<br/>
指定新的默认大小。

### <a name="remarks"></a>备注

此函数用于将默认值设置为动画对象。 此方法将默认值分配到动画大小的宽度和高度。 它还重新创建底层的 COM 对象，如果已创建。 如果你订阅事件 （ValueChanged 或 IntegerValueChanged） 此动画对象，您需要重新启用这些事件。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
