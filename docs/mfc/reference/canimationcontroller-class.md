---
title: CAnimationController 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::AddAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::AddKeyframeToGroup
- AFXANIMATIONCONTROLLER/CAnimationController::AnimateGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CleanUpGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CreateKeyframe
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationManagerEvent
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnablePriorityComparisonHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnableStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::GetKeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionLibrary
- AFXANIMATIONCONTROLLER/CAnimationController::IsAnimationInProgress
- AFXANIMATIONCONTROLLER/CAnimationController::IsValid
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnBeforeAnimationStart
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCancel
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCompress
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityConclude
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityTrim
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAllAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationController::ScheduleGroup
- AFXANIMATIONCONTROLLER/CAnimationController::SetRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::UpdateAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::OnAfterSchedule
- AFXANIMATIONCONTROLLER/CAnimationController::gkeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::m_bIsValid
- AFXANIMATIONCONTROLLER/CAnimationController::m_lstAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::m_pRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionLibrary
dev_langs:
- C++
helpviewer_keywords:
- CAnimationController [MFC], CAnimationController
- CAnimationController [MFC], AddAnimationObject
- CAnimationController [MFC], AddKeyframeToGroup
- CAnimationController [MFC], AnimateGroup
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], CreateKeyframe
- CAnimationController [MFC], EnableAnimationManagerEvent
- CAnimationController [MFC], EnableAnimationTimerEventHandler
- CAnimationController [MFC], EnablePriorityComparisonHandler
- CAnimationController [MFC], EnableStoryboardEventHandler
- CAnimationController [MFC], FindAnimationGroup
- CAnimationController [MFC], FindAnimationObject
- CAnimationController [MFC], GetKeyframeStoryboardStart
- CAnimationController [MFC], GetUIAnimationManager
- CAnimationController [MFC], GetUIAnimationTimer
- CAnimationController [MFC], GetUITransitionFactory
- CAnimationController [MFC], GetUITransitionLibrary
- CAnimationController [MFC], IsAnimationInProgress
- CAnimationController [MFC], IsValid
- CAnimationController [MFC], OnAnimationIntegerValueChanged
- CAnimationController [MFC], OnAnimationManagerStatusChanged
- CAnimationController [MFC], OnAnimationTimerPostUpdate
- CAnimationController [MFC], OnAnimationTimerPreUpdate
- CAnimationController [MFC], OnAnimationTimerRenderingTooSlow
- CAnimationController [MFC], OnAnimationValueChanged
- CAnimationController [MFC], OnBeforeAnimationStart
- CAnimationController [MFC], OnHasPriorityCancel
- CAnimationController [MFC], OnHasPriorityCompress
- CAnimationController [MFC], OnHasPriorityConclude
- CAnimationController [MFC], OnHasPriorityTrim
- CAnimationController [MFC], OnStoryboardStatusChanged
- CAnimationController [MFC], OnStoryboardUpdated
- CAnimationController [MFC], RemoveAllAnimationGroups
- CAnimationController [MFC], RemoveAnimationGroup
- CAnimationController [MFC], RemoveAnimationObject
- CAnimationController [MFC], RemoveTransitions
- CAnimationController [MFC], ScheduleGroup
- CAnimationController [MFC], SetRelatedWnd
- CAnimationController [MFC], UpdateAnimationManager
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], OnAfterSchedule
- CAnimationController [MFC], gkeyframeStoryboardStart
- CAnimationController [MFC], m_bIsValid
- CAnimationController [MFC], m_lstAnimationGroups
- CAnimationController [MFC], m_pAnimationManager
- CAnimationController [MFC], m_pAnimationTimer
- CAnimationController [MFC], m_pRelatedWnd
- CAnimationController [MFC], m_pTransitionFactory
- CAnimationController [MFC], m_pTransitionLibrary
ms.assetid: ed294c98-695e-40a6-b940-33ef1d40aa6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ec93c2d39206bbc0c3076835f55e624d3eef715
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356919"
---
# <a name="canimationcontroller-class"></a>CAnimationController 类
实现动画控制器，它为创建和管理动画提供了中央接口。  
  
## <a name="syntax"></a>语法  
  
```  
class CAnimationController : public CObject;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationController::CAnimationController](#canimationcontroller)|构造一个动画控制器。|  
|[CAnimationController:: ~ CAnimationController](#canimationcontroller__~canimationcontroller)|析构函数。 当动画控制器对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationController::AddAnimationObject](#addanimationobject)|将动画对象添加到动画控制器所属的组。|  
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|向组添加关键帧。|  
|[CAnimationController::AnimateGroup](#animategroup)|准备要运行动画的组和 （可选） 对其进行安排。|  
|[CAnimationController::CleanUpGroup](#cleanupgroup)|已重载。 由框架调用以在计划动画时清理组。|  
|[CAnimationController::CreateKeyframe](#createkeyframe)|已重载。 创建取决于过渡的关键帧并将其添加到指定的组。|  
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|设置或释放在动画管理器的状态更改时调用的处理程序。|  
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|设置或版本的处理程序计时事件和处理程序计时更新。|  
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|设置或释放优先级比较处理程序以调用以决定是否计划的情节提要可以取消、 结束、 删除或压缩。|  
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|设置或释放情节提要状态和更新事件处理程序。|  
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|已重载。 查找依据其情节提要的动画组。|  
|[CAnimationController::FindAnimationObject](#findanimationobject)|查找包含指定的动画变量的动画对象。|  
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|返回标识情节提要的开头的关键帧。|  
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|提供对封装 IUIAnimationManager 对象访问。|  
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|提供对封装 IUIAnimationTimer 对象访问。|  
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|一个指向 IUIAnimationTransitionFactory 接口或 NULL，如果转换库创建失败。|  
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|提供对封装 IUIAnimationTransitionLibrary 对象访问。|  
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|指示是否在至少一个组在播放动画。|  
|[CAnimationController::IsValid](#isvalid)|指示动画控制器是否有效。|  
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|动画变量的整数值已更改时由框架调用。|  
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|由框架调用以响应来自动画管理器的 StatusChanged 事件。|  
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|动画更新完成后，由框架调用。|  
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|在动画更新开始之前，由框架调用。|  
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|当动画呈现帧速率低于最小的理想帧速率时由框架调用。|  
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|动画变量的值已更改时由框架调用。|  
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|由框架调用右在计划动画之前。|  
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|由框架调用以便解决计划冲突。|  
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|由框架调用以便解决计划冲突。|  
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|由框架调用以便解决计划冲突。|  
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|由框架调用以便解决计划冲突。|  
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|情节提要状态已更改时由框架调用。|  
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|情节提要已更新时，由框架调用。|  
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|从动画控制器中删除所有动画组。|  
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|从动画控制器中删除具有指定 ID 的动画组。|  
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|从动画控制器中删除的动画对象。|  
|[CAnimationController::RemoveTransitions](#removetransitions)|从属于指定的组的动画对象中删除转换。|  
|[CAnimationController::ScheduleGroup](#schedulegroup)|计划动画。|  
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|建立动画控制器和一个窗口之间的关系。|  
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|指示要更新的所有动画变量的值的动画管理器。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationController::CleanUpGroup](#cleanupgroup)|已重载。 清理组帮助器。|  
|[CAnimationController::OnAfterSchedule](#onafterschedule)|当指定组动画刚刚安排好时由框架调用。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|关键帧，表示情节提要的开头。|  
|[CAnimationController::m_bIsValid](#m_bisvalid)|指定动画控制器是否为有效。 如果当前操作系统不支持 Windows 动画 API，此成员设置为 FALSE。|  
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|属于此动画控制器的动画组的列表。|  
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|将存储指向动画管理器 COM 对象的指针。|  
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|将存储指向动画计时器 COM 对象的指针。|  
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|指向相关的 CWnd 对象，可以自动重新绘制动画管理器的状态已更改，或后更新事件发生时的指针。 可以为 NULL。|  
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|将存储指向转换工厂 COM 对象的指针。|  
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|将存储指向转换库 COM 对象的指针。|  
  
## <a name="remarks"></a>备注  
 CAnimationController 类是管理动画的键类。 你可能创建的动画控制器的一个或多个实例应用程序中，并 （可选） 将的动画控制器实例连接到使用 CAnimationController::SetRelatedWnd CWnd 对象。 此连接需要 WM_PAINT 时发送消息到相关的窗口自动动画管理器状态已更改或已更新动画计时器。 如果不启用此关系，则必须重绘手动显示动画的窗口。 为此目的你可以从 CAnimationController 派生一个类和重写 OnAnimationManagerStatusChanged 和/或 OnAnimationTimerPostUpdate 并使一个或多个 windows 在必要时无效。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAnimationController`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="_dtorcanimationcontroller"></a>  CAnimationController:: ~ CAnimationController  
 析构函数。 当动画控制器对象被销毁时调用。  
  
```  
virtual ~CAnimationController(void);
```   
  
##  <a name="addanimationobject"></a>  CAnimationController::AddAnimationObject  
 将动画对象添加到动画控制器所属的组。  
  
```  
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```  
  
### <a name="parameters"></a>参数  
 `pObject`  
 指向的动画对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则其中已添加 pObject 的现有或新动画组指向的指针如果 pObject 已添加到另一个动画控制器所属的组，则为 NULL。  
  
### <a name="remarks"></a>备注  
 调用此方法以添加到动画控制器的动画对象。 一个对象将添加到对象的 GroupID 根据组 （请参阅 CAnimationBaseObject::SetID）。 如果它是使用指定的 GroupID 所添加的第一个对象，动画控制器将创建一个新的组。 动画对象可以添加到仅一个动画控制器。 如果你需要将对象添加到另一个控制器，则应首先调用 RemoveAnimationObject。 如果你已添加到组为对象调用与新 GroupID SetID，将从旧的组中删除并添加到具有指定 ID 的另一个组对象  
  
##  <a name="addkeyframetogroup"></a>  CAnimationController::AddKeyframeToGroup  
 向组添加关键帧。  
  
```  
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,  
    CBaseKeyFrame* pKeyframe);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定组 id。  
  
 `pKeyframe`  
 指向一个关键帧的指针。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 通常你不需要调用此方法，请改用 CAnimationController::CreateKeyframe，它创建并自动向组添加创建的关键帧。  
  
##  <a name="animategroup"></a>  CAnimationController::AnimateGroup  
 准备要运行动画的组和 （可选） 对其进行安排。  
  
```  
BOOL AnimateGroup(
    UINT32 nGroupID,  
    BOOL bScheduleNow = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定 GroupID。  
  
 `bScheduleNow`  
 指定是否要立即运行动画。  
  
### <a name="return-value"></a>返回值  
 如果成功计划并运行动画，则为 TRUE。  
  
### <a name="remarks"></a>备注  
 此方法执行创建情节提要、 添加动画变量、 应用转换和设置关键帧的实际工作。 很可能要延迟计划如果 bScheduleNow 设置为 FALSE。 在这种情况下指定的组将保存已设置动画的情节提要。 此时，你可以设置的情节提要和动画变量的事件。 当你实际上需要运行动画调用 CAnimationController::ScheduleGroup。  
  
##  <a name="canimationcontroller"></a>  CAnimationController::CAnimationController  
 构造一个动画控制器。  
  
```  
CAnimationController(void);
```   
  
##  <a name="cleanupgroup"></a>  CAnimationController::CleanUpGroup  
 由框架调用以在计划动画时清理组。  
  
```  
void CleanUpGroup(UINT32 nGroupID);  
void CleanUpGroup(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定 GroupID。  
  
 `pGroup`  
 指向要清理的动画组的指针。  
  
### <a name="remarks"></a>备注  
 因为动画已计划之后，它们是不相关，此方法会从指定的组中，删除所有转换和关键帧。  
  
##  <a name="createkeyframe"></a>  CAnimationController::CreateKeyframe  
 创建取决于过渡的关键帧并将其添加到指定的组。  
  
```  
CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,  
    CBaseTransition* pTransition);

 
CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,  
    CBaseKeyFrame* pKeyframe,  
    UI_ANIMATION_SECONDS offset = 0.0);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定要为其创建关键帧的组 ID。  
  
 `pTransition`  
 指向过渡的指针。 关键帧将插入到此过渡后的情节提要。  
  
 `pKeyframe`  
 指向此关键帧的基关键帧的指针。  
  
 `offset`  
 由 pKeyframe 指定的基关键帧的偏移量（以秒为单位）。  
  
### <a name="return-value"></a>返回值  
 指向新创建的关键帧（如果函数成功）的指针。  
  
### <a name="remarks"></a>备注  
 可以存储返回的指针，也可以在新创建的关键帧的基础上创建其他关键帧（请参阅第二个重载）。 可以在关键帧处开始过渡 - 请参阅 CBaseTransition::SetKeyframes。 不需要删除以这种方式创建的关键帧，因为动画组会自动删除它们。 基于其他关键帧和过渡创建关键帧时请小心，避免循环引用。  
  
##  <a name="enableanimationmanagerevent"></a>  CAnimationController::EnableAnimationManagerEvent  
 设置或释放在动画管理器的状态更改时调用的处理程序。  
  
```  
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bEnable`  
 指定是否要设置或释放一个处理程序。  
  
### <a name="return-value"></a>返回值  
 如果处理程序已成功设置或发布，则为 TRUE。  
  
### <a name="remarks"></a>备注  
 处理程序设置 （启用） 时 Windows 动画在动画管理器的状态更改时调用 OnAnimationManagerStatusChanged。  
  
##  <a name="enableanimationtimereventhandler"></a>  CAnimationController::EnableAnimationTimerEventHandler  
 设置或版本的处理程序计时事件和处理程序计时更新。  
  
```  
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,  
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```  
  
### <a name="parameters"></a>参数  
 `bEnable`  
 指定是否要设置或释放处理程序。  
  
 `idleBehavior`  
 指定空闲行为计时器更新处理程序。  
  
### <a name="return-value"></a>返回值  
 如果处理程序已成功设置或释放; 则为 TRUE如果此属性为 FALSE 的方法进行第二次调用而不释放这些处理程序首先，或如果任何其他发生错误。  
  
### <a name="remarks"></a>备注  
 在处理程序设置 （启用） Windows 动画 API 调用 OnAnimationTimerPreUpdate，OnAnimationTimerPostUpdate，OnRenderingTooSlow 方法。 你需要启用动画计时器，以便允许 Windows 动画 API 更新情节提要。 否则，你需要调用 CAnimationController::UpdateAnimationManager，以便直接动画管理器来更新所有动画变量的值。  
  
##  <a name="enableprioritycomparisonhandler"></a>  CAnimationController::EnablePriorityComparisonHandler  
 设置或释放优先级比较处理程序以调用以决定是否计划的情节提要可以取消、 结束、 删除或压缩。  
  
```  
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```  
  
### <a name="parameters"></a>参数  
 `dwHandlerType`  
 UI_ANIMATION_PHT_ 组合标志 （请参阅备注），它指定要设置或释放哪些处理程序。  
  
### <a name="return-value"></a>返回值  
 如果处理程序已成功设置或发布，则为 TRUE。  
  
### <a name="remarks"></a>备注  
 Windows 动画处理程序设置 （启用） 时调用的以下的虚方法，具体取决于 dwHandlerType: OnHasPriorityCancel、 OnHasPriorityConclude、 OnHasPriorityTrim、 OnHasPriorityCompress。 dwHandler 可以是以下标志的组合： UI_ANIMATION_PHT_NONE-版本所有处理程序 ui_animation_pht_cancel，则-设置取消比较处理程序 ui_animation_pht_conclude，则-设置结束比较处理程序 ui_animation_pht_compress，则-设置压缩比较处理程序-设置剪裁比较处理程序 UI_ANIMATION_PHT_CANCEL_REMOVE-删除取消比较处理程序 UI_ANIMATION_PHT_CONCLUDE_REMOVE-ui_animation_pht_trim，则删除结束比较处理程序 UI_ANIMATION_PHT_COMPRESS_删除-删除压缩比较处理程序 UI_ANIMATION_PHT_TRIM_REMOVE-删除剪裁比较处理程序  
  
##  <a name="enablestoryboardeventhandler"></a>  CAnimationController::EnableStoryboardEventHandler  
 设置或释放情节提要状态和更新事件处理程序。  
  
```  
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,  
    BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定组 id。  
  
 `bEnable`  
 指定是否要设置或释放一个处理程序。  
  
### <a name="return-value"></a>返回值  
 如果处理程序已成功设置或释放; 则为 TRUE如果现在找不到指定的动画组或指定组的动画不具有已启动，并且其内部的情节提要为 NULL，则为 FALSE。  
  
### <a name="remarks"></a>备注  
 当设置处理程序 （启用） Windows 动画 API 调用 OnStoryboardStatusChanges 和 OnStoryboardUpdated 虚拟方法。 处理程序必须设置后 CAnimationController::Animate 已调用指定的动画组中，因为它会封装的 IUIAnimationStoryboard 对象。  
  
##  <a name="findanimationgroup"></a>  CAnimationController::FindAnimationGroup  
 查找动画组通过其组 id。  
  
```  
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);  
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定 GroupID。  
  
 `pStoryboard`  
 指向情节提要的指针。  
  
### <a name="return-value"></a>返回值  
 动画组或者如果找不到具有指定 ID 的组的为 NULL 指针。  
  
### <a name="remarks"></a>备注  
 使用此方法在运行时查找动画组。 创建一个组并将其时具有特定 GroupID 的第一个动画对象将被添加到动画控制器添加到动画组的内部列表。  
  
##  <a name="findanimationobject"></a>  CAnimationController::FindAnimationObject  
 查找包含指定的动画变量的动画对象。  
  
```  
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,  
    CAnimationBaseObject** ppObject,  
    CAnimationGroup** ppGroup);
```  
  
### <a name="parameters"></a>参数  
 `pVariable`  
 指向动画变量的指针。  
  
 `ppObject`  
 输出。 包含指向动画对象或 NULL。  
  
 `ppGroup`  
 输出。 包含指向包含的动画对象或为 NULL 的动画组。  
  
### <a name="return-value"></a>返回值  
 如果对象; 如果未找到，则返回 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 具有需要查找从传入的动画变量的动画对象时，从事件处理程序调用。  
  
##  <a name="g_keyframestoryboardstart"></a>  CAnimationController::gkeyframeStoryboardStart  
 关键帧，表示情节提要的开头。  
  
```  
static CBaseKeyFrame gkeyframeStoryboardStart;  
```  
  
##  <a name="getkeyframestoryboardstart"></a>  CAnimationController::GetKeyframeStoryboardStart  
 返回标识情节提要的开头的关键帧。  
  
```  
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```  
  
### <a name="return-value"></a>返回值  
 指向标识情节提要的开头的基本关键帧的指针。  
  
### <a name="remarks"></a>备注  
 获取要基于那一刻情节提要的开始的时间的任何其他关键帧或转换此关键帧。  
  
##  <a name="getuianimationmanager"></a>  CAnimationController::GetUIAnimationManager  
 提供对封装 IUIAnimationManager 对象访问。  
  
```  
IUIAnimationManager* GetUIAnimationManager();
```  
  
### <a name="return-value"></a>返回值  
 一个指向 IUIAnimationManager 接口或 NULL，如果动画管理器创建失败。  
  
### <a name="remarks"></a>备注  
 如果当前操作系统不支持 Windows 动画 API，此方法返回 NULL，并且在此之后 CAnimationController::IsValid 上的所有后续调用会返回 FALSE。 你可能需要访问 IUIAnimationManager 以便调用其接口方法，其未包装的动画控制器。  
  
##  <a name="getuianimationtimer"></a>  CAnimationController::GetUIAnimationTimer  
 提供对封装 IUIAnimationTimer 对象访问。  
  
```  
IUIAnimationTimer* GetUIAnimationTimer();
```  
  
### <a name="return-value"></a>返回值  
 指向 IUIAnimationTimer 接口或 NULL，如果创建的动画计时器失败的指针。  
  
### <a name="remarks"></a>备注  
 如果当前操作系统不支持 Windows 动画 API，此方法返回 NULL，并且在此之后 CAnimationController::IsValid 上的所有后续调用会返回 FALSE。  
  
##  <a name="getuitransitionfactory"></a>  CAnimationController::GetUITransitionFactory  
 一个指向 IUIAnimationTransitionFactory 接口或 NULL，如果转换库创建失败。  
  
```  
IUIAnimationTransitionFactory* GetUITransitionFactory();
```  
  
### <a name="return-value"></a>返回值  
 一个指向 IUIAnimationTransitionFactory 或 NULL，如果转换工厂创建失败。  
  
### <a name="remarks"></a>备注  
 如果当前操作系统不支持 Windows 动画 API，此方法返回 NULL，并且在此之后 CAnimationController::IsValid 上的所有后续调用会返回 FALSE。  
  
##  <a name="getuitransitionlibrary"></a>  CAnimationController::GetUITransitionLibrary  
 提供对封装 IUIAnimationTransitionLibrary 对象访问。  
  
```  
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```  
  
### <a name="return-value"></a>返回值  
 一个指向 IUIAnimationTransitionLibrary 接口或 NULL，如果转换库创建失败。  
  
### <a name="remarks"></a>备注  
 如果当前操作系统不支持 Windows 动画 API，此方法返回 NULL，并且在此之后 CAnimationController::IsValid 上的所有后续调用会返回 FALSE。  
  
##  <a name="isanimationinprogress"></a>  CAnimationController::IsAnimationInProgress  
 指示是否在至少一个组在播放动画。  
  
```  
virtual BOOL IsAnimationInProgress();
```  
  
### <a name="return-value"></a>返回值  
 如果没有此动画控制器; 正在动画，则返回 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 检查的动画管理器的状态，并返回 TRUE，如果状态为 UI_ANIMATION_MANAGER_BUSY。  
  
##  <a name="isvalid"></a>  CAnimationController::IsValid  
 指示动画控制器是否有效。  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果有效，则为动画控制器，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此方法返回 FALSE，仅当 Windows 动画 API 不支持当前的操作系统和动画管理器创建失败，因为它未注册。 你需要至少一次在初始化 COM 库，若要使此标志设置后，调用 GetUIAnimationManager。  
  
##  <a name="m_bisvalid"></a>  CAnimationController::m_bIsValid  
 指定动画控制器是否为有效。 如果当前操作系统不支持 Windows 动画 API，此成员设置为 FALSE。  
  
```  
BOOL m_bIsValid;  
```  
  
##  <a name="m_lstanimationgroups"></a>  CAnimationController::m_lstAnimationGroups  
 属于此动画控制器的动画组的列表。  
  
```  
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;  
```  
  
##  <a name="m_panimationmanager"></a>  CAnimationController::m_pAnimationManager  
 将存储指向动画管理器 COM 对象的指针。  
  
```  
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;  
```  
  
##  <a name="m_panimationtimer"></a>  CAnimationController::m_pAnimationTimer  
 将存储指向动画计时器 COM 对象的指针。  
  
```  
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;  
```  
  
##  <a name="m_prelatedwnd"></a>  CAnimationController::m_pRelatedWnd  
 指向相关的 CWnd 对象，可以自动重新绘制动画管理器的状态已更改，或后更新事件发生时的指针。 可以为 NULL。  
  
```  
CWnd* m_pRelatedWnd;  
```  
  
##  <a name="m_ptransitionfactory"></a>  CAnimationController::m_pTransitionFactory  
 将存储指向转换工厂 COM 对象的指针。  
  
```  
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;  
```  
  
##  <a name="m_ptransitionlibrary"></a>  CAnimationController::m_pTransitionLibrary  
 将存储指向转换库 COM 对象的指针。  
  
```  
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;  
```  
  
##  <a name="onafterschedule"></a>  CAnimationController::OnAfterSchedule  
 当指定组动画刚刚安排好时由框架调用。  
  
```  
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>参数  
 `pGroup`  
 指向已计划的动画组的指针。  
  
### <a name="remarks"></a>备注  
 默认实现从指定的组中删除的关键帧并将转换从属于指定组的动画变量。 可在重写派生类才能根据动画安排任何其他操作。  
  
##  <a name="onanimationintegervaluechanged"></a>  CAnimationController::OnAnimationIntegerValueChanged  
 动画变量的整数值已更改时由框架调用。  
  
```  
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,  
    CAnimationBaseObject* pObject,  
    IUIAnimationVariable* variable,  
    INT32 newValue,  
    INT32 prevValue);
```  
  
### <a name="parameters"></a>参数  
 `pGroup`  
 已更改到动画组包含其值的动画对象的指针。  
  
 `pObject`  
 指向一个包含已更改其值的动画变量的动画对象的指针。  
  
 `variable`  
 指向动画变量的指针。  
  
 `newValue`  
 指定新值。  
  
 `prevValue`  
 指定以前的值。  
  
### <a name="remarks"></a>备注  
 如果使用为特定的动画变量或动画对象调用 EnableIntegerValueChangedEvent 启用动画变量事件，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。  
  
##  <a name="onanimationmanagerstatuschanged"></a>  CAnimationController::OnAnimationManagerStatusChanged  
 由框架调用以响应来自动画管理器的 StatusChanged 事件。  
  
```  
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,  
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```  
  
### <a name="parameters"></a>参数  
 `newStatus`  
 新动画管理器状态。  
  
 `previousStatus`  
 以前的动画管理器状态。  
  
### <a name="remarks"></a>备注  
 如果启用与 EnableAnimationManagerEvent 动画管理器事件，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 如果使用 SetRelatedWnd 已设置，默认实现将更新相关的窗口。  
  
##  <a name="onanimationtimerpostupdate"></a>  CAnimationController::OnAnimationTimerPostUpdate  
 动画更新完成后，由框架调用。  
  
```  
virtual void OnAnimationTimerPostUpdate();
```  
  
### <a name="remarks"></a>备注  
 如果启用使用 EnableAnimationTimerEventHandler 的计时器事件处理程序，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。  
  
##  <a name="onanimationtimerpreupdate"></a>  CAnimationController::OnAnimationTimerPreUpdate  
 在动画更新开始之前，由框架调用。  
  
```  
virtual void OnAnimationTimerPreUpdate();
```  
  
### <a name="remarks"></a>备注  
 如果启用使用 EnableAnimationTimerEventHandler 的计时器事件处理程序，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。  
  
##  <a name="onanimationtimerrenderingtooslow"></a>  CAnimationController::OnAnimationTimerRenderingTooSlow  
 当动画呈现帧速率低于最小的理想帧速率时由框架调用。  
  
```  
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```  
  
### <a name="parameters"></a>参数  
 `fps`  
 每秒帧数中的当前帧速率。  
  
### <a name="remarks"></a>备注  
 如果启用使用 EnableAnimationTimerEventHandler 的计时器事件处理程序，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 通过调用 IUIAnimationTimer::SetFrameRateThreshold 指定最小的理想帧速率。  
  
##  <a name="onanimationvaluechanged"></a>  CAnimationController::OnAnimationValueChanged  
 动画变量的值已更改时由框架调用。  
  
```  
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,  
    CAnimationBaseObject* pObject,  
    IUIAnimationVariable* variable,  
    DOUBLE newValue,  
    DOUBLE prevValue);
```  
  
### <a name="parameters"></a>参数  
 `pGroup`  
 已更改到动画组包含其值的动画对象的指针。  
  
 `pObject`  
 指向一个包含已更改其值的动画变量的动画对象的指针。  
  
 `variable`  
 指向动画变量的指针。  
  
 `newValue`  
 指定新值。  
  
 `prevValue`  
 指定以前的值。  
  
### <a name="remarks"></a>备注  
 如果使用为特定的动画变量或动画对象调用 EnableValueChangedEvent 启用动画变量事件，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。  
  
##  <a name="onbeforeanimationstart"></a>  CAnimationController::OnBeforeAnimationStart  
 由框架调用右在计划动画之前。  
  
```  
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>参数  
 `pGroup`  
 指向其动画即将开始的动画组的指针。  
  
### <a name="remarks"></a>备注  
 此调用路由到相关 CWnd，并且可以在指定组的动画开始之前执行其他任何操作的派生类中重写。  
  
##  <a name="onhasprioritycancel"></a>  CAnimationController::OnHasPriorityCancel  
 由框架调用以便解决计划冲突。  
  
```  
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>参数  
 `pGroupScheduled`  
 拥有当前已计划的情节提要的组。  
  
 `pGroupNew`  
 拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。  
  
 `priorityEffect`  
 如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。  
  
### <a name="return-value"></a>返回值  
 如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TURE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。  
  
### <a name="remarks"></a>备注  
 如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_CANCEL，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 阅读 Windows 动画 API 文档，了解有关冲突管理的详细信息 (http://msdn.microsoft.com/library/dd371759(VS.85).aspx)。  
  
##  <a name="onhasprioritycompress"></a>  CAnimationController::OnHasPriorityCompress  
 由框架调用以便解决计划冲突。  
  
```  
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>参数  
 `pGroupScheduled`  
 拥有当前已计划的情节提要的组。  
  
 `pGroupNew`  
 拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。  
  
 `priorityEffect`  
 如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。  
  
### <a name="return-value"></a>返回值  
 如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TURE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。  
  
### <a name="remarks"></a>备注  
 如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_COMPRESS，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 阅读 Windows 动画 API 文档，了解有关冲突管理的详细信息 (http://msdn.microsoft.com/library/dd371759(VS.85).aspx)。  
  
##  <a name="onhaspriorityconclude"></a>  CAnimationController::OnHasPriorityConclude  
 由框架调用以便解决计划冲突。  
  
```  
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>参数  
 `pGroupScheduled`  
 拥有当前已计划的情节提要的组。  
  
 `pGroupNew`  
 拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。  
  
 `priorityEffect`  
 如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。  
  
### <a name="return-value"></a>返回值  
 如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TURE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。  
  
### <a name="remarks"></a>备注  
 如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_CONCLUDE，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 阅读 Windows 动画 API 文档，了解有关冲突管理的详细信息 (http://msdn.microsoft.com/library/dd371759(VS.85).aspx)。  
  
##  <a name="onhasprioritytrim"></a>  CAnimationController::OnHasPriorityTrim  
 由框架调用以便解决计划冲突。  
  
```  
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,  
    CAnimationGroup* pGroupNew,  
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```  
  
### <a name="parameters"></a>参数  
 `pGroupScheduled`  
 拥有当前已计划的情节提要的组。  
  
 `pGroupNew`  
 拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。  
  
 `priorityEffect`  
 如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。  
  
### <a name="return-value"></a>返回值  
 如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TURE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。  
  
### <a name="remarks"></a>备注  
 如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_TRIM，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 阅读 Windows 动画 API 文档，了解有关冲突管理的详细信息 (http://msdn.microsoft.com/library/dd371759(VS.85).aspx)。  
  
##  <a name="onstoryboardstatuschanged"></a>  CAnimationController::OnStoryboardStatusChanged  
 情节提要状态已更改时由框架调用。  
  
```  
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,  
    UI_ANIMATION_STORYBOARD_STATUS newStatus,  
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```  
  
### <a name="parameters"></a>参数  
 `pGroup`  
 指向拥有其状态的情节提要的动画组的已更改。  
  
 `newStatus`  
 指定的新状态。  
  
 `previousStatus`  
 指定以前的状态。  
  
### <a name="remarks"></a>备注  
 如果你启用使用 CAnimationController::EnableStoryboardEventHandler 的情节提要事件，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。  
  
##  <a name="onstoryboardupdated"></a>  CAnimationController::OnStoryboardUpdated  
 情节提要已更新时，由框架调用。  
  
```  
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>参数  
 `pGroup`  
 指向拥有的情节提要的组的指针。  
  
### <a name="remarks"></a>备注  
 如果你启用使用 CAnimationController::EnableStoryboardEventHandler 的情节提要事件，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。  
  
##  <a name="removeallanimationgroups"></a>  CAnimationController::RemoveAllAnimationGroups  
 从动画控制器中删除所有动画组。  
  
```  
void RemoveAllAnimationGroups();
```  
  
### <a name="remarks"></a>备注  
 所有组都将删除，其指针，如果存储在应用程序级别，必须都将失效。 如果要删除组的 CAnimationGroup::m_bAutodestroyAnimationObjects 为 TRUE，则将删除属于该组的所有动画对象;否则为其父动画控制器的引用将设置为 NULL，并将它们添加到另一个控制器。  
  
##  <a name="removeanimationgroup"></a>  CAnimationController::RemoveAnimationGroup  
 从动画控制器中删除具有指定 ID 的动画组。  
  
```  
void RemoveAnimationGroup(UINT32 nGroupID);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定动画组 id。  
  
### <a name="remarks"></a>备注  
 此方法从组的内部列表中移除的动画组并将其删除，因此如果你存储指向动画该组的指针，它必须使其无效。 如果 CAnimationGroup::m_bAutodestroyAnimationObjects 为 TRUE，则将删除属于该组的所有动画对象;否则为其父动画控制器的引用将设置为 NULL，并将它们添加到另一个控制器。  
  
##  <a name="removeanimationobject"></a>  CAnimationController::RemoveAnimationObject  
 从动画控制器中删除的动画对象。  
  
```  
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,  
    BOOL bNoDelete = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `pObject`  
 指向的动画对象的指针。  
  
 `bNoDelete`  
 如果此参数为 TRUE 的对象将不会删除在删除时。  
  
### <a name="remarks"></a>备注  
 从动画控制器和动画组中移除的动画对象。 如果特定的对象应不进行动画处理，或者如果你需要将对象移动到另一个动画控制器，请调用此函数。 在最后一个事例 bNoDelete 必须为 TRUE。  
  
##  <a name="removetransitions"></a>  CAnimationController::RemoveTransitions  
 从属于指定的组的动画对象中删除转换。  
  
```  
void RemoveTransitions(UINT32 nGroupID);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定组 id。  
  
### <a name="remarks"></a>备注  
 组循环访问其动画对象，并为每个动画对象调用 ClearTransitions(FALSE)。 已计划动画之后，将由框架调用此方法。  
  
##  <a name="schedulegroup"></a>  CAnimationController::ScheduleGroup  
 计划动画。  
  
```  
BOOL ScheduleGroup(
    UINT32 nGroupID,  
    UI_ANIMATION_SECONDS time = 0.0);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定动画要计划的组 ID。  
  
 `time`  
 指定计划的时间。  
  
### <a name="return-value"></a>返回值  
 如果已成功计划了动画，则为 TRUE。 如果尚未创建情节提要，否则会发生其他错误，则为 FALSE。  
  
### <a name="remarks"></a>备注  
 你必须设置为 FALSE 的以前 ScheduleGroup 参数 bScheduleNow 调用 AnimateGroup。 你可以指定从 IUIAnimationTimer::GetTime 获取所需的动画时间。 如果时间参数为 0.0，动画计划在当前时间。  
  
##  <a name="setrelatedwnd"></a>  CAnimationController::SetRelatedWnd  
 建立动画控制器和一个窗口之间的关系。  
  
```  
void SetRelatedWnd(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向要设置的窗口对象的指针。  
  
### <a name="remarks"></a>备注  
 如果设置相关的 CWnd 对象，动画控制器都可以以自动更新它 （发送 WM_PAINT 消息） 的动画管理器的状态已更改或计时器后更新事件发生时。  
  
##  <a name="updateanimationmanager"></a>  CAnimationController::UpdateAnimationManager  
 指示要更新的所有动画变量的值的动画管理器。  
  
```  
virtual void UpdateAnimationManager();
```  
  
### <a name="remarks"></a>备注  
 调用此方法将推进到当前时间的动画管理器、 根据需要更改情节提要的状态和更新到相应的任何动画变量内插值。 此方法在内部调用 IUIAnimationTimer::GetTime(timeNow) 和 IUIAnimationManager::Update(timeNow)。 重写此方法在派生类以自定义此行为。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
