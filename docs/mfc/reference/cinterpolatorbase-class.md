---
title: "CInterpolatorBase 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 79cea720391127f52d441de8f02c53756790d4b2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
|[CInterpolatorBase::CreateInstance](#createinstance)|创建的实例`CInterpolatorBase`，并将存储指向自定义内插器，将处理事件的指针。|  
|[CInterpolatorBase::GetDependencies](#getdependencies)|获取插值程序的依赖项。 （重写 `CUIAnimationInterpolatorBase::GetDependencies`。）|  
|[CInterpolatorBase::GetDuration](#getduration)|获取插值程序的持续时间。 （重写 `CUIAnimationInterpolatorBase::GetDuration`。）|  
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|获取插值程序潜在顾客的最终值。 （重写 `CUIAnimationInterpolatorBase::GetFinalValue`。）|  
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|内插给定的偏移量处的值 (重写`CUIAnimationInterpolatorBase::InterpolateValue`。)|  
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|内插在给定的偏移量的速度 (重写`CUIAnimationInterpolatorBase::InterpolateVelocity`。)|  
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|存储指向自定义内插器，将处理事件。|  
|[CInterpolatorBase::SetDuration](#setduration)|设置插值程序的持续时间 (重写`CUIAnimationInterpolatorBase::SetDuration`。)|  
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|设置插值程序的初始值和速度。 （重写 `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`。）|  
  
## <a name="remarks"></a>备注  
 此处理程序是创建并传递给`IUIAnimationTransitionFactory::CreateTransition`时`CCustomTransition`对象正在创建动画初始化过程的一部分 (通过启动`CAnimationController::AnimateGroup`)。 通常无需直接使用此类情况下，它只需 routs 到的所有事件`CCustomInterpolator`-派生的类，其指针传递到构造函数的`CCustomTransition`。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationInterpolatorBase`  
  
 `CInterpolatorBase`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxanimationcontroller.h  
  
##  <a name="cinterpolatorbase"></a>CInterpolatorBase::CInterpolatorBase  
 构造 CInterpolatorBase 对象。  
  
```  
CInterpolatorBase();
```  
  
##  <a name="createinstance"></a>CInterpolatorBase::CreateInstance  
 创建的 CInterpolatorBase 实例并将存储指向自定义内插器，将处理事件的指针。  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,  
    IUIAnimationInterpolator** ppHandler);
```  
  
### <a name="parameters"></a>参数  
 `pInterpolator`  
 指向自定义插值程序的指针。  
  
 `ppHandler`  
 输出。 在函数返回时包含指向 CInterpolatorBase 实例的指针。  
  
### <a name="return-value"></a>返回值  
  
##  <a name="getdependencies"></a>CInterpolatorBase::GetDependencies  
 获取插值程序的依赖项。  
  
```  
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>参数  
 `initialValueDependencies`  
 输出。 各个方面插值程序依赖于初始的值传递给 SetInitialValueAndVelocity。  
  
 `initialVelocityDependencies`  
 输出。 各个方面插值程序依赖于的初始速度传递给 SetInitialValueAndVelocity。  
  
 `durationDependencies`  
 输出。 各个方面插值程序持续时间取决于传递给 SetDuration。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回，则为 S_OK。 如果未设置 CCustomInterpolator，或自定义实现将返回 FALSE GetDependencies 方法，它将返回 E_FAIL。  
  
##  <a name="getduration"></a>CInterpolatorBase::GetDuration  
 获取插值程序的持续时间。  
  
```  
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 输出。 转换，以秒为单位的持续时间。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回，则为 S_OK。 如果未设置 CCustomInterpolator，或自定义实现将返回 FALSE GetDuration 方法，它将返回 E_FAIL。  
  
##  <a name="getfinalvalue"></a>CInterpolatorBase::GetFinalValue  
 获取插值程序潜在顾客的最终值。  
  
```  
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```  
  
### <a name="parameters"></a>参数  
 `value`  
 输出。 变量在转换结束最终值。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回，则为 S_OK。 如果未设置 CCustomInterpolator，或自定义实现将返回 FALSE GetFinalValue 方法，它将返回 E_FAIL。  
  
##  <a name="interpolatevalue"></a>CInterpolatorBase::InterpolateValue  
 内插给定的偏移量处的值  
  
```  
IFACEMETHOD(InterpolateValue)(
  __in UI_ANIMATION_SECONDS offset, 
  __out DOUBLE* value);
```  
  
### <a name="parameters"></a>参数  
 `offset`  
 从转换的开始的偏移量。 偏移量始终是大于或等于零且小于转换的持续时间。 如果转换的持续时间为零，不会调用此方法。  
  
 `value`  
 输出。 内插的值。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回，则为 S_OK。 如果未设置 CCustomInterpolator，或自定义实现将返回 FALSE InterpolateValue 方法，它将返回 E_FAIL。  
  
##  <a name="interpolatevelocity"></a>CInterpolatorBase::InterpolateVelocity  
 内插在给定的偏移量的速度  
  
```  
IFACEMETHOD(InterpolateVelocity)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* velocity);
```  
  
### <a name="parameters"></a>参数  
 `offset`  
 从转换的开始的偏移量。 偏移量始终是大于或等于零且小于或等于转换的持续时间。 如果转换的持续时间为零，不会调用此方法。  
  
 `velocity`  
 输出。 偏移量处变量的速度。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回，则为 S_OK。 如果未设置 CCustomInterpolator，或自定义实现将返回 FALSE InterpolateVelocity 方法，它将返回 E_FAIL。  
  
##  <a name="setcustominterpolator"></a>CInterpolatorBase::SetCustomInterpolator  
 存储指向自定义内插器，将处理事件。  
  
```  
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```  
  
### <a name="parameters"></a>参数  
 `pInterpolator`  
 指向自定义插值程序的指针。  
  
##  <a name="setduration"></a>CInterpolatorBase::SetDuration  
 设置插值程序的持续时间  
  
```  
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 转换的持续时间。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回，则为 S_OK。 如果未设置 CCustomInterpolator，或自定义实现将返回 FALSE SetDuration 方法，它将返回 E_FAIL。  
  
##  <a name="setinitialvalueandvelocity"></a>CInterpolatorBase::SetInitialValueAndVelocity  
 设置插值程序的初始值和速度。  
  
```  
IFACEMETHOD(SetInitialValueAndVelocity)(
  __in DOUBLE initialValue, 
  __in DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>参数  
 `initialValue`  
 在转换的开始的变量的值。  
  
 `initialVelocity`  
 在转换的开始的变量的速度。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回，则为 S_OK。 如果未设置 CCustomInterpolator，或自定义实现将返回 FALSE SetInitialValueAndVelocity 方法，它将返回 E_FAIL。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
