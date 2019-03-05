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
ms.openlocfilehash: 379aa5607e459ad8acfd99c5899315afb84ac4a3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57302281"
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
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|构造`CInterpolatorBase`对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CInterpolatorBase::CreateInstance](#createinstance)|创建的实例`CInterpolatorBase`和存储指向自定义内插器，将处理事件。|
|[CInterpolatorBase::GetDependencies](#getdependencies)|获取该内插器的依赖项。 （重写 `CUIAnimationInterpolatorBase::GetDependencies`。）|
|[CInterpolatorBase::GetDuration](#getduration)|获取该内插器的持续时间。 （重写 `CUIAnimationInterpolatorBase::GetDuration`。）|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|获取该内插器导致的最终值。 （重写 `CUIAnimationInterpolatorBase::GetFinalValue`。）|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|给定的偏移量处的值的内插 (重写`CUIAnimationInterpolatorBase::InterpolateValue`。)|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|内插在给定的偏移量的速度 (重写`CUIAnimationInterpolatorBase::InterpolateVelocity`。)|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|存储指向自定义内插器，将处理事件。|
|[CInterpolatorBase::SetDuration](#setduration)|设置内插器的持续时间 (重写`CUIAnimationInterpolatorBase::SetDuration`。)|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|设置内插器的初始值和速度。 （重写 `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`。）|

## <a name="remarks"></a>备注

创建此处理程序并将其传递给`IUIAnimationTransitionFactory::CreateTransition`时`CCustomTransition`正在动画初始化过程的一部分创建对象 (由启动`CAnimationController::AnimateGroup`)。 通常无需直接使用此类，它只是 routs 到的所有事件`CCustomInterpolator`的派生的类，其指针传递到构造函数的`CCustomTransition`。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="cinterpolatorbase"></a>  CInterpolatorBase::CInterpolatorBase

构造 CInterpolatorBase 对象。

```
CInterpolatorBase();
```

##  <a name="createinstance"></a>  CInterpolatorBase::CreateInstance

创建的 CInterpolatorBase 实例和存储指向自定义内插器，将处理事件。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>参数

*pInterpolator*<br/>
自定义内插器指向的指针。

*ppHandler*<br/>
输出。 在函数返回时包含指向 CInterpolatorBase 实例的指针。

### <a name="return-value"></a>返回值

##  <a name="getdependencies"></a>  CInterpolatorBase::GetDependencies

获取该内插器的依赖项。

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>参数

*initialValueDependencies*<br/>
输出。 取决于初始值的内插器方面传递给 SetInitialValueAndVelocity。

*initialVelocityDependencies*<br/>
输出。 取决于初始速度的内插器方面传递给 SetInitialValueAndVelocity。

*durationDependencies*<br/>
输出。 依赖于持续时间内插器方面传递给 SetDuration。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 如果未设置 CCustomInterpolator，或自定义实现从一个 GetDependencies 方法将返回 FALSE，则返回 E_FAIL。

##  <a name="getduration"></a>  CInterpolatorBase::GetDuration

获取该内插器的持续时间。

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>参数

*duration*<br/>
输出。 转换以秒为单位的持续时间。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 如果未设置 CCustomInterpolator，或自定义实现从 GetDuration 方法将返回 FALSE，则返回 E_FAIL。

##  <a name="getfinalvalue"></a>  CInterpolatorBase::GetFinalValue

获取该内插器导致的最终值。

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>参数

*值*<br/>
输出。 转换结束时变量的最终值。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 如果未设置 CCustomInterpolator，或自定义实现从 GetFinalValue 方法将返回 FALSE，则返回 E_FAIL。

##  <a name="interpolatevalue"></a>  CInterpolatorBase::InterpolateValue

给定的偏移量处的值的内插

```
IFACEMETHOD(InterpolateValue)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* value);
```

### <a name="parameters"></a>参数

*offset*<br/>
从过渡的开头的偏移量。 偏移量始终为大于或等于零且小于过渡的持续时间。 如果转换的持续时间为零，不调用此方法。

*值*<br/>
输出。 内插的值。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 如果未设置 CCustomInterpolator，或自定义实现从 InterpolateValue 方法将返回 FALSE，则返回 E_FAIL。

##  <a name="interpolatevelocity"></a>  CInterpolatorBase::InterpolateVelocity

内插在给定的偏移量的速度

```
IFACEMETHOD(InterpolateVelocity)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* velocity);
```

### <a name="parameters"></a>参数

*offset*<br/>
从过渡的开头的偏移量。 偏移量始终是大于或等于零且小于或等于过渡的持续时间。 如果转换的持续时间为零，不调用此方法。

*velocity*<br/>
输出。 变量的偏移量处的方向的速度。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 如果未设置 CCustomInterpolator，或自定义实现从 InterpolateVelocity 方法将返回 FALSE，则返回 E_FAIL。

##  <a name="setcustominterpolator"></a>  CInterpolatorBase::SetCustomInterpolator

存储指向自定义内插器，将处理事件。

```
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>参数

*pInterpolator*<br/>
自定义内插器指向的指针。

##  <a name="setduration"></a>  CInterpolatorBase::SetDuration

内插器的持续时间设置

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>参数

*duration*<br/>
过渡的持续时间。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 如果未设置 CCustomInterpolator，或自定义实现 SetDuration 方法将返回 FALSE，则返回 E_FAIL。

##  <a name="setinitialvalueandvelocity"></a>  CInterpolatorBase::SetInitialValueAndVelocity

设置内插器的初始值和速度。

```
IFACEMETHOD(SetInitialValueAndVelocity)(
  __in DOUBLE initialValue,
  __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>参数

*initialValue*<br/>
在过渡的开头的变量的值。

*initialVelocity*<br/>
在过渡的开头的变量的方向的速度。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 如果未设置 CCustomInterpolator，或自定义实现从 SetInitialValueAndVelocity 方法将返回 FALSE，则返回 E_FAIL。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
