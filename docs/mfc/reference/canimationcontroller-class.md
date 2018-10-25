---
title: CAnimationController 类 |Microsoft Docs
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
ms.openlocfilehash: c9f17eea48e01d12df103382483b352e5dce46b7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080554"
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
|[CAnimationController::AnimateGroup](#animategroup)|准备要运行动画的组，并根据需要对其进行安排。|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|已重载。 由框架调用以在计划动画时清理组。|
|[CAnimationController::CreateKeyframe](#createkeyframe)|已重载。 创建取决于过渡的关键帧并将其添加到指定的组。|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|设置或释放动画管理器的状态更改时要调用的处理程序。|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|设置或释放的计时事件的处理程序和计时更新处理程序。|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|设置或释放调用以确定是否计划的情节提要可以取消、 得出的结论是，修整或压缩的优先级比较处理程序。|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|设置或释放的情节提要状态和更新事件的处理程序。|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|已重载。 查找其演示图板动画组。|
|[CAnimationController::FindAnimationObject](#findanimationobject)|查找动画对象，其中包含指定的动画变量。|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|返回标识启动情节提要的一个关键帧。|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|提供对封装 IUIAnimationManager 对象的访问。|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|提供对封装 IUIAnimationTimer 对象的访问。|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|一个指向 IUIAnimationTransitionFactory 接口或如果创建的转换库失败，则为 NULL。|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|提供对封装 IUIAnimationTransitionLibrary 对象的访问。|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|指示至少一个组是否正在播放动画。|
|[CAnimationController::IsValid](#isvalid)|指示动画控制器是否有效。|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|动画变量的整数值发生更改时由框架调用。|
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|由框架调用以响应 StatusChanged 事件从动画管理器。|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|动画更新完成后，由框架调用。|
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|在动画更新开始之前，由框架调用。|
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|当动画呈现帧速率低于最小的理想帧速率时由框架调用。|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|动画变量的值发生更改时由框架调用。|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|之前由框架调用正确计划动画。|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|由框架调用以便解决计划冲突。|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|由框架调用以便解决计划冲突。|
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|由框架调用以便解决计划冲突。|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|由框架调用以便解决计划冲突。|
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|情节提要状态发生更改时由框架调用。|
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|已更新情节提要时由框架调用。|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|从动画控制器中移除所有动画组。|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|从动画控制器中删除具有指定 ID 的动画组。|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|从动画控制器中删除动画对象。|
|[CAnimationController::RemoveTransitions](#removetransitions)|从属于指定组的动画对象中删除转换。|
|[CAnimationController::ScheduleGroup](#schedulegroup)|计划动画。|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|建立动画控制器和一个窗口之间的关系。|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|指示动画管理器来更新所有的动画变量的值。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|已重载。 清理组帮助程序。|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|当动画，以指定组只是已计划时，由框架调用。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|表示开始情节提要的一个关键帧。|
|[CAnimationController::m_bIsValid](#m_bisvalid)|指定动画控制器是否为有效。 如果当前操作系统不支持 Windows 动画 API，此成员设置为 FALSE。|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|属于此动画控制器的动画组的列表。|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|存储指向动画管理器 COM 对象的指针。|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|存储指向动画计时器 COM 对象的指针。|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|指向相关的 CWnd 对象，可以将自动重绘动画管理器的状态已更改，或后更新事件发生时的指针。 可以为 NULL。|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|存储指向转换工厂 COM 对象的指针。|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|存储指向转换库 COM 对象的指针。|

## <a name="remarks"></a>备注

CAnimationController 类是管理动画的关键类。 您可能的应用程序中创建的动画控制器的一个或多个实例，连接到使用 CAnimationController::SetRelatedWnd CWnd 对象 （可选） 的动画控制器实例。 自动将发送 WM_PAINT 消息到相关的窗口动画管理器状态已更改或已更新动画计时器时需要此连接。 如果不启用此关系，则必须重绘一个窗口，手动显示动画。 实现此目的，您可以从 CAnimationController 派生一个类并覆盖 OnAnimationManagerStatusChanged 和/或 OnAnimationTimerPostUpdate 并使一个或多个 windows 在必要时。

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

*pObject*<br/>
指向动画对象的指针。

### <a name="return-value"></a>返回值

如果函数成功，则具有已 pObject 添加其中的现有或新动画组到指针如果已将 pObject 添加到另一个动画控制器所属的组，则为 NULL。

### <a name="remarks"></a>备注

调用此方法将动画对象添加到动画控制器。 一个对象将添加到对象的 GroupID 按照为组 （请参阅 CAnimationBaseObject::SetID）。 它是否与指定 GroupID 所添加的第一个对象，动画控制器将创建一个新组。 可以将的动画对象添加到仅一个动画控制器。 如果需要将对象添加到另一个控制器，则应首先调用 RemoveAnimationObject。 如果已添加到组的对象调用与新 GroupID SetID，将从旧的组中删除和添加到具有指定 ID 的另一个组对象

##  <a name="addkeyframetogroup"></a>  CAnimationController::AddKeyframeToGroup

向组添加关键帧。

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定组 id。

*pKeyframe*<br/>
指向一个关键帧的指针。

### <a name="return-value"></a>返回值

如果函数成功，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

通常不需要调用此方法，请改用 CAnimationController::CreateKeyframe，它创建并自动将创建关键帧添加到组。

##  <a name="animategroup"></a>  CAnimationController::AnimateGroup

准备要运行动画的组，并根据需要对其进行安排。

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定 GroupID。

*bScheduleNow*<br/>
指定是否要立即运行动画。

### <a name="return-value"></a>返回值

如果动画已成功计划和运行，则为 TRUE。

### <a name="remarks"></a>备注

此方法执行实际的工作创建情节提要、 添加动画变量、 应用转换和设置关键帧。 很可能要延迟计划如果 bScheduleNow 设置为 FALSE。 在这种情况下指定的组将保存已设置动画的情节提要。 此时，你可以设置的情节提要和动画变量的事件。 当你实际上需要运行动画调用 CAnimationController::ScheduleGroup。

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

*nGroupID*<br/>
指定 GroupID。

*pGroup*<br/>
指向要清除的动画组的指针。

### <a name="remarks"></a>备注

因为动画具有计划之后，它们是不相关，此方法会从指定的组中，删除所有转换和关键帧。

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

*nGroupID*<br/>
指定要为其创建关键帧的组 ID。

*pTransition*<br/>
指向过渡的指针。 关键帧将插入到此过渡后的情节提要。

*pKeyframe*<br/>
指向此关键帧的基关键帧的指针。

*offset*<br/>
由 pKeyframe 指定的基关键帧的偏移量（以秒为单位）。

### <a name="return-value"></a>返回值

指向新创建的关键帧（如果函数成功）的指针。

### <a name="remarks"></a>备注

可以存储返回的指针，也可以在新创建的关键帧的基础上创建其他关键帧（请参阅第二个重载）。 可以在关键帧处开始过渡 - 请参阅 CBaseTransition::SetKeyframes。 不需要删除以这种方式创建的关键帧，因为动画组会自动删除它们。 基于其他关键帧和过渡创建关键帧时请小心，避免循环引用。

##  <a name="enableanimationmanagerevent"></a>  CAnimationController::EnableAnimationManagerEvent

设置或释放动画管理器的状态更改时要调用的处理程序。

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
指定是否要设置或释放一个处理程序。

### <a name="return-value"></a>返回值

如果处理程序已成功设置或发布，则为 TRUE。

### <a name="remarks"></a>备注

当一个处理程序设置 （已启用） 时 Windows 动画调用 OnAnimationManagerStatusChanged 动画管理器的状态更改时。

##  <a name="enableanimationtimereventhandler"></a>  CAnimationController::EnableAnimationTimerEventHandler

设置或释放的计时事件的处理程序和计时更新处理程序。

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
指定是否设置或取消处理程序。

*idleBehavior*<br/>
指定空闲计时器更新处理程序的行为。

### <a name="return-value"></a>返回值

如果处理程序已成功设置或发布; 则为 TRUE而不释放在处理程序首先，为第二次调用如果此属性为 FALSE 方法或者其他任何错误。

### <a name="remarks"></a>备注

在处理程序设置 （已启用） 的 Windows 动画 API 调用 OnAnimationTimerPreUpdate，OnAnimationTimerPostUpdate，OnRenderingTooSlow 方法。 需要启用动画计时器，以便允许 Windows 动画 API 更新情节提要。 否则你将需要调用 CAnimationController::UpdateAnimationManager，若要指示动画管理器更新所有的动画变量的值。

##  <a name="enableprioritycomparisonhandler"></a>  CAnimationController::EnablePriorityComparisonHandler

设置或释放调用以确定是否计划的情节提要可以取消、 得出的结论是，修整或压缩的优先级比较处理程序。

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>参数

*dwHandlerType*<br/>
UI_ANIMATION_PHT_ 组合标志 （请参阅备注），它指定要设置或释放哪些处理程序。

### <a name="return-value"></a>返回值

如果处理程序已成功设置或发布，则为 TRUE。

### <a name="remarks"></a>备注

Windows 动画时设置 （已启用） 的处理程序调用以下虚拟方法具体取决于 dwHandlerType: OnHasPriorityCancel、 OnHasPriorityConclude、 OnHasPriorityTrim、 OnHasPriorityCompress。 dwHandler 可以是下列标志的组合： UI_ANIMATION_PHT_NONE-发布所有处理程序 ui_animation_pht_cancel，则-设置取消设置结束比较处理程序 ui_animation_pht_compress，则比较处理程序 ui_animation_pht_conclude，则--设置Compress 比较处理程序-设置剪裁比较处理程序 UI_ANIMATION_PHT_CANCEL_REMOVE-删除取消比较处理程序 UI_ANIMATION_PHT_CONCLUDE_REMOVE-ui_animation_pht_trim，则删除结束比较处理程序 UI_ANIMATION_PHT_COMPRESS_删除-删除压缩比较处理程序 UI_ANIMATION_PHT_TRIM_REMOVE-删除剪裁比较处理程序

##  <a name="enablestoryboardeventhandler"></a>  CAnimationController::EnableStoryboardEventHandler

设置或释放的情节提要状态和更新事件的处理程序。

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定组 id。

*bEnable*<br/>
指定是否要设置或释放一个处理程序。

### <a name="return-value"></a>返回值

如果处理程序已成功设置或发布; 则为 TRUE如果指定的动画组现在找到或尚未启动动画，以指定的组和其内部的情节提要为 NULL，则为 FALSE。

### <a name="remarks"></a>备注

当设置处理程序 （已启用） 的 Windows 动画 API 调用 OnStoryboardStatusChanges 和 OnStoryboardUpdated 虚拟方法。 一个处理程序后，必须设置 CAnimationController::Animate 已调用指定的动画组，因为它会封装的 IUIAnimationStoryboard 对象。

##  <a name="findanimationgroup"></a>  CAnimationController::FindAnimationGroup

查找动画组通过其组 id。

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定 GroupID。

*pStoryboard*<br/>
指向情节提要的指针。

### <a name="return-value"></a>返回值

一个指向动画组或如果找不到具有指定 ID 的组，则为 NULL。

### <a name="remarks"></a>备注

使用此方法在运行时查找动画组。 创建并添加到动画组的内部列表时具有特定 GroupID 的第一个动画对象添加到动画控制器组。

##  <a name="findanimationobject"></a>  CAnimationController::FindAnimationObject

查找动画对象，其中包含指定的动画变量。

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>参数

*pVariable*<br/>
指向动画变量的指针。

*ppObject*<br/>
输出。 包含指向动画对象或为 NULL。

*ppGroup*<br/>
输出。 包含指向包含的动画对象或为 NULL 的动画组。

### <a name="return-value"></a>返回值

如果找到对象; 则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

从事件处理程序需要查找从传入的动画变量的动画对象时调用。

##  <a name="g_keyframestoryboardstart"></a>  CAnimationController::gkeyframeStoryboardStart

表示开始情节提要的一个关键帧。

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

##  <a name="getkeyframestoryboardstart"></a>  CAnimationController::GetKeyframeStoryboardStart

返回标识启动情节提要的一个关键帧。

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>返回值

指向基关键帧，它标识情节提要的开头的指针。

### <a name="remarks"></a>备注

获取此关键帧，以基于任何其他关键帧或转换情节提要启动时的时刻。

##  <a name="getuianimationmanager"></a>  CAnimationController::GetUIAnimationManager

提供对封装 IUIAnimationManager 对象的访问。

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>返回值

一个指向 IUIAnimationManager 接口或如果动画管理器创建失败，则为 NULL。

### <a name="remarks"></a>备注

如果当前操作系统不支持 Windows 动画 API，此方法返回 NULL，并且此后 CAnimationController::IsValid 上的所有后续调用将返回 FALSE。 您可能需要访问 IUIAnimationManager，才能调用不使用动画控制器的包装及其接口方法。

##  <a name="getuianimationtimer"></a>  CAnimationController::GetUIAnimationTimer

提供对封装 IUIAnimationTimer 对象的访问。

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>返回值

一个指向 IUIAnimationTimer 接口或如果动画计时器创建失败，则为 NULL。

### <a name="remarks"></a>备注

如果当前操作系统不支持 Windows 动画 API，此方法返回 NULL，并且此后 CAnimationController::IsValid 上的所有后续调用将返回 FALSE。

##  <a name="getuitransitionfactory"></a>  CAnimationController::GetUITransitionFactory

一个指向 IUIAnimationTransitionFactory 接口或如果创建的转换库失败，则为 NULL。

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>返回值

指向 IUIAnimationTransitionFactory 或者如果转换工厂创建失败，则为 NULL 指针。

### <a name="remarks"></a>备注

如果当前操作系统不支持 Windows 动画 API，此方法返回 NULL，并且此后 CAnimationController::IsValid 上的所有后续调用将返回 FALSE。

##  <a name="getuitransitionlibrary"></a>  CAnimationController::GetUITransitionLibrary

提供对封装 IUIAnimationTransitionLibrary 对象的访问。

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>返回值

一个指向 IUIAnimationTransitionLibrary 接口或如果创建的转换库失败，则为 NULL。

### <a name="remarks"></a>备注

如果当前操作系统不支持 Windows 动画 API，此方法返回 NULL，并且此后 CAnimationController::IsValid 上的所有后续调用将返回 FALSE。

##  <a name="isanimationinprogress"></a>  CAnimationController::IsAnimationInProgress

指示至少一个组是否正在播放动画。

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>返回值

如果没有为此动画控制器; 进行动画，则返回 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

检查动画管理器的状态，如果状态为 UI_ANIMATION_MANAGER_BUSY 则返回 TRUE。

##  <a name="isvalid"></a>  CAnimationController::IsValid

指示动画控制器是否有效。

```
BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果动画控制器有效，则为 TRUE否则为 FALSE。

### <a name="remarks"></a>备注

此方法返回 FALSE，仅当 Windows 动画 API 不支持的当前 OS 和动画管理器创建失败，因为它未注册。 你需要初始化 COM 库来设置此标志后至少一次调用 GetUIAnimationManager。

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

存储指向动画管理器 COM 对象的指针。

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

##  <a name="m_panimationtimer"></a>  CAnimationController::m_pAnimationTimer

存储指向动画计时器 COM 对象的指针。

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

##  <a name="m_prelatedwnd"></a>  CAnimationController::m_pRelatedWnd

指向相关的 CWnd 对象，可以将自动重绘动画管理器的状态已更改，或后更新事件发生时的指针。 可以为 NULL。

```
CWnd* m_pRelatedWnd;
```

##  <a name="m_ptransitionfactory"></a>  CAnimationController::m_pTransitionFactory

存储指向转换工厂 COM 对象的指针。

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

##  <a name="m_ptransitionlibrary"></a>  CAnimationController::m_pTransitionLibrary

存储指向转换库 COM 对象的指针。

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

##  <a name="onafterschedule"></a>  CAnimationController::OnAfterSchedule

当动画，以指定组只是已计划时，由框架调用。

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>参数

*pGroup*<br/>
已计划将动画组到指针。

### <a name="remarks"></a>备注

默认实现从指定组中删除关键帧，并从属于指定组的动画变量过渡。 在派生类才能根据动画安排任何其他操作，可以重写。

##  <a name="onanimationintegervaluechanged"></a>  CAnimationController::OnAnimationIntegerValueChanged

动画变量的整数值发生更改时由框架调用。

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>参数

*pGroup*<br/>
已更改的指针指向包含其值的动画对象的动画组。

*pObject*<br/>
指向一个动画对象，包含其值已更改的动画变量的指针。

*变量*<br/>
指向一个动画变量的指针。

*newValue*<br/>
指定新值。

*prevValue*<br/>
指定以前的值。

### <a name="remarks"></a>备注

如果使用为特定的动画变量或动画对象调用 EnableIntegerValueChangedEvent 启用动画变量事件，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

##  <a name="onanimationmanagerstatuschanged"></a>  CAnimationController::OnAnimationManagerStatusChanged

由框架调用以响应 StatusChanged 事件从动画管理器。

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>参数

*newStatus*<br/>
新动画管理器状态。

*previousStatus*<br/>
上一个动画管理器状态。

### <a name="remarks"></a>备注

如果启用与 EnableAnimationManagerEvent 动画管理器事件，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 如果设置 SetRelatedWnd 的默认实现将更新相关的窗口。

##  <a name="onanimationtimerpostupdate"></a>  CAnimationController::OnAnimationTimerPostUpdate

动画更新完成后，由框架调用。

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>备注

如果您启用使用 EnableAnimationTimerEventHandler 计时器事件处理程序，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

##  <a name="onanimationtimerpreupdate"></a>  CAnimationController::OnAnimationTimerPreUpdate

在动画更新开始之前，由框架调用。

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>备注

如果您启用使用 EnableAnimationTimerEventHandler 计时器事件处理程序，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

##  <a name="onanimationtimerrenderingtooslow"></a>  CAnimationController::OnAnimationTimerRenderingTooSlow

当动画呈现帧速率低于最小的理想帧速率时由框架调用。

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>参数

*每秒帧数*<br/>
每秒帧数中的当前帧速率。

### <a name="remarks"></a>备注

如果您启用使用 EnableAnimationTimerEventHandler 计时器事件处理程序，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 通过调用 IUIAnimationTimer::SetFrameRateThreshold 指定最小的理想帧速率。

##  <a name="onanimationvaluechanged"></a>  CAnimationController::OnAnimationValueChanged

动画变量的值发生更改时由框架调用。

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>参数

*pGroup*<br/>
已更改的指针指向包含其值的动画对象的动画组。

*pObject*<br/>
指向一个动画对象，包含其值已更改的动画变量的指针。

*变量*<br/>
指向一个动画变量的指针。

*newValue*<br/>
指定新值。

*prevValue*<br/>
指定以前的值。

### <a name="remarks"></a>备注

如果使用为特定的动画变量或动画对象调用 EnableValueChangedEvent 启用动画变量事件，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

##  <a name="onbeforeanimationstart"></a>  CAnimationController::OnBeforeAnimationStart

之前由框架调用正确计划动画。

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>参数

*pGroup*<br/>
一个指向其动画即将开始的动画组。

### <a name="remarks"></a>备注

此调用将路由到相关 CWnd，并可以在执行任何其他操作之前在动画开始指定组的派生类中重写。

##  <a name="onhasprioritycancel"></a>  CAnimationController::OnHasPriorityCancel

由框架调用以便解决计划冲突。

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>参数

*pgroupscheduled 所*<br/>
拥有当前已计划的情节提要的组。

*pGroupNew*<br/>
拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。

*priorityEffect*<br/>
如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。

### <a name="return-value"></a>返回值

如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TURE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。

### <a name="remarks"></a>备注

如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_CANCEL，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关详细信息的阅读 Windows 动画 API 文档[冲突管理](https://msdn.microsoft.com/library/dd371759)。

##  <a name="onhasprioritycompress"></a>  CAnimationController::OnHasPriorityCompress

由框架调用以便解决计划冲突。

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>参数

*pgroupscheduled 所*<br/>
拥有当前已计划的情节提要的组。

*pGroupNew*<br/>
拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。

*priorityEffect*<br/>
如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。

### <a name="return-value"></a>返回值

如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TURE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。

### <a name="remarks"></a>备注

如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_COMPRESS，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关详细信息的阅读 Windows 动画 API 文档[冲突管理](https://msdn.microsoft.com/library/dd371759)。

##  <a name="onhaspriorityconclude"></a>  CAnimationController::OnHasPriorityConclude

由框架调用以便解决计划冲突。

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>参数

*pgroupscheduled 所*<br/>
拥有当前已计划的情节提要的组。

*pGroupNew*<br/>
拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。

*priorityEffect*<br/>
如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。

### <a name="return-value"></a>返回值

如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TURE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。

### <a name="remarks"></a>备注

如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_CONCLUDE，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关详细信息的阅读 Windows 动画 API 文档[冲突管理](https://msdn.microsoft.com/library/dd371759)。

##  <a name="onhasprioritytrim"></a>  CAnimationController::OnHasPriorityTrim

由框架调用以便解决计划冲突。

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>参数

*pgroupscheduled 所*<br/>
拥有当前已计划的情节提要的组。

*pGroupNew*<br/>
拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。

*priorityEffect*<br/>
如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。

### <a name="return-value"></a>返回值

如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TURE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。

### <a name="remarks"></a>备注

如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_TRIM，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关详细信息的阅读 Windows 动画 API 文档[冲突管理](https://msdn.microsoft.com/library/dd371759)。

##  <a name="onstoryboardstatuschanged"></a>  CAnimationController::OnStoryboardStatusChanged

情节提要状态发生更改时由框架调用。

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>参数

*pGroup*<br/>
已更改的动画组拥有其状态的情节提要的指针。

*newStatus*<br/>
指定新状态。

*previousStatus*<br/>
指定的以前的状态。

### <a name="remarks"></a>备注

如果您启用使用 CAnimationController::EnableStoryboardEventHandler 情节提要事件，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

##  <a name="onstoryboardupdated"></a>  CAnimationController::OnStoryboardUpdated

已更新情节提要时由框架调用。

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>参数

*pGroup*<br/>
一个指向拥有的情节提要的组。

### <a name="remarks"></a>备注

如果您启用使用 CAnimationController::EnableStoryboardEventHandler 情节提要事件，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

##  <a name="removeallanimationgroups"></a>  CAnimationController::RemoveAllAnimationGroups

从动画控制器中移除所有动画组。

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>备注

所有组将都被删除，其指针，如果存储在应用程序级别，必须都将失效。 如果要删除的组的 CAnimationGroup::m_bAutodestroyAnimationObjects 为 TRUE，则将删除属于该组的所有动画对象;否则为其对父动画控制器的引用将设置为 NULL，并将它们添加到另一个控制器。

##  <a name="removeanimationgroup"></a>  CAnimationController::RemoveAnimationGroup

从动画控制器中删除具有指定 ID 的动画组。

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定动画组 id。

### <a name="remarks"></a>备注

此方法从内部的组列表中删除动画组并将其删除，因此如果存储一个指向该动画组时，它必须使其无效。 如果 CAnimationGroup::m_bAutodestroyAnimationObjects 为 TRUE，则将删除属于该组的所有动画对象;否则为其对父动画控制器的引用将设置为 NULL，并将它们添加到另一个控制器。

##  <a name="removeanimationobject"></a>  CAnimationController::RemoveAnimationObject

从动画控制器中删除动画对象。

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>参数

*pObject*<br/>
指向动画对象的指针。

*bNoDelete*<br/>
如果此参数为 TRUE 时删除将不删除对象。

### <a name="remarks"></a>备注

从动画控制器和动画组中删除动画对象。 如果特定的对象应不进行动画处理，或如果你需要将对象移动到另一个动画控制器调用此函数。 在最后一个事例 bNoDelete 必须为 TRUE。

##  <a name="removetransitions"></a>  CAnimationController::RemoveTransitions

从属于指定组的动画对象中删除转换。

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定组 id。

### <a name="remarks"></a>备注

在组及其动画对象将循环，并针对每个动画对象调用 ClearTransitions(FALSE)。 已安排动画后，由框架调用此方法。

##  <a name="schedulegroup"></a>  CAnimationController::ScheduleGroup

计划动画。

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定动画要计划的组 ID。

*time*<br/>
指定计划的时间。

### <a name="return-value"></a>返回值

如果已成功计划了动画，则为 TRUE。 如果尚未创建情节提要，或发生其他错误，则为 FALSE。

### <a name="remarks"></a>备注

必须使用设置为 FALSE 之前 ScheduleGroup 参数 bScheduleNow 调用 AnimateGroup。 您可以指定从 IUIAnimationTimer::GetTime 获取所需的动画时间。 如果时间参数为 0.0，动画的当前时间计划。

##  <a name="setrelatedwnd"></a>  CAnimationController::SetRelatedWnd

建立动画控制器和一个窗口之间的关系。

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向要设置的窗口对象的指针。

### <a name="remarks"></a>备注

如果设置相关的 CWnd 对象，动画控制器都可以以自动更新它 （发送 WM_PAINT 消息） 的动画管理器的状态已更改或计时器后更新事件发生时。

##  <a name="updateanimationmanager"></a>  CAnimationController::UpdateAnimationManager

指示动画管理器来更新所有的动画变量的值。

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>备注

调用此方法将推进到当前时间的动画管理器，根据需要更改情节提要的状态和更新到相应的任何动画变量内插的值。 此方法在内部调用 IUIAnimationTimer::GetTime(timeNow) 和 IUIAnimationManager::Update(timeNow)。 重写此方法在派生类来自定义此行为。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
