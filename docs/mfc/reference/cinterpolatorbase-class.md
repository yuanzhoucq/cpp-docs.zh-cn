---
title: CInterpolatorBase 类
ms.date: 11/04/2016
f1_keywords:
- CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CreateInstance
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDependencies
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetFinalValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetCustomInterpolator
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetInitialValueAndVelocity
helpviewer_keywords:
- CInterpolatorBase [MFC], CInterpolatorBase
- CInterpolatorBase [MFC], CreateInstance
- CInterpolatorBase [MFC], GetDependencies
- CInterpolatorBase [MFC], GetDuration
- CInterpolatorBase [MFC], GetFinalValue
- CInterpolatorBase [MFC], InterpolateValue
- CInterpolatorBase [MFC], InterpolateVelocity
- CInterpolatorBase [MFC], SetCustomInterpolator
- CInterpolatorBase [MFC], SetDuration
- CInterpolatorBase [MFC], SetInitialValueAndVelocity
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
ms.openlocfilehash: d1fc675b1014ab9a099e8310b52b7458f2bff65f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916201"
---
# <a name="cinterpolatorbase-class"></a>CInterpolatorBase 类

实现回调，它在必须计算动画变量的新值时由动画 API 调用。

## <a name="syntax"></a>语法

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|`CInterpolatorBase`构造对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CInterpolatorBase::CreateInstance](#createinstance)|创建的`CInterpolatorBase`实例, 并存储指向将处理事件的自定义内插程序的指针。|
|[CInterpolatorBase::GetDependencies](#getdependencies)|获取内插程序的依赖项。 （重写 `CUIAnimationInterpolatorBase::GetDependencies`。）|
|[CInterpolatorBase::GetDuration](#getduration)|获取内插程序的持续时间。 （重写 `CUIAnimationInterpolatorBase::GetDuration`。）|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|获取该内插的最终值。 （重写 `CUIAnimationInterpolatorBase::GetFinalValue`。）|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|按给定的偏移量 (重写`CUIAnimationInterpolatorBase::InterpolateValue`) 插值。|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|按给定的偏移量 (重写`CUIAnimationInterpolatorBase::InterpolateVelocity`) 内插速度。|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|存储一个指向自定义内插的指针, 该指针将处理事件。|
|[CInterpolatorBase::SetDuration](#setduration)|设置内插程序的持续时间`CUIAnimationInterpolatorBase::SetDuration`(重写)。|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|设置内插程序的初始值和速度。 （重写 `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`。）|

## <a name="remarks"></a>备注

创建`IUIAnimationTransitionFactory::CreateTransition` 对象`CCustomTransition`时, 将创建此处理程序, 并将其传递到动画初始化过程 (由`CAnimationController::AnimateGroup`启动) 的一部分。 通常不需要直接使用此类, 它只是将所有事件从者到`CCustomInterpolator`派生类中, 其指针传递到的`CCustomTransition`构造函数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="cinterpolatorbase"></a>CInterpolatorBase:: CInterpolatorBase

构造 CInterpolatorBase 对象。

```
CInterpolatorBase();
```

##  <a name="createinstance"></a>CInterpolatorBase:: CreateInstance

创建 CInterpolatorBase 的实例, 并存储指向将处理事件的自定义内插程序的指针。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>参数

*pInterpolator*<br/>
指向自定义内插的指针。

*ppHandler*<br/>
输出. 当函数返回时, 包含指向 CInterpolatorBase 实例的指针。

### <a name="return-value"></a>返回值

##  <a name="getdependencies"></a>CInterpolatorBase:: GetDependencies

获取内插程序的依赖项。

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>参数

*initialValueDependencies*<br/>
输出. 依赖于传递给 SetInitialValueAndVelocity 的初始值的内插程序的各个方面。

*initialVelocityDependencies*<br/>
输出. 取决于传递到 SetInitialValueAndVelocity 的初始速度的内插程序的各个方面。

*durationDependencies*<br/>
输出. 取决于传递到 SetDuration 的持续时间的内插程序的各个方面。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 S_OK。 如果未设置 CCustomInterpolator, 或自定义实现从 GetDependencies 方法返回 FALSE, 则返回 E_FAIL。

##  <a name="getduration"></a>CInterpolatorBase:: GetDuration

获取内插程序的持续时间。

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>参数

*duration*<br/>
输出. 转换的持续时间 (以秒为单位)。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 S_OK。 如果未设置 CCustomInterpolator, 或自定义实现从 GetDuration 方法返回 FALSE, 则返回 E_FAIL。

##  <a name="getfinalvalue"></a>CInterpolatorBase:: GetFinalValue

获取该内插的最终值。

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>参数

*值*<br/>
输出. 转换结束时变量的最终值。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 S_OK。 如果未设置 CCustomInterpolator, 或自定义实现从 GetFinalValue 方法返回 FALSE, 则返回 E_FAIL。

##  <a name="interpolatevalue"></a>CInterpolatorBase:: InterpolateValue

按给定的偏移量内插值

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>参数

*offset*<br/>
与转换开头之间的偏移量。 偏移量始终大于或等于零, 并且小于转换的持续时间。 如果转换的持续时间为零, 则不会调用此方法。

*值*<br/>
输出. 内插值。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 S_OK。 如果未设置 CCustomInterpolator, 或自定义实现从 InterpolateValue 方法返回 FALSE, 则返回 E_FAIL。

##  <a name="interpolatevelocity"></a>CInterpolatorBase:: InterpolateVelocity

按给定的偏移量内插速度

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>参数

*offset*<br/>
与转换开头之间的偏移量。 偏移量始终大于或等于零且小于或等于转换的持续时间。 如果转换的持续时间为零, 则不会调用此方法。

*velocity*<br/>
输出. 变量在偏移量处的速度。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 S_OK。 如果未设置 CCustomInterpolator, 或自定义实现从 InterpolateVelocity 方法返回 FALSE, 则返回 E_FAIL。

##  <a name="setcustominterpolator"></a>CInterpolatorBase:: SetCustomInterpolator

存储一个指向自定义内插的指针, 该指针将处理事件。

```
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>参数

*pInterpolator*<br/>
指向自定义内插的指针。

##  <a name="setduration"></a>CInterpolatorBase:: SetDuration

设置内插程序的持续时间

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>参数

*duration*<br/>
转换的持续时间。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 S_OK。 如果未设置 CCustomInterpolator, 或自定义实现从 SetDuration 方法返回 FALSE, 则返回 E_FAIL。

##  <a name="setinitialvalueandvelocity"></a>CInterpolatorBase:: SetInitialValueAndVelocity

设置内插程序的初始值和速度。

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>参数

*initialValue*<br/>
转换开始时变量的值。

*initialVelocity*<br/>
变量在转换开始时的速度。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 S_OK。 如果未设置 CCustomInterpolator, 或自定义实现从 SetInitialValueAndVelocity 方法返回 FALSE, 则返回 E_FAIL。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
