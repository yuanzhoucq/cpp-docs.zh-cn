---
title: "CCubicTransition 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::Create
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalVelocity
- AFXANIMATIONCONTROLLER/CCubicTransition::m_duration
dev_langs:
- C++
helpviewer_keywords:
- CCubicTransition class
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 511dc175d51db7887a462aaf63f4f91290375751
ms.lasthandoff: 02/24/2017

---
# <a name="ccubictransition-class"></a>CCubicTransition 类
封装立方转换。  
  
## <a name="syntax"></a>语法  
  
```  
class CCubicTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CCubicTransition::CCubicTransition](#ccubictransition)|构造转换对象并初始化其参数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CCubicTransition::Create](#create)|调用转换库来创建封装的转换 COM 对象。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CCubicTransition::m_dblFinalValue](#m_dblfinalvalue)|末尾的过渡动画变量的值。|  
|[CCubicTransition::m_dblFinalVelocity](#m_dblfinalvelocity)|在转换结束变量的速度。|  
|[CCubicTransition::m_duration](#m_duration)|过渡的持续时间。|  
  
## <a name="remarks"></a>备注  
 三次方在转换期间，动画变量的值从更改其初始值为指定的最终值，转换，以指定的速度结束的持续时间。 因为所有的转换会自动清除，建议为它们分配使用 new 运算符。 封装 IUIAnimationTransition 创建的 COM 对象是通过 CAnimationController::AnimateGroup，直到则，则为 NULL。 在创建此 COM 对象不起作用后，请更改成员变量。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CCubicTransition`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="ccubictransition"></a>CCubicTransition::CCubicTransition  
 构造转换对象并初始化其参数。  
  
```  
CCubicTransition(
    UI_ANIMATION_SECONDS duration,  
    DOUBLE finalValue,  
    DOUBLE finalVelocity);
```  
  
### <a name="parameters"></a>参数  
 `duration`  
 过渡的持续时间。  
  
 `finalValue`  
 末尾的过渡动画变量的值。  
  
 `finalVelocity`  
 在转换结束变量的速度。  
  
##  <a name="create"></a>CCubicTransition::Create  
 调用转换库来创建封装的转换 COM 对象。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
### <a name="parameters"></a>参数  
`pLibrary`  
 一个指向[IUIAnimationTransitionLibrary 接口](https://msdn.microsoft.com/library/windows/desktop/dd371897)，后者定义一个标准转换的库。  

### <a name="return-value"></a>返回值  
 如果成功，则创建转换，则返回 TRUE否则为 FALSE。  
  
##  <a name="m_dblfinalvalue"></a>CCubicTransition::m_dblFinalValue  
 末尾的过渡动画变量的值。  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="m_dblfinalvelocity"></a>CCubicTransition::m_dblFinalVelocity  
 在转换结束变量的速度。  
  
```  
DOUBLE m_dblFinalVelocity;  
```  
  
##  <a name="m_duration"></a>CCubicTransition::m_duration  
 过渡的持续时间。  
  
```  
UI_ANIMATION_SECONDS m_duration;  
```  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

