---
title: "CParabolicTransitionFromAcceleration 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::Create
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalVelocity
dev_langs:
- C++
helpviewer_keywords:
- CParabolicTransitionFromAcceleration class
ms.assetid: 1e59b86f-358b-4da0-a4fd-8eaf5e85e00f
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
ms.openlocfilehash: f0d3089a01cd244851be3d4bdf0453101a9c8274
ms.lasthandoff: 02/24/2017

---
# <a name="cparabolictransitionfromacceleration-class"></a>CParabolicTransitionFromAcceleration 类
封装抛物线加速转换。  
  
## <a name="syntax"></a>语法  
  
```  
class CParabolicTransitionFromAcceleration : public CBaseTransition;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration](#cparabolictransitionfromacceleration)|构造抛物线加速转换，并使用指定的参数对其进行初始化。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::Create](#create)|调用转换库来创建封装的转换 COM 对象。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CParabolicTransitionFromAcceleration::m_dblAcceleration](#m_dblacceleration)|在转换期间加速的动画变量。|  
|[CParabolicTransitionFromAcceleration::m_dblFinalValue](#m_dblfinalvalue)|末尾的过渡动画变量的值。|  
|[CParabolicTransitionFromAcceleration::m_dblFinalVelocity](#m_dblfinalvelocity)|末尾的过渡动画变量的速度。|  
  
## <a name="remarks"></a>备注  
 在一个抛物线加速转换，动画变量的值从变为初始值以指定的速度结束的最终值。 您可以控制如何快速变量达到的最终值通过指定加速的速率。 因为所有的转换会自动清除，建议为它们分配使用 new 运算符。 封装 IUIAnimationTransition 创建的 COM 对象是通过 CAnimationController::AnimateGroup，直到则，则为 NULL。 在创建此 COM 对象不起作用后，请更改成员变量。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CParabolicTransitionFromAcceleration](../../mfc/reference/cparabolictransitionfromacceleration-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="cparabolictransitionfromacceleration"></a>CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration  
 构造抛物线加速转换，并使用指定的参数对其进行初始化。  
  
```  
CParabolicTransitionFromAcceleration(
    DOUBLE dblFinalValue,  
    DOUBLE dblFinalVelocity,  
    DOUBLE dblAcceleration);
```  
  
### <a name="parameters"></a>参数  
 `dblFinalValue`  
 末尾的过渡动画变量的值。  
  
 `dblFinalVelocity`  
 末尾的过渡动画变量的速度。  
  
 `dblAcceleration`  
 在转换期间加速的动画变量。  
  
##  <a name="create"></a>CParabolicTransitionFromAcceleration::Create  
 调用转换库来创建封装的转换 COM 对象。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* /* not used */);
```  
  
### <a name="parameters"></a>参数  
 `pLibrary`  
 指向负责创建标准转换的转换库的指针。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建转换，则返回 TRUE否则为 FALSE。  
  
##  <a name="m_dblacceleration"></a>CParabolicTransitionFromAcceleration::m_dblAcceleration  
 在转换期间加速的动画变量。  
  
```  
DOUBLE m_dblAcceleration;  
```  
  
##  <a name="m_dblfinalvalue"></a>CParabolicTransitionFromAcceleration::m_dblFinalValue  
 末尾的过渡动画变量的值。  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_dblfinalvelocity"></a>CParabolicTransitionFromAcceleration::m_dblFinalVelocity  
 末尾的过渡动画变量的速度。  
  
```  
DOUBLE m_dblFinalVelocity;  
```  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

