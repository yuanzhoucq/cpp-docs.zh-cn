---
title: "CDiscreteTransition 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDiscreteTransition
- afxanimationcontroller/CDiscreteTransition
dev_langs:
- C++
helpviewer_keywords:
- CDiscreteTransition class
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
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
ms.openlocfilehash: dcec642fede0ec6895c928925676232319099be7
ms.lasthandoff: 02/24/2017

---
# <a name="cdiscretetransition-class"></a>CDiscreteTransition 类
封装离散转换。  
  
## <a name="syntax"></a>语法  
  
```  
class CDiscreteTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CDiscreteTransition::CDiscreteTransition](#cdiscretetransition)|构造一个离散转换对象并初始化其参数。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CDiscreteTransition::Create](#create)|调用转换库来创建封装的转换 COM 对象。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CDiscreteTransition::m_dblFinalValue](#m_dblfinalvalue)|末尾的过渡动画变量的值。|  
|[CDiscreteTransition::m_delay](#m_delay)|用于瞬时切换到最终值延迟的时间量。|  
|[CDiscreteTransition::m_hold](#m_hold)|若要保存该变量在其最终值所依据的时间量。|  
  
## <a name="remarks"></a>备注  
 离散在转换期间，动画变量将保留为初始值为指定的延迟时间，然后切换到指定的最终值并在此值保持在瞬间完成给定的保留时间。 因为所有的转换会自动清除，建议为它们分配使用 new 运算符。 封装 IUIAnimationTransition 创建的 COM 对象是通过 CAnimationController::AnimateGroup，直到则，则为 NULL。 在创建此 COM 对象不起作用后，请更改成员变量。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 [CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="a-namecdiscretetransitiona--cdiscretetransitioncdiscretetransition"></a><a name="cdiscretetransition"></a>CDiscreteTransition::CDiscreteTransition  
 构造一个离散转换对象并初始化其参数。  
  
```  
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,  
    DOUBLE dblFinalValue,  
    UI_ANIMATION_SECONDS hold);
```  
  
### <a name="parameters"></a>参数  
 `delay`  
 用于瞬时切换到最终值延迟的时间量。  
  
 `dblFinalValue`  
 末尾的过渡动画变量的值。  
  
 `hold`  
 若要保存该变量在其最终值所依据的时间量。  
  
##  <a name="a-namecreatea--cdiscretetransitioncreate"></a><a name="create"></a>CDiscreteTransition::Create  
 调用转换库来创建封装的转换 COM 对象。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,  
    IUIAnimationTransitionFactory* \*not used*\);
```  
  
`pLibrary`  
 一个指向[IUIAnimationTransitionLibrary 接口](https://msdn.microsoft.com/library/windows/desktop/dd371897)，后者定义一个标准转换的库。  

  
### <a name="return-value"></a>返回值  
 如果成功，则创建转换，则返回 TRUE否则为 FALSE。  
  
##  <a name="a-namemdblfinalvaluea--cdiscretetransitionmdblfinalvalue"></a><a name="m_dblfinalvalue"></a>CDiscreteTransition::m_dblFinalValue  
 末尾的过渡动画变量的值。  
  
```  
DOUBLE m_dblFinalValue;  
```  
  
##  <a name="a-namemdelaya--cdiscretetransitionmdelay"></a><a name="m_delay"></a>CDiscreteTransition::m_delay  
 用于瞬时切换到最终值延迟的时间量。  
  
```  
UI_ANIMATION_SECONDS m_delay;  
```  
  
##  <a name="a-namemholda--cdiscretetransitionmhold"></a><a name="m_hold"></a>CDiscreteTransition::m_hold  
 若要保存该变量在其最终值所依据的时间量。  
  
```  
UI_ANIMATION_SECONDS m_hold;  
```  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

