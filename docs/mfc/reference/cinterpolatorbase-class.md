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
ms.openlocfilehash: efa08aa5dd556d7e136323c31451a9f33bd72ec6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754956"
---
# <a name="cinterpolatorbase-class"></a>CInterpolatorBase 类

实现回调，它在必须计算动画变量的新值时由动画 API 调用。

## <a name="syntax"></a>语法

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[C插值器基础：C插值器基础](#cinterpolatorbase)|构造`CInterpolatorBase`对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C插值器基础：：创建实例](#createinstance)|创建 的`CInterpolatorBase`实例并存储指向自定义插值器的指针，该指针将处理事件。|
|[CInterpolatorBase：获取依赖性](#getdependencies)|获取插值器的依赖项。 （重写 `CUIAnimationInterpolatorBase::GetDependencies`。）|
|[C插值器基础：获取持续时间](#getduration)|获取插值器的持续时间。 （重写 `CUIAnimationInterpolatorBase::GetDuration`。）|
|[C插值器基础：获取最终值](#getfinalvalue)|获取插值器引由的最终值。 （重写 `CUIAnimationInterpolatorBase::GetFinalValue`。）|
|[C插值器基础：：刑警价值](#interpolatevalue)|插值在给定偏移量处的值（覆盖`CUIAnimationInterpolatorBase::InterpolateValue`. ）|
|[C插值器基础：：刑警组织](#interpolatevelocity)|插值在给定偏移处的速度（覆盖`CUIAnimationInterpolatorBase::InterpolateVelocity`. ）|
|[C插值器基础：设置自定义器](#setcustominterpolator)|存储指向自定义插值器的指针，该指针将处理事件。|
|[C插值器基础：：设置持续时间](#setduration)|设置插值器的持续时间（覆盖`CUIAnimationInterpolatorBase::SetDuration`.）|
|[C插值器基础：：设置初始值和速度](#setinitialvalueandvelocity)|设置插值器的初始值和速度。 （重写 `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`。）|

## <a name="remarks"></a>备注

当`IUIAnimationTransitionFactory::CreateTransition``CCustomTransition`对象作为动画初始化过程的一部分（由 启动）`CAnimationController::AnimateGroup`创建并传递给该处理程序时， 通常不需要直接使用此类，它只是将所有事件传递给`CCustomInterpolator`派生类，其指针传递给 的`CCustomTransition`构造函数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="cinterpolatorbasecinterpolatorbase"></a><a name="cinterpolatorbase"></a>C插值器基础：C插值器基础

构造 C插值器基础对象。

```
CInterpolatorBase();
```

## <a name="cinterpolatorbasecreateinstance"></a><a name="createinstance"></a>C插值器基础：：创建实例

创建 CInterpolatorBase 的实例并存储指向自定义插值器的指针，该指针将处理事件。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>参数

*p插值器*<br/>
指向自定义插值器的指针。

*普汉德勒*<br/>
输出。 当函数返回时，包含指向 CInterpolatorBase 实例的指针。

### <a name="return-value"></a>返回值

## <a name="cinterpolatorbasegetdependencies"></a><a name="getdependencies"></a>CInterpolatorBase：获取依赖性

获取插值器的依赖项。

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>参数

*初始价值依赖性*<br/>
输出。 插值器的一些方面，这些插值取决于传递给 Set初始值和Velocity 的初始值。

*初始速度依赖性*<br/>
输出。 插值器的方面，这些插值器取决于传递给 Set 初始值和Velocity的初始速度。

*持续时间 依赖*<br/>
输出。 插值器的一些方面，这些插值器取决于传递给 SetDuration 的持续时间。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 如果未设置 CCustomInterpolator，则返回E_FAIL，或者自定义实现从 GetDependencies 方法返回 FALSE。

## <a name="cinterpolatorbasegetduration"></a><a name="getduration"></a>C插值器基础：获取持续时间

获取插值器的持续时间。

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>参数

*duration*<br/>
输出。 转换的持续时间，以秒为单位。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 如果未设置 CCustomInterpolator，则返回E_FAIL，或者自定义实现从 GetDuration 方法返回 FALSE。

## <a name="cinterpolatorbasegetfinalvalue"></a><a name="getfinalvalue"></a>C插值器基础：获取最终值

获取插值器引由的最终值。

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>参数

*value*<br/>
输出。 转换结束时变量的最终值。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 如果未设置 CCustomInterpolator，则返回E_FAIL，或者自定义实现从 GetFinalValue 方法返回 FALSE。

## <a name="cinterpolatorbaseinterpolatevalue"></a><a name="interpolatevalue"></a>C插值器基础：：刑警价值

插值在给定偏移量处的值

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>参数

*偏移量*<br/>
转换开始时的偏移量。 偏移量始终大于或等于零，小于转换的持续时间。 如果转换的持续时间为零，则不调用此方法。

*value*<br/>
输出。 插值值。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 如果未设置 CCustomInterpolator，或者自定义实现从插值值方法返回 FALSE，则返回E_FAIL。

## <a name="cinterpolatorbaseinterpolatevelocity"></a><a name="interpolatevelocity"></a>C插值器基础：：刑警组织

在给定偏移处插入速度

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>参数

*偏移量*<br/>
转换开始时的偏移量。 偏移量始终大于或等于零，小于或等于转换的持续时间。 如果转换的持续时间为零，则不调用此方法。

*velocity*<br/>
输出。 偏移处变量的速度。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 如果未设置 CCustomInterpolator，或者自定义实现从插值速度方法返回 FALSE，则返回E_FAIL。

## <a name="cinterpolatorbasesetcustominterpolator"></a><a name="setcustominterpolator"></a>C插值器基础：设置自定义器

存储指向自定义插值器的指针，该指针将处理事件。

```cpp
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>参数

*p插值器*<br/>
指向自定义插值器的指针。

## <a name="cinterpolatorbasesetduration"></a><a name="setduration"></a>C插值器基础：：设置持续时间

设置插值器的持续时间

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>参数

*duration*<br/>
转换的持续时间。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 如果未设置 CCustomInterpolator，或者自定义实现从 SetDuration 方法返回 FALSE，则返回E_FAIL。

## <a name="cinterpolatorbasesetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>C插值器基础：：设置初始值和速度

设置插值器的初始值和速度。

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>参数

*初始值*<br/>
转换开始时变量的值。

*初始速度*<br/>
转换开始时变量的速度。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 如果未设置 CCustomInterpolator，则返回E_FAIL，或者自定义实现从 Set初始值和Velocity 方法返回 FALSE。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
