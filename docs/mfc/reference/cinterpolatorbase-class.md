---
title: "CInterpolatorBase 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
dev_langs:
- C++
helpviewer_keywords:
- CInterpolatorBase class
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 44c67eef38b34a2a3cf677b42a40304c01668b42
ms.lasthandoff: 02/24/2017

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
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|构造`CInterpolatorBase`对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CInterpolatorBase::CreateInstance](#createinstance)|创建的一个实例`CInterpolatorBase`，并将存储指向自定义内插器，将处理事件的指针。|  
|[CInterpolatorBase::GetDependencies](#getdependencies)|获取该内插器依赖项。 （重写 `CUIAnimationInterpolatorBase::GetDependencies`。）|  
|[CInterpolatorBase::GetDuration](#getduration)|获取该内插器持续时间。 （重写 `CUIAnimationInterpolatorBase::GetDuration`。）|  
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|获取该内插器导致的最终值。 （重写 `CUIAnimationInterpolatorBase::GetFinalValue`。）|  
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|内插给定的偏移量处的值 (重写`CUIAnimationInterpolatorBase::InterpolateValue`。)|  
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|内插在给定的偏移量的速度 (重写`CUIAnimationInterpolatorBase::InterpolateVelocity`。)|  
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|存储自定义内插器，将处理事件的指针。|  
|[CInterpolatorBase::SetDuration](#setduration)|设置内插器的持续时间 (重写`CUIAnimationInterpolatorBase::SetDuration`。)|  
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|设置内插器的初始值和速度。 （重写 `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`。）|  
  
## <a name="remarks"></a>备注  
 此处理程序被创建并传递到`IUIAnimationTransitionFactory::CreateTransition`时`CCustomTransition`正在作为动画初始化过程的一部分创建对象 (由启动`CAnimationController::AnimateGroup`)。 通常不需要直接使用此类情况下，它只是 routs 的所有事件`CCustomInterpolator`-派生的类，其指针传递到构造函数`CCustomTransition`。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationInterpolatorBase`  
  
 `CInterpolatorBase`  
  
## <a name="requirements"></a>要求  
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
 自定义内插器指向的指针。  
  
 `ppHandler`  
 输出。 当函数返回时包含指向 CInterpolatorBase 实例的指针。  
  
### <a name="return-value"></a>返回值  
  
##  <a name="getdependencies"></a>CInterpolatorBase::GetDependencies  
 获取该内插器依赖项。  
  
```  
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>参数  
 `initialValueDependencies`  
 输出。 各个方面该内插器依赖于初始的值传递给 SetInitialValueAndVelocity。  
  
 `initialVelocityDependencies`  
 输出。 取决于初始速度该内插器方面传递给 SetInitialValueAndVelocity。  
  
 `durationDependencies`  
 输出。 该内插器方面的持续时间在依赖于传递给 SetDuration。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 如果未设置 CCustomInterpolator，或自定义实现从一个 GetDependencies 方法将返回 FALSE，则返回 E_FAIL。  
  
##  <a name="getduration"></a>CInterpolatorBase::GetDuration  
 获取该内插器持续时间。  
  
```  
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 输出。 该转换，以秒为单位的持续时间。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 如果未设置 CCustomInterpolator，或自定义实现从 GetDuration 方法将返回 FALSE，则返回 E_FAIL。  
  
##  <a name="getfinalvalue"></a>CInterpolatorBase::GetFinalValue  
 获取该内插器导致的最终值。  
  
```  
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```  
  
### <a name="parameters"></a>参数  
 `value`  
 输出。 变量在转换结束最终值。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 如果未设置 CCustomInterpolator，或自定义实现从 GetFinalValue 方法将返回 FALSE，则返回 E_FAIL。  
  
##  <a name="interpolatevalue"></a>CInterpolatorBase::InterpolateValue  
 给定的偏移量处的值的内插  
  
```  
IFACEMETHOD(InterpolateValue)(
  __in UI_ANIMATION_SECONDS offset, 
  __out DOUBLE* value);
```  
  
### <a name="parameters"></a>参数  
 `offset`  
 转换的开始的偏移量。 偏移量始终为大于或等于零且小于过渡的持续时间。 如果转换的持续时间为零，不调用此方法。  
  
 `value`  
 输出。 内插的值。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 如果未设置 CCustomInterpolator，或自定义实现从 InterpolateValue 方法将返回 FALSE，则返回 E_FAIL。  
  
##  <a name="interpolatevelocity"></a>CInterpolatorBase::InterpolateVelocity  
 内插在给定的偏移量的速度  
  
```  
IFACEMETHOD(InterpolateVelocity)(
  __in UI_ANIMATION_SECONDS offset,
  __out DOUBLE* velocity);
```  
  
### <a name="parameters"></a>参数  
 `offset`  
 转换的开始的偏移量。 偏移量始终是大于或等于零且小于或等于过渡的持续时间。 如果转换的持续时间为零，不调用此方法。  
  
 `velocity`  
 输出。 偏移量处变量的速度。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 如果未设置 CCustomInterpolator，或自定义实现从 InterpolateVelocity 方法将返回 FALSE，则返回 E_FAIL。  
  
##  <a name="setcustominterpolator"></a>CInterpolatorBase::SetCustomInterpolator  
 存储自定义内插器，将处理事件的指针。  
  
```  
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```  
  
### <a name="parameters"></a>参数  
 `pInterpolator`  
 自定义内插器指向的指针。  
  
##  <a name="setduration"></a>CInterpolatorBase::SetDuration  
 将内插器的持续时间设置  
  
```  
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 过渡的持续时间。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 如果未设置 CCustomInterpolator，或自定义实现 SetDuration 方法将返回 FALSE，则返回 E_FAIL。  
  
##  <a name="setinitialvalueandvelocity"></a>CInterpolatorBase::SetInitialValueAndVelocity  
 设置内插器的初始值和速度。  
  
```  
IFACEMETHOD(SetInitialValueAndVelocity)(
  __in DOUBLE initialValue, 
  __in DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>参数  
 `initialValue`  
 在转换开始的变量的值。  
  
 `initialVelocity`  
 该变量在转换开始的速度。  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 如果未设置 CCustomInterpolator，或自定义实现从 SetInitialValueAndVelocity 方法将返回 FALSE，则返回 E_FAIL。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

