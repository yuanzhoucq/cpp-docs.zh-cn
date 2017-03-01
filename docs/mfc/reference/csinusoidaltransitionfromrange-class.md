---
title: "CSinusoidalTransitionFromRange 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxanimationcontroller/CSinusoidalTransitionFromRange
- CSinusoidalTransitionFromRange
dev_langs:
- C++
helpviewer_keywords:
- CSinusoidalTransitionFromRange class
ms.assetid: 8b66a729-5f10-431a-b055-e3600d0065da
caps.latest.revision: 18
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: f9dd0e236207c0b4139de42f4c616aaad9dcad28
ms.lasthandoff: 02/24/2017

---
# <a name="csinusoidaltransitionfromrange-class"></a>CSinusoidalTransitionFromRange 类
封装具有给定振动范围的正弦范围转换。  
  
## <a name="syntax"></a>语法  
  
```  
class CSinusoidalTransitionFromRange : public CBaseTransition;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange](#csinusoidaltransitionfromrange)|构造转换对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::Create](#create)|调用转换库来创建封装的转换 COM 对象。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CSinusoidalTransitionFromRange::m_dblMaximumValue](#m_dblmaximumvalue)|在高峰期正弦波的动画变量的值。|  
|[CSinusoidalTransitionFromRange::m_dblMinimumValue](#m_dblminimumvalue)|在通过正弦波的动画变量的值。|  
|[CSinusoidalTransitionFromRange::m_duration](#m_duration)|过渡的持续时间。|  
|[CSinusoidalTransitionFromRange::m_period](#m_period)|以秒为单位的正弦波振动的段。|  
|[CSinusoidalTransitionFromRange::m_slope](#m_slope)|在转换开始的斜率。|  
  
## <a name="remarks"></a>备注  
 通过正弦范围转换的整个持续时间指定的最小值和最大值之间波动动画变量的值。 斜率参数用于消除由其他参数指定两个可能正弦波之间的歧义。 因为所有的转换会自动清除，建议为它们分配使用 new 运算符。 封装 IUIAnimationTransition 创建的 COM 对象是通过 CAnimationController::AnimateGroup，直到则，则为 NULL。 在创建此 COM 对象不起作用后，请更改成员变量。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSinusoidalTransitionFromRange](../../mfc/reference/csinusoidaltransitionfromrange-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="a-namecreatea--csinusoidaltransitionfromrangecreate"></a><a name="create"></a>CSinusoidalTransitionFromRange::Create  
 调用转换库来创建封装的转换 COM 对象。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>参数  
 `pLibrary`  
 指向负责创建标准转换的转换库的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建转换，则返回 TRUE否则为 FALSE。  
  
##  <a name="a-namecsinusoidaltransitionfromrangea--csinusoidaltransitionfromrangecsinusoidaltransitionfromrange"></a><a name="csinusoidaltransitionfromrange"></a>CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange  
 构造转换对象。  
  
```  
CSinusoidalTransitionFromRange(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE dblMinimumValue,  
    DOUBLE dblMaximumValue,  
    UI_ANIMATION_SECONDS period,  
    UI_ANIMATION_SLOPE slope);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 过渡的持续时间。  
  
 `dblMinimumValue`  
 在通过正弦波的动画变量的值。  
  
 `dblMaximumValue`  
 在高峰期正弦波的动画变量的值。  
  
 `period`  
 以秒为单位的正弦波振动的段。  
  
 `slope`  
 在转换开始的斜率。  
  
##  <a name="a-namemdblmaximumvaluea--csinusoidaltransitionfromrangemdblmaximumvalue"></a><a name="m_dblmaximumvalue"></a>CSinusoidalTransitionFromRange::m_dblMaximumValue  
 在高峰期正弦波的动画变量的值。  
  
```  
DOUBLE m_dblMaximumValue;  
```  
  
##  <a name="a-namemdblminimumvaluea--csinusoidaltransitionfromrangemdblminimumvalue"></a><a name="m_dblminimumvalue"></a>CSinusoidalTransitionFromRange::m_dblMinimumValue  
 在通过正弦波的动画变量的值。  
  
```  
DOUBLE m_dblMinimumValue;  
```  
  
##  <a name="a-namemdurationa--csinusoidaltransitionfromrangemduration"></a><a name="m_duration"></a>CSinusoidalTransitionFromRange::m_duration  
 过渡的持续时间。  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="a-namemperioda--csinusoidaltransitionfromrangemperiod"></a><a name="m_period"></a>CSinusoidalTransitionFromRange::m_period  
 以秒为单位的正弦波振动的段。  
  
```  
UI_ANIMATION_SECONDS m_period;  
```  
  
##  <a name="a-namemslopea--csinusoidaltransitionfromrangemslope"></a><a name="m_slope"></a>CSinusoidalTransitionFromRange::m_slope  
 在转换开始的斜率。  
  
```  
UI_ANIMATION_SLOPE m_slope;  
```  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

