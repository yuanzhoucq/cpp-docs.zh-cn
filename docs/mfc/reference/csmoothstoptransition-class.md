---
title: "CSmoothStopTransition 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::CSmoothStopTransition
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::Create
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CSmoothStopTransition::m_maximumDuration
dev_langs:
- C++
helpviewer_keywords:
- CSmoothStopTransition class
ms.assetid: e1a4b476-6f96-43dd-90db-870a64406b85
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
ms.openlocfilehash: 60cdc3528d10270187dccd42a634f7483c58821f
ms.lasthandoff: 02/24/2017

---
# <a name="csmoothstoptransition-class"></a>CSmoothStopTransition 类
封装平稳停止转换。  
  
## <a name="syntax"></a>语法  
  
```  
class CSmoothStopTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CSmoothStopTransition::CSmoothStopTransition](#csmoothstoptransition)|构造平稳停止转换并初始化其最大持续时间和最终值。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CSmoothStopTransition::Create](#create)|调用转换库来创建封装的转换 COM 对象。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CSmoothStopTransition::m_dblFinalValue](#m_dblfinalvalue)|末尾的过渡动画变量的值。|  
|[CSmoothStopTransition::m_maximumDuration](#m_maximumduration)|过渡的最大持续时间。|  
  
## <a name="remarks"></a>备注  
 平稳停止转换随着它接近给定的最后一个值，并且达到零在速度减慢。 过渡的持续时间取决于初始速度，初始和最终值和指定的最大持续时间之间的差异。 如果没有解决方案，其中包含的单一的抛物线圆弧，此方法创建立方转换。 因为所有的转换会自动清除，建议为它们分配使用 new 运算符。 封装 IUIAnimationTransition 创建的 COM 对象是通过 CAnimationController::AnimateGroup，直到则，则为 NULL。 在创建此 COM 对象不起作用后，请更改成员变量。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CSmoothStopTransition](../../mfc/reference/csmoothstoptransition-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="create"></a>CSmoothStopTransition::Create  
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
  
##  <a name="csmoothstoptransition"></a>CSmoothStopTransition::CSmoothStopTransition  
 构造平稳停止转换并初始化其最大持续时间和最终值。  
  
```  
CSmoothStopTransition(
    UI_ANIMATION_SECONDS maximumDuration,  
    DOUBLE dblFinalValue);
```  
  
### <a name="parameters"></a>参数  
 `maximumDuration`  
 过渡的最大持续时间。  
  
 `dblFinalValue`  
 末尾的过渡动画变量的值。  
  
##  <a name="m_dblfinalvalue"></a>CSmoothStopTransition::m_dblFinalValue  
 末尾的过渡动画变量的值。  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_maximumduration"></a>CSmoothStopTransition::m_maximumDuration  
 过渡的最大持续时间。  
  
```  
UI_ANIMATION_SECONDS m_maximumDuration;  
```  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

