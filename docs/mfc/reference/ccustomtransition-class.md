---
title: "CCustomTransition 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- afxanimationcontroller/CCustomTransition
- CCustomTransition
dev_langs:
- C++
helpviewer_keywords:
- CCustomTransition class
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
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
ms.openlocfilehash: 483fb2ab84d2c41fe4666a4ea333c0be8b07caee
ms.lasthandoff: 02/24/2017

---
# <a name="ccustomtransition-class"></a>CCustomTransition 类
实现自定义转换。  
  
## <a name="syntax"></a>语法  
  
```  
class CCustomTransition : public CBaseTransition;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CCustomTransition::CCustomTransition](#ccustomtransition)|构造一个自定义转换对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CCustomTransition::Create](#create)|调用转换库来创建封装的转换 COM 对象。 (重写[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create)。)|  
|[CCustomTransition::SetInitialValue](#setinitialvalue)|设置将应用于与此转换关联的动画变量的初始值。|  
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|设置初始速度，将应用于与此转换关联的动画变量。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|指定与 SetInitialValue 是否指定了初始的值。|  
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|指定是否使用 setinitialvelocity 方法指定了初始速度。|  
|[CCustomTransition::m_initialValue](#m_initialvalue)|将存储的初始值。|  
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|将存储的初始速度。|  
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|存储自定义内插器的指针。|  
  
## <a name="remarks"></a>备注  
 CCustomTransitions 类允许开发人员实现自定义转换。 其创建和使用作为标准的转换，但其构造函数将作为参数接受指向自定义内插器的指针。 执行以下步骤以使用自定义的转换︰ 1。 从 CCustomInterpolator 派生一个类并实现至少 InterpolateValue 方法。 2. 确保必须长于动画的持续时间中仍在使用自定义内插器对象的生存期。 3. 实例化 （使用 new 运算符） CCustomTransition 对象，并将指针传递到构造函数中的自定义内插器。 4. 如果这些参数所需的自定义内插，调用 CCustomTransition::SetInitialValue 和 CCustomTransition::SetInitialVelocity。 5. 将指针传递给自定义转换到 AddTransition 方法的动画对象，其值应使用自定义算法进行动画处理。 6. 当动画对象的值应更改 Windows 动画 API 将在 CCustomInterpolator 调用 InterpolateValue （和其他相关的方法）。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseTransition](../../mfc/reference/cbasetransition-class.md)  
  
 `CCustomTransition`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="a-nameccustomtransitiona--ccustomtransitionccustomtransition"></a><a name="ccustomtransition"></a>CCustomTransition::CCustomTransition  
 构造一个自定义转换对象。  
  
```  
CCustomTransition(CCustomInterpolator* pInterpolator);
```  
  
### <a name="parameters"></a>参数  
 `pInterpolator`  
 自定义内插器指向的指针。  
  
##  <a name="a-namecreatea--ccustomtransitioncreate"></a><a name="create"></a>CCustomTransition::Create  
 调用转换库来创建封装的转换 COM 对象。  
  
```  
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,  
    IUIAnimationTransitionFactory* pFactory);
```  
  
### <a name="parameters"></a>参数  
 `pFactory`  
 负责创建的自定义转换的转换工厂指向的指针。  
  
### <a name="return-value"></a>返回值  
  
### <a name="remarks"></a>备注  
 此方法还可以设置初始值和初始速度要应用于与此转换相关联的动画变量。 实现此目的，您需要调用 SetInitialValue 和 setinitialvelocity 方法之前在框架创建 （它会在发生调用 CAnimationController::AnimateGroup） 的封装的转换 COM 对象。  
  
##  <a name="a-namembinitialvaluespecifieda--ccustomtransitionmbinitialvaluespecified"></a><a name="m_binitialvaluespecified"></a>CCustomTransition::m_bInitialValueSpecified  
 指定与 SetInitialValue 是否指定了初始的值。  
  
```  
BOOL m_bInitialValueSpecified;  
```  
  
##  <a name="a-namembinitialvelocityspecifieda--ccustomtransitionmbinitialvelocityspecified"></a><a name="m_binitialvelocityspecified"></a>CCustomTransition::m_bInitialVelocitySpecified  
 指定是否使用 setinitialvelocity 方法指定了初始速度。  
  
```  
BOOL m_bInitialVelocitySpecified;  
```  
  
##  <a name="a-nameminitialvaluea--ccustomtransitionminitialvalue"></a><a name="m_initialvalue"></a>CCustomTransition::m_initialValue  
 将存储的初始值。  
  
```  
DOUBLE m_initialValue;  
```  
  
##  <a name="a-nameminitialvelocitya--ccustomtransitionminitialvelocity"></a><a name="m_initialvelocity"></a>CCustomTransition::m_initialVelocity  
 将存储的初始速度。  
  
```  
DOUBLE m_initialVelocity;  
```  
  
##  <a name="a-namempinterpolatora--ccustomtransitionmpinterpolator"></a><a name="m_pinterpolator"></a>CCustomTransition::m_pInterpolator  
 存储自定义内插器的指针。  
  
```  
CCustomInterpolator* m_pInterpolator;  
```  
  
##  <a name="a-namesetinitialvaluea--ccustomtransitionsetinitialvalue"></a><a name="setinitialvalue"></a>CCustomTransition::SetInitialValue  
 设置将应用于与此转换关联的动画变量的初始值。  
  
```  
void SetInitialValue(DOUBLE initialValue);
```  
  
### <a name="parameters"></a>参数  
 `initialValue`  
  
##  <a name="a-namesetinitialvelocitya--ccustomtransitionsetinitialvelocity"></a><a name="setinitialvelocity"></a>CCustomTransition::SetInitialVelocity  
 设置初始速度，将应用于与此转换关联的动画变量。  
  
```  
void SetInitialVelocity(DOUBLE initialVelocity);
```  
  
### <a name="parameters"></a>参数  
 `initialVelocity`  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

