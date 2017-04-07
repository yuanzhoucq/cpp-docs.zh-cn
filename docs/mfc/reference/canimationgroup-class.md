---
title: "CAnimationGroup 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::Animate
- AFXANIMATIONCONTROLLER/CAnimationGroup::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationGroup::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::Schedule
- AFXANIMATIONCONTROLLER/CAnimationGroup::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutoclearTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstKeyFrames
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pStoryboard
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pParentController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationGroup class
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a59d8a86fde68510d48e4a3398b6590b2215cbea
ms.lasthandoff: 02/24/2017

---
# <a name="canimationgroup-class"></a>CAnimationGroup 类
实现动画组，它结合了动画情节提要、 动画对象和转换来定义动画。  
  
## <a name="syntax"></a>语法  
  
```  
class CAnimationGroup;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|构造的动画组。|  
|[CAnimationGroup:: ~ CAnimationGroup](#canimationgroup__~canimationgroup)|析构函数。 当动画组被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationGroup::Animate](#animate)|一组进行动画处理。|  
|[CAnimationGroup::ApplyTransitions](#applytransitions)|将转换应用于动画对象。|  
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|查找包含指定的动画变量的动画对象。|  
|[CAnimationGroup::GetGroupID](#getgroupid)|返回 GroupID。|  
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|删除并有选择地销毁属于动画组的所有关键帧。|  
|[CAnimationGroup::RemoveTransitions](#removetransitions)|从属于组的动画的动画对象中删除转换。|  
|[CAnimationGroup::Schedule](#schedule)|将动画安排在指定的时间。|  
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|指示属于进行自动分组的所有动画对象都销毁转换。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationGroup::AddKeyframes](#addkeyframes)|一个帮助程序，将关键帧添加到情节提要。|  
|[CAnimationGroup::AddTransitions](#addtransitions)|一个帮助程序，将转换添加到情节提要。|  
|[CAnimationGroup::CreateTransitions](#createtransitions)|创建 COM 转换对象帮助器。|  
  
### <a name="public-data-members"></a>公共数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|指定如何清除从属于组的动画对象的转换。 如果此成员为 TRUE 时，会自动删除转换时已安排动画。 否则，您需要手动删除转换。|  
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|指定如何进行销毁的动画对象。 如果此参数为 TRUE，则当该组被销毁时，将自动销毁动画对象。 否则，必须手动销毁动画对象。 默认值为 FALSE。 仅当使用 new 运算符动态分配属于组的所有动画对象，请将此值设置为 TRUE。|  
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|指定如何进行销毁的关键帧。 如果此值为 TRUE，所有关键帧的删除和销毁;否则，则就会从列表中只删除。 默认值为 TRUE。|  
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|包含的动画对象的列表。|  
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|列出的关键帧。|  
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|指向以动画情节提要。 此指针仅在调用动画之后才有效。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|动画组的唯一标识符。|  
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|此组所属的动画控制器指向的指针。|  
  
## <a name="remarks"></a>备注  
 动画组由动画控制器 (CAnimationController) 添加动画对象使用 CAnimationController::AddAnimationObject 时自动创建。 动画组由 GroupID，通常作为一个参数用来操作动画组标识。 GroupID 取自被添加到新的动画组的第一个动画对象。 调用 CAnimationController::AnimateGroup 并可通过公共成员 m_pStoryboard 访问后，将创建封装的动画情节提要。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CAnimationGroup`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationgroup"></a>CAnimationGroup:: ~ CAnimationGroup  
 析构函数。 当动画组被销毁时调用。  
  
```  
~CAnimationGroup();
```  
  
##  <a name="addkeyframes"></a>CAnimationGroup::AddKeyframes  
 一个帮助程序，将关键帧添加到情节提要。  
  
```  
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```  
  
### <a name="parameters"></a>参数  
 `pStoryboard`  
 指向情节提要 COM 对象的指针。  
  
 `bAddDeep`  
 指定是否应将此方法添加到依赖于其他关键帧的情节提要关键帧。  
  
##  <a name="addtransitions"></a>CAnimationGroup::AddTransitions  
 一个帮助程序，将转换添加到情节提要。  
  
```  
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDependOnKeyframes);
```  
  
### <a name="parameters"></a>参数  
 `pStoryboard`  
 指向情节提要 COM 对象的指针。  
  
 `bDependOnKeyframes`  
  
##  <a name="animate"></a>CAnimationGroup::Animate  
 一组进行动画处理。  
  
```  
BOOL Animate(
    IUIAnimationManager* pManager,  
    IUIAnimationTimer* pTimer,  
    BOOL bScheduleNow);
```  
  
### <a name="parameters"></a>参数  
 `pManager`  
 `pTimer`  
 `bScheduleNow`  
  
### <a name="return-value"></a>返回值  
 如果方法成功，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此方法创建内部情节提要、 创建和应用转换和动画安排 bScheduleNow 为 TRUE 时。 如果 bScheduleNow 为 FALSE，您需要调用计划，以便启动动画在指定的时间。  
  
##  <a name="applytransitions"></a>CAnimationGroup::ApplyTransitions  
 将转换应用于动画对象。  
  
```  
void ApplyTransitions();
```  
  
### <a name="remarks"></a>备注  
 此方法断言在调试模式下，如果尚未创建情节提要。 它首先，创建的所有转换，然后将"静态"关键帧 （取决于的偏移量的关键帧） 添加、 添加不依赖于关键帧的转换、 添加关键帧，具体取决于转换和其他关键帧，并最后添加依赖于关键帧的转换。  
  
##  <a name="canimationgroup"></a>CAnimationGroup::CAnimationGroup  
 构造的动画组。  
  
```  
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```  
  
### <a name="parameters"></a>参数  
 `pParentController`  
 指向用于创建一组动画控制器的指针。  
  
 `nGroupID`  
 指定 GroupID。  
  
##  <a name="createtransitions"></a>CAnimationGroup::CreateTransitions  
 创建 COM 转换对象帮助器。  
  
```  
BOOL CreateTransitions();
```  
  
### <a name="return-value"></a>返回值  
 TRUE 是此方法成功，否则为 FALSE。  
  
##  <a name="findanimationobject"></a>CAnimationGroup::FindAnimationObject  
 查找包含指定的动画变量的动画对象。  
  
```  
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```  
  
### <a name="parameters"></a>参数  
 `pVariable`  
 指向动画变量的指针。  
  
### <a name="return-value"></a>返回值  
 指向动画对象，则为 NULL，如果找不到动画对象的指针。  
  
##  <a name="getgroupid"></a>CAnimationGroup::GetGroupID  
 返回 GroupID。  
  
```  
UINT32 GetGroupID() const;  
```  
  
### <a name="return-value"></a>返回值  
 组标识符。  
  
##  <a name="m_bautocleartransitions"></a>CAnimationGroup::m_bAutoclearTransitions  
 指定如何清除从属于组的动画对象的转换。 如果此成员为 TRUE 时，会自动删除转换时已安排动画。 否则，您需要手动删除转换。  
  
```  
BOOL m_bAutoclearTransitions;  
```  
  
##  <a name="m_bautodestroyanimationobjects"></a>CAnimationGroup::m_bAutodestroyAnimationObjects  
 指定如何进行销毁的动画对象。 如果此参数为 TRUE，则当该组被销毁时，将自动销毁动画对象。 否则，必须手动销毁动画对象。 默认值为 FALSE。 仅当使用 new 运算符动态分配属于组的所有动画对象，请将此值设置为 TRUE。  
  
```  
BOOL m_bAutodestroyAnimationObjects;  
```  
  
##  <a name="m_bautodestroykeyframes"></a>CAnimationGroup::m_bAutodestroyKeyframes  
 指定如何进行销毁的关键帧。 如果此值为 TRUE，所有关键帧的删除和销毁;否则，则就会从列表中只删除。 默认值为 TRUE。  
  
```  
BOOL m_bAutodestroyKeyframes;  
```  
  
##  <a name="m_lstanimationobjects"></a>CAnimationGroup::m_lstAnimationObjects  
 包含的动画对象的列表。  
  
```  
CObList m_lstAnimationObjects;  
```  
  
##  <a name="m_lstkeyframes"></a>CAnimationGroup::m_lstKeyFrames  
 列出的关键帧。  
  
```  
CObList m_lstKeyFrames;  
```  
  
##  <a name="m_ngroupid"></a>CAnimationGroup::m_nGroupID  
 动画组的唯一标识符。  
  
```  
UINT32 m_nGroupID;  
```  
  
##  <a name="m_pparentcontroller"></a>CAnimationGroup::m_pParentController  
 此组所属的动画控制器指向的指针。  
  
```  
CAnimationController* m_pParentController;  
```  
  
##  <a name="m_pstoryboard"></a>CAnimationGroup::m_pStoryboard  
 指向以动画情节提要。 此指针仅在调用动画之后才有效。  
  
```  
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;  
```  
  
##  <a name="removekeyframes"></a>CAnimationGroup::RemoveKeyframes  
 删除并有选择地销毁属于动画组的所有关键帧。  
  
```  
void RemoveKeyframes();
```  
  
### <a name="remarks"></a>备注  
 如果 m_bAutodestroyKeyframes 成员为 TRUE，则会删除关键帧并将其销毁，否则关键帧只是删除从关键帧的内部列表。  
  
##  <a name="removetransitions"></a>CAnimationGroup::RemoveTransitions  
 从属于组的动画的动画对象中删除转换。  
  
```  
void RemoveTransitions();
```  
  
### <a name="remarks"></a>备注  
 如果 m_bAutoclearTransitions 标志设置为 TRUE，则此方法循环访问属于的组的所有动画对象，并调用 CAnimationObject::ClearTransitions(FALSE)。  
  
##  <a name="schedule"></a>CAnimationGroup::Schedule  
 将动画安排在指定的时间。  
  
```  
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```  
  
### <a name="parameters"></a>参数  
 `pTimer`  
 指向动画计时器的指针。  
  
 `time`  
 指定该动画的安排的时间。  
  
### <a name="return-value"></a>返回值  
 如果方法成功，则为 TRUEFALSE 如果该方法将失败，或者如果动画尚未调用与 bScheduleNow 设置为 FALSE。  
  
### <a name="remarks"></a>备注  
 调用此函数可将动画安排在指定的时间。 您必须首先设置为 FALSE 的 bScheduleNow 调用 Animate。  
  
##  <a name="setautodestroytransitions"></a>CAnimationGroup::SetAutodestroyTransitions  
 指示属于进行自动分组的所有动画对象都销毁转换。  
  
```  
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bAutoDestroy`  
 指定如何进行销毁转换。  
  
### <a name="remarks"></a>备注  
 将此值设置为 FALSE，仅当分配到堆栈上的转换。 默认值为 TRUE，因此我们仍强烈建议为使用运算符 new 转换对象分配空间。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

