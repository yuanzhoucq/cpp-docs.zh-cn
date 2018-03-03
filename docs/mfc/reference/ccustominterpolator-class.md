---
title: "CCustomInterpolator 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDependencies
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetFinalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::Init
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetInitialValueAndVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_duration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_finalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialVelocity
dev_langs:
- C++
helpviewer_keywords:
- CCustomInterpolator [MFC], CCustomInterpolator
- CCustomInterpolator [MFC], GetDependencies
- CCustomInterpolator [MFC], GetDuration
- CCustomInterpolator [MFC], GetFinalValue
- CCustomInterpolator [MFC], Init
- CCustomInterpolator [MFC], InterpolateValue
- CCustomInterpolator [MFC], InterpolateVelocity
- CCustomInterpolator [MFC], SetDuration
- CCustomInterpolator [MFC], SetInitialValueAndVelocity
- CCustomInterpolator [MFC], m_currentValue
- CCustomInterpolator [MFC], m_currentVelocity
- CCustomInterpolator [MFC], m_duration
- CCustomInterpolator [MFC], m_finalValue
- CCustomInterpolator [MFC], m_initialValue
- CCustomInterpolator [MFC], m_initialVelocity
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 26763a16c4de59f33622ea904ea8aa132fe0d5f2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ccustominterpolator-class"></a>CCustomInterpolator 类
实现基本插值程序。  
  
## <a name="syntax"></a>语法  
  
```  
class CCustomInterpolator;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|已重载。 构造一个自定义插值程序对象并初始化持续时间和为指定值的速度。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CCustomInterpolator::GetDependencies](#getdependencies)|获取插值程序的依赖项。|  
|[CCustomInterpolator::GetDuration](#getduration)|获取插值程序的持续时间。|  
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|获取插值程序潜在顾客的最终值。|  
|[CCustomInterpolator::Init](#init)|初始化持续时间和最终值。|  
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|内插给定的偏移量处的值。|  
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|内插在给定的偏移量的速度|  
|[CCustomInterpolator::SetDuration](#setduration)|设置插值程序的持续时间。|  
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|设置插值程序的初始值和速度。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|内插的值。|  
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|内插的速度。|  
|[CCustomInterpolator::m_duration](#m_duration)|转换的持续时间。|  
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|变量在转换结束最终值。|  
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|在转换的开始的变量的值。|  
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|在转换的开始的变量的速度。|  
  
## <a name="remarks"></a>备注  
 从 CCustomInterpolator 派生一个类并重写为了实现自定义的内插算法的所有所需的方法。 与此类指针应作为参数传递给 CCustomTransition。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CCustomInterpolator`  
  
## <a name="requirements"></a>惠?  
 **标头：** afxanimationcontroller.h  
  
##  <a name="ccustominterpolator"></a>CCustomInterpolator::CCustomInterpolator  
 构造一个自定义插值程序对象和设置默认值为 0 的所有值。  
  
```  
CCustomInterpolator();

 
CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 转换的持续时间。  
  
 `finalValue`  
  
### <a name="remarks"></a>备注  
 使用 CCustomInterpolator::Init 初始化持续时间和更高版本在代码中的最终值。  
  
##  <a name="getdependencies"></a>CCustomInterpolator::GetDependencies  
 获取插值程序的依赖项。  
  
```  
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,  
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,  
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>参数  
 `initialValueDependencies`  
 输出。 各个方面插值程序依赖于初始的值传递给 SetInitialValueAndVelocity。  
  
 `initialVelocityDependencies`  
 输出。 各个方面插值程序依赖于的初始速度传递给 SetInitialValueAndVelocity。  
  
 `durationDependencies`  
 输出。 各个方面插值程序持续时间取决于传递给 SetDuration。  
  
### <a name="return-value"></a>返回值  
 基本实现始终返回 TRUE。 返回 FALSE 从重写实现如果你想要失败事件。  
  
##  <a name="getduration"></a>CCustomInterpolator::GetDuration  
 获取插值程序的持续时间。  
  
```  
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 输出。 转换，以秒为单位的持续时间。  
  
### <a name="return-value"></a>返回值  
 基本实现始终返回 TRUE。 返回 FALSE 从重写实现如果你想要失败事件。  
  
##  <a name="getfinalvalue"></a>CCustomInterpolator::GetFinalValue  
 获取插值程序潜在顾客的最终值。  
  
```  
virtual BOOL GetFinalValue(DOUBLE* value);
```  
  
### <a name="parameters"></a>参数  
 `value`  
 输出。 变量在转换结束最终值。  
  
### <a name="return-value"></a>返回值  
 基本实现始终返回 TRUE。 返回 FALSE 从重写实现如果你想要失败事件。  
  
##  <a name="init"></a>CCustomInterpolator::Init  
 初始化持续时间和最终值。  
  
```  
void Init(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 转换的持续时间。  
  
 `finalValue`  
 变量在转换结束最终值。  
  
##  <a name="interpolatevalue"></a>CCustomInterpolator::InterpolateValue  
 内插给定的偏移量处的值。  
  
```  
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* value);
```  
  
### <a name="parameters"></a>参数  
 `value`  
 输出。 内插的值。  
  
### <a name="return-value"></a>返回值  
 基本实现始终返回 TRUE。 返回 FALSE 从重写实现如果你想要失败事件。  
  
##  <a name="interpolatevelocity"></a>CCustomInterpolator::InterpolateVelocity  
 内插在给定的偏移量的速度  
  
```  
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,  
    DOUBLE* velocity);
```  
  
### <a name="parameters"></a>参数  
 `velocity`  
 输出。 偏移量处变量的速度。  
  
### <a name="return-value"></a>返回值  
 基本实现始终返回 TRUE。 返回 FALSE 从重写实现如果你想要失败事件。  
  
##  <a name="m_currentvalue"></a>CCustomInterpolator::m_currentValue  
 内插的值。  
  
```  
DOUBLE m_currentValue;  
```  
  
##  <a name="m_currentvelocity"></a>CCustomInterpolator::m_currentVelocity  
 内插的速度。  
  
```  
DOUBLE m_currentVelocity;  
```  
  
##  <a name="m_duration"></a>CCustomInterpolator::m_duration  
 转换的持续时间。  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_finalvalue"></a>CCustomInterpolator::m_finalValue  
 变量在转换结束最终值。  
  
```  
DOUBLE m_finalValue;  
```  
  
##  <a name="m_initialvalue"></a>CCustomInterpolator::m_initialValue  
 在转换的开始的变量的值。  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="m_initialvelocity"></a>CCustomInterpolator::m_initialVelocity  
 在转换的开始的变量的速度。  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="setduration"></a>CCustomInterpolator::SetDuration  
 设置插值程序的持续时间。  
  
```  
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 转换的持续时间。  
  
### <a name="return-value"></a>返回值  
 基本实现始终返回 TRUE。 返回 FALSE 从重写实现如果你想要失败事件。  
  
##  <a name="setinitialvalueandvelocity"></a>CCustomInterpolator::SetInitialValueAndVelocity  
 设置插值程序的初始值和速度。  
  
```  
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,  
    DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>参数  
 `initialValue`  
 在转换的开始的变量的值。  
  
 `initialVelocity`  
 在转换的开始的变量的速度。  
  
### <a name="return-value"></a>返回值  
 基本实现始终返回 TRUE。 返回 FALSE 从重写实现如果你想要失败事件。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
