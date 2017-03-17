---
title: "CCustomInterpolator 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
- CCustomInterpolator class
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
caps.latest.revision: 17
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
ms.sourcegitcommit: 73410ae17465880f455e5b15026f6cc010803c19
ms.openlocfilehash: 4d0b38543092dc68c2527f7e1385712164faf996
ms.lasthandoff: 02/24/2017

---
# <a name="ccustominterpolator-class"></a>CCustomInterpolator 类
实现基本插值程序。  
  
## <a name="syntax"></a>语法  
  
```  
class CCustomInterpolator;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|已重载。 构造一个自定义内插器对象并初始化持续时间和为指定值的速度。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CCustomInterpolator::GetDependencies](#getdependencies)|获取该内插器依赖项。|  
|[CCustomInterpolator::GetDuration](#getduration)|获取该内插器持续时间。|  
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|获取该内插器导致的最终值。|  
|[CCustomInterpolator::Init](#init)|初始化持续时间和最终值。|  
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|内插给定的偏移量处的值。|  
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|内插在给定的偏移量的速度|  
|[CCustomInterpolator::SetDuration](#setduration)|设置内插器的持续时间。|  
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|设置内插器的初始值和速度。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|内插的值。|  
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|内插的速度。|  
|[CCustomInterpolator::m_duration](#m_duration)|过渡的持续时间。|  
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|变量在转换结束最终值。|  
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|在转换开始的变量的值。|  
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|该变量在转换开始的速度。|  
  
## <a name="remarks"></a>备注  
 从 CCustomInterpolator 派生一个类，如果要实现自定义内插算法重写所有必需的方法。 与此类指针应作为一个参数传递给 CCustomTransition。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CCustomInterpolator`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="ccustominterpolator"></a>CCustomInterpolator::CCustomInterpolator  
 构造一个自定义内插器对象和设置所有默认值为 0 的值。  
  
```  
CCustomInterpolator();

 
CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 过渡的持续时间。  
  
 `finalValue`  
  
### <a name="remarks"></a>备注  
 使用 CCustomInterpolator::Init 初始化持续时间和更高版本在代码中的最终值。  
  
##  <a name="getdependencies"></a>CCustomInterpolator::GetDependencies  
 获取该内插器依赖项。  
  
```  
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,  
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,  
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```  
  
### <a name="parameters"></a>参数  
 `initialValueDependencies`  
 输出。 各个方面该内插器依赖于初始的值传递给 SetInitialValueAndVelocity。  
  
 `initialVelocityDependencies`  
 输出。 取决于初始速度该内插器方面传递给 SetInitialValueAndVelocity。  
  
 `durationDependencies`  
 输出。 该内插器方面的持续时间在依赖于传递给 SetDuration。  
  
### <a name="return-value"></a>返回值  
 基本实现始终返回 TRUE。 返回 FALSE 从重写实现如果您希望该事件失败。  
  
##  <a name="getduration"></a>CCustomInterpolator::GetDuration  
 获取该内插器持续时间。  
  
```  
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 输出。 该转换，以秒为单位的持续时间。  
  
### <a name="return-value"></a>返回值  
 基本实现始终返回 TRUE。 返回 FALSE 从重写实现如果您希望该事件失败。  
  
##  <a name="getfinalvalue"></a>CCustomInterpolator::GetFinalValue  
 获取该内插器导致的最终值。  
  
```  
virtual BOOL GetFinalValue(DOUBLE* value);
```  
  
### <a name="parameters"></a>参数  
 `value`  
 输出。 变量在转换结束最终值。  
  
### <a name="return-value"></a>返回值  
 基本实现始终返回 TRUE。 返回 FALSE 从重写实现如果您希望该事件失败。  
  
##  <a name="init"></a>CCustomInterpolator::Init  
 初始化持续时间和最终值。  
  
```  
void Init(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 过渡的持续时间。  
  
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
 基本实现始终返回 TRUE。 返回 FALSE 从重写实现如果您希望该事件失败。  
  
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
 基本实现始终返回 TRUE。 返回 FALSE 从重写实现如果您希望该事件失败。  
  
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
 过渡的持续时间。  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_finalvalue"></a>CCustomInterpolator::m_finalValue  
 变量在转换结束最终值。  
  
```  
DOUBLE m_finalValue;  
```  
  
##  <a name="m_initialvalue"></a>CCustomInterpolator::m_initialValue  
 在转换开始的变量的值。  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="m_initialvelocity"></a>CCustomInterpolator::m_initialVelocity  
 该变量在转换开始的速度。  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="setduration"></a>CCustomInterpolator::SetDuration  
 设置内插器的持续时间。  
  
```  
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 过渡的持续时间。  
  
### <a name="return-value"></a>返回值  
 基本实现始终返回 TRUE。 返回 FALSE 从重写实现如果您希望该事件失败。  
  
##  <a name="setinitialvalueandvelocity"></a>CCustomInterpolator::SetInitialValueAndVelocity  
 设置内插器的初始值和速度。  
  
```  
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,  
    DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>参数  
 `initialValue`  
 在转换开始的变量的值。  
  
 `initialVelocity`  
 该变量在转换开始的速度。  
  
### <a name="return-value"></a>返回值  
 基本实现始终返回 TRUE。 返回 FALSE 从重写实现如果您希望该事件失败。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

