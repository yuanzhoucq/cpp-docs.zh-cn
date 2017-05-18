---
title: "CAccelerateDecelerateTransition Class1 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
dev_langs:
- C++
helpviewer_keywords:
- CAccelerateDecelerateTransition class
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
caps.latest.revision: 16
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: f11dc96b48695b998fb17c33735e8f56bce517b7
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="cacceleratedeceleratetransition-class"></a>CAccelerateDecelerateTransition 类
实现加速-减速转换。  
  
## <a name="syntax"></a>语法  
  
```  
class CAccelerateDecelerateTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|构造转换对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::Create](#create)|调用转换库来创建封装的转换 COM 对象。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|所用的时间加快了持续时间的比率。|  
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|所用的时间的持续时间减速的比率。|  
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|过渡的持续时间。|  
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|末尾的过渡动画变量的值。|  
  
## <a name="remarks"></a>备注  
 在加速-减速转换、 动画变量的速度并再减速的转换，以指定的值结束的持续时间内。 您可以控制如何快速变量独立加速和减速，通过指定不同的加速和减速比率。 当初始速度为零时，加速比率是该变量将用于加速; 的持续时间的部分同样与减速度比。 如果初始速度为非零值，则速度接近零和转换末尾之间的时间间隔的一部分。 加速比率和减速比率的总和应为最多为 1.0。 因为所有的转换会自动清除，建议为它们分配使用 new 运算符。 封装 IUIAnimationTransition 创建的 COM 对象是通过 CAnimationController::AnimateGroup，直到则，则为 NULL。 在创建此 COM 对象不起作用后，请更改成员变量。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CAccelerateDecelerateTransition`   
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="cacceleratedeceleratetransition"></a>CAccelerateDecelerateTransition::CAccelerateDecelerateTransition  
 构造转换对象。  
  
```  
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue,  
    DOUBLE accelerationRatio = 0.3,  
    DOUBLE decelerationRatio = 0.3);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 过渡的持续时间。  
  
 `finalValue`  
 末尾的过渡动画变量的值。  
  
 `accelerationRatio`  
 所用的时间加快了持续时间的比率。  
  
 `decelerationRatio`  
 所用的时间的持续时间减速的比率。  
  
##  <a name="create"></a>CAccelerateDecelerateTransition::Create  
 调用转换库来创建封装的转换 COM 对象。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* *\not used*\);
```  
  
### <a name="parameters"></a>参数  
`pLibrary`  
 一个指向[IUIAnimationTransitionLibrary 接口](https://msdn.microsoft.com/library/windows/desktop/dd371897)，后者定义一个标准转换的库。  
  
### <a name="return-value"></a>返回值  
 如果成功，则创建转换，则返回 TRUE否则为 FALSE。  
  
##  <a name="m_accelerationratio"></a>CAccelerateDecelerateTransition::m_accelerationRatio  
 所用的时间加快了持续时间的比率。  
  
```  
DOUBLE m_accelerationRatio;  
```  
  
##  <a name="m_decelerationratio"></a>CAccelerateDecelerateTransition::m_decelerationRatio  
 所用的时间的持续时间减速的比率。  
  
```  
DOUBLE m_decelerationRatio;  
```  
  
##  <a name="m_duration"></a>CAccelerateDecelerateTransition::m_duration  
 过渡的持续时间。  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
##  <a name="m_finalvalue"></a>CAccelerateDecelerateTransition::m_finalValue  
 末尾的过渡动画变量的值。  
  
```  
DOUBLE m_finalValue;  
```  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

