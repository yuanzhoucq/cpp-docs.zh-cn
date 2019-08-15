---
title: CAnimationController 类
ms.date: 03/27/2019
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
ms.openlocfilehash: 9039d44d9ef36a47c11b3ecaddf232ad427727c4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507641"
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
|[CAnimationController::CAnimationController](#canimationcontroller)|构造动画控制器。|
|[CAnimationController::~CAnimationController](#_dtorcanimationcontroller)|析构函数。 当动画控制器对象被销毁时调用。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAnimationController::AddAnimationObject](#addanimationobject)|向属于动画控制器的组添加动画对象。|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|将关键帧添加到组。|
|[CAnimationController::AnimateGroup](#animategroup)|准备组以运行动画并根据需要对其进行计划。|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|已重载。 在计划动画时, 由框架调用以清除组。|
|[CAnimationController::CreateKeyframe](#createkeyframe)|已重载。 创建取决于过渡的关键帧并将其添加到指定的组。|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|设置或释放在动画管理器状态更改时要调用的处理程序。|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|设置或释放计时事件的处理程序和计时更新处理程序。|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|设置或释放要调用的优先级比较处理程序, 以确定是否可以取消、结束、修整或压缩计划的情节提要。|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|设置或释放情节提要状态和更新事件的处理程序。|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|已重载。 按动画组的情节提要查找动画组。|
|[CAnimationController::FindAnimationObject](#findanimationobject)|查找包含指定动画变量的动画对象。|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|返回标识情节提要开头的关键帧。|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|提供对封装的 IUIAnimationManager 对象的访问。|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|提供对封装的 IUIAnimationTimer 对象的访问。|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|指向 IUIAnimationTransitionFactory 接口的指针; 如果创建转换库失败, 则为 NULL。|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|提供对封装的 IUIAnimationTransitionLibrary 对象的访问。|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|指示是否至少有一个组正在播放动画。|
|[CAnimationController::IsValid](#isvalid)|指示动画控制器是否有效。|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|当动画变量的整数值已更改时由框架调用。|
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|由框架调用, 以响应动画管理器中的 StatusChanged 事件。|
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|动画更新完成后, 由框架调用。|
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|在动画更新开始之前由框架调用。|
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|当动画的呈现帧速率低于最小理想帧速率时由框架调用。|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|当动画变量的值已更改时由框架调用。|
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|在计划动画之前由框架调用。|
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|由框架调用以便解决计划冲突。|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|由框架调用以便解决计划冲突。|
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|由框架调用以便解决计划冲突。|
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|由框架调用以便解决计划冲突。|
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|当情节提要状态发生更改时由框架调用。|
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|当情节提要已更新时由框架调用。|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|从动画控制器中移除所有动画组。|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|从动画控制器中删除具有指定 ID 的动画组。|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|从动画控制器中删除动画对象。|
|[CAnimationController::RemoveTransitions](#removetransitions)|从属于指定组的动画对象中移除转换。|
|[CAnimationController::ScheduleGroup](#schedulegroup)|计划动画。|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|在动画控制器和窗口之间建立关系。|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|指示动画管理器更新所有动画变量的值。|

### <a name="protected-methods"></a>受保护的方法

|名称|描述|
|----------|-----------------|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|已重载。 清理组的帮助器。|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|当刚计划指定组的动画时, 由框架调用。|

### <a name="protected-data-members"></a>受保护的数据成员

|name|描述|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|表示情节提要开头的关键帧。|
|[CAnimationController::m_bIsValid](#m_bisvalid)|指定动画控制器是否有效。 如果当前操作系统不支持 Windows 动画 API, 则将此成员设置为 FALSE。|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|属于此动画控制器的动画组的列表。|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|存储指向动画管理器 COM 对象的指针。|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|存储指向动画计时器 COM 对象的指针。|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|指向相关 CWnd 对象的指针, 该对象可以在动画管理器的状态发生更改时自动重新绘制, 或发生更新后事件。 可以为 NULL。|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|存储指向过渡工厂 COM 对象的指针。|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|存储指向转换库 COM 对象的指针。|

## <a name="remarks"></a>备注

CAnimationController 类是用于管理动画的键类。 可以在应用程序中创建一个或多个动画控制器实例, 还可以选择使用 CAnimationController:: SetRelatedWnd 将动画控制器的实例连接到 CWnd 对象。 若要在动画管理器状态发生更改或更新动画计时器时自动将 WM_PAINT 消息发送到相关窗口, 则需要此连接。 如果不启用此关系, 则必须重绘显示动画的窗口。 出于此目的, 可以从 CAnimationController 派生一个类, 并重写 OnAnimationManagerStatusChanged 和/或 OnAnimationTimerPostUpdate, 并在必要时使一个或多个窗口无效。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="_dtorcanimationcontroller"></a>CAnimationController:: ~ CAnimationController

析构函数。 当动画控制器对象被销毁时调用。

```
virtual ~CAnimationController(void);
```

##  <a name="addanimationobject"></a>CAnimationController:: AddAnimationObject

向属于动画控制器的组添加动画对象。

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>参数

*pObject*<br/>
指向动画对象的指针。

### <a name="return-value"></a>返回值

一个指针, 指向现有的或新的动画组 (如果函数成功, 则添加 pObject);如果已将 pObject 添加到属于另一个动画控制器的组, 则为 NULL。

### <a name="remarks"></a>备注

调用此方法可向动画控制器添加动画对象。 对象将根据对象的 GroupID 添加到组中 (请参见 CAnimationBaseObject:: SetID)。 如果动态控制器是使用指定的 GroupID 添加的第一个对象, 则它将创建一个新组。 只能向一个动画控制器添加动画对象。 如果需要将对象添加到另一个控制器, 请先调用 RemoveAnimationObject。 如果对已添加到组的对象调用 SetID, 则会从旧组中删除该对象, 并将该对象添加到具有指定 ID 的其他组。

##  <a name="addkeyframetogroup"></a>CAnimationController:: AddKeyframeToGroup

将关键帧添加到组。

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定组 ID。

*pKeyframe*<br/>
指向关键帧的指针。

### <a name="return-value"></a>返回值

如果函数成功, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

通常不需要调用此方法, 而应使用 CAnimationController:: CreateKeyframe 来自动创建创建的关键帧并将其添加到组。

##  <a name="animategroup"></a>CAnimationController:: AnimateGroup

准备组以运行动画并根据需要对其进行计划。

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定 GroupID。

*bScheduleNow*<br/>
指定是否立即运行动画。

### <a name="return-value"></a>返回值

如果动画已成功计划并运行, 则为 TRUE。

### <a name="remarks"></a>备注

此方法执行实际工作创建情节提要、添加动画变量、应用过渡和设置关键帧。 如果将 bScheduleNow 设置为 FALSE, 则可能会延迟计划。 在这种情况下, 指定的组将包含已为动画设置的情节提要。 此时, 可以设置情节提要和动画变量的事件。 当你实际需要运行动画时, 请调用 CAnimationController:: ScheduleGroup。

##  <a name="canimationcontroller"></a>CAnimationController:: CAnimationController

构造动画控制器。

```
CAnimationController(void);
```

##  <a name="cleanupgroup"></a>CAnimationController:: CleanUpGroup

在计划动画时, 由框架调用以清除组。

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定 GroupID。

*pGroup*<br/>
指向要清理的动画组的指针。

### <a name="remarks"></a>备注

此方法从指定的组中删除所有转换和关键帧, 因为它们在计划动画后不相关。

##  <a name="createkeyframe"></a>CAnimationController:: CreateKeyframe

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

设置或释放在动画管理器状态更改时要调用的处理程序。

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
指定是设置还是释放处理程序。

### <a name="return-value"></a>返回值

如果已成功设置或释放处理程序, 则为 TRUE。

### <a name="remarks"></a>备注

设置 (启用) 处理程序时, 当动画管理器的状态发生更改时, Windows 动画将调用 OnAnimationManagerStatusChanged。

##  <a name="enableanimationtimereventhandler"></a>CAnimationController:: EnableAnimationTimerEventHandler

设置或释放计时事件的处理程序和计时更新处理程序。

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>参数

*bEnable*<br/>
指定是设置还是释放处理程序。

*idleBehavior*<br/>
指定计时器更新处理程序的空闲行为。

### <a name="return-value"></a>返回值

如果成功设置或释放了处理程序, 则为 TRUE;如果再次调用此方法而不先释放处理程序, 则为 FALSE; 如果发生其他错误, 则为 FALSE。

### <a name="remarks"></a>备注

设置 (启用) 处理程序时, Windows 动画 API 调用 OnAnimationTimerPreUpdate、OnAnimationTimerPostUpdate、OnRenderingTooSlow 方法。 需要启用动画计时器以允许 Windows 动画 API 更新情节提要。 否则, 你将需要调用 CAnimationController:: UpdateAnimationManager 以指示动画管理器更新所有动画变量的值。

##  <a name="enableprioritycomparisonhandler"></a>  CAnimationController::EnablePriorityComparisonHandler

设置或释放要调用的优先级比较处理程序, 以确定是否可以取消、结束、修整或压缩计划的情节提要。

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>参数

*dwHandlerType*<br/>
UI_ANIMATION_PHT_ 标志的组合 (请参见 "备注"), 它指定要设置或释放的处理程序。

### <a name="return-value"></a>返回值

如果已成功设置或释放处理程序, 则为 TRUE。

### <a name="remarks"></a>备注

设置 (启用) 处理程序时, Windows 动画会调用以下虚拟方法, 具体取决于 dwHandlerType:OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler 可以是以下标志的组合:UI_ANIMATION_PHT_NONE-发布所有处理程序 UI_ANIMATION_PHT_CANCEL-set Cancel 比较处理程序 UI_ANIMATION_PHT_CONCLUDE-set 结束比较处理程序 UI_ANIMATION_PHT_COMPRESS-set 压缩比较处理程序 UI_ANIMATION_PHT_TRIM-setTrim 比较处理程序 UI_ANIMATION_PHT_CANCEL_REMOVE-remove Cancel 比较处理程序 UI_ANIMATION_PHT_CONCLUDE_REMOVE-remove 结束比较处理程序 UI_ANIMATION_PHT_COMPRESS_REMOVE-remove 压缩比较处理程序 UI_ANIMATION_PHT_TRIM_REMOVE-删除剪裁比较处理程序

##  <a name="enablestoryboardeventhandler"></a>CAnimationController:: EnableStoryboardEventHandler

设置或释放情节提要状态和更新事件的处理程序。

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定组 ID。

*bEnable*<br/>
指定是设置还是释放处理程序。

### <a name="return-value"></a>返回值

如果已成功设置或释放处理程序, 则为 TRUE;如果现在找到指定的动画组, 或尚未启动指定组的动画, 其内部情节提要为 NULL, 则为 FALSE。

### <a name="remarks"></a>备注

设置 (启用) 处理程序时, Windows 动画 API 调用 OnStoryboardStatusChanges 和 OnStoryboardUpdated 虚方法。 为指定动画组调用了 CAnimationController:: 动画后, 必须设置该处理程序, 因为它会创建封装的 IUIAnimationStoryboard 对象。

##  <a name="findanimationgroup"></a>CAnimationController:: FindAnimationGroup

按组 ID 查找动画组。

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

指向动画组的指针; 如果找不到具有指定 ID 的组, 则为 NULL。

### <a name="remarks"></a>备注

使用此方法可在运行时查找动画组。 当具有特定 GroupID 的第一个动画对象添加到动画控制器时, 将创建一个组并将该对象添加到动画组的内部列表中。

##  <a name="findanimationobject"></a>CAnimationController:: FindAnimationObject

查找包含指定动画变量的动画对象。

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
输出. 包含指向动画对象或 NULL 的指针。

*ppGroup*<br/>
输出. 包含一个指向包含动画对象的动画组的指针, 或为 NULL。

### <a name="return-value"></a>返回值

如果找到对象, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

当需要从传入动画变量中查找动画对象时, 从事件处理程序调用。

##  <a name="g_keyframestoryboardstart"></a>CAnimationController:: gkeyframeStoryboardStart

表示情节提要开头的关键帧。

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

##  <a name="getkeyframestoryboardstart"></a>CAnimationController:: GetKeyframeStoryboardStart

返回标识情节提要开头的关键帧。

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>返回值

指向基本关键帧的指针, 它标识情节提要的开头。

### <a name="remarks"></a>备注

获取此关键帧以使情节提要开始时的任何其他关键帧或转换成为基础。

##  <a name="getuianimationmanager"></a>CAnimationController:: GetUIAnimationManager

提供对封装的 IUIAnimationManager 对象的访问。

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>返回值

指向 IUIAnimationManager 接口的指针; 如果创建动画管理器失败, 则为 NULL。

### <a name="remarks"></a>备注

如果当前操作系统不支持 Windows 动画 API, 则此方法返回 NULL, 并在 CAnimationController:: IsValid 上的所有后续调用返回 FALSE 后返回 FALSE。 你可能需要访问 IUIAnimationManager 以调用其不是由动画控制器包装的接口方法。

##  <a name="getuianimationtimer"></a>CAnimationController:: GetUIAnimationTimer

提供对封装的 IUIAnimationTimer 对象的访问。

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>返回值

指向 IUIAnimationTimer 接口的指针; 如果创建动画计时器失败, 则为 NULL。

### <a name="remarks"></a>备注

如果当前操作系统不支持 Windows 动画 API, 则此方法返回 NULL, 并在 CAnimationController:: IsValid 上的所有后续调用返回 FALSE 后返回 FALSE。

##  <a name="getuitransitionfactory"></a>CAnimationController:: GetUITransitionFactory

指向 IUIAnimationTransitionFactory 接口的指针; 如果创建转换库失败, 则为 NULL。

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>返回值

如果创建转换工厂失败, 则为指向 IUIAnimationTransitionFactory 的指针或 NULL。

### <a name="remarks"></a>备注

如果当前操作系统不支持 Windows 动画 API, 则此方法返回 NULL, 并在 CAnimationController:: IsValid 上的所有后续调用返回 FALSE 后返回 FALSE。

##  <a name="getuitransitionlibrary"></a>CAnimationController:: GetUITransitionLibrary

提供对封装的 IUIAnimationTransitionLibrary 对象的访问。

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>返回值

指向 IUIAnimationTransitionLibrary 接口的指针; 如果创建转换库失败, 则为 NULL。

### <a name="remarks"></a>备注

如果当前操作系统不支持 Windows 动画 API, 则此方法返回 NULL, 并在 CAnimationController:: IsValid 上的所有后续调用返回 FALSE 后返回 FALSE。

##  <a name="isanimationinprogress"></a>CAnimationController:: IsAnimationInProgress

指示是否至少有一个组正在播放动画。

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>返回值

如果此动画控制器正在进行动画处理, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

检查动画管理器的状态, 如果状态为 UI_ANIMATION_MANAGER_BUSY, 则返回 TRUE。

##  <a name="isvalid"></a>CAnimationController:: IsValid

指示动画控制器是否有效。

```
BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果动画控制器有效, 则为 TRUE;否则为 FALSE。

### <a name="remarks"></a>备注

仅当当前操作系统上不支持 Windows 动画 API 并创建动画管理器失败 (因为未注册) 时, 此方法才返回 FALSE。 需要在初始化 COM 库后至少调用一次 GetUIAnimationManager, 以导致设置此标志。

##  <a name="m_bisvalid"></a>  CAnimationController::m_bIsValid

指定动画控制器是否有效。 如果当前操作系统不支持 Windows 动画 API, 则将此成员设置为 FALSE。

```
BOOL m_bIsValid;
```

##  <a name="m_lstanimationgroups"></a>CAnimationController:: m_lstAnimationGroups

属于此动画控制器的动画组的列表。

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

##  <a name="m_panimationmanager"></a>  CAnimationController::m_pAnimationManager

存储指向动画管理器 COM 对象的指针。

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

##  <a name="m_panimationtimer"></a>CAnimationController:: m_pAnimationTimer

存储指向动画计时器 COM 对象的指针。

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

##  <a name="m_prelatedwnd"></a>CAnimationController:: m_pRelatedWnd

指向相关 CWnd 对象的指针, 该对象可以在动画管理器的状态发生更改时自动重新绘制, 或发生更新后事件。 可以为 NULL。

```
CWnd* m_pRelatedWnd;
```

##  <a name="m_ptransitionfactory"></a>  CAnimationController::m_pTransitionFactory

存储指向过渡工厂 COM 对象的指针。

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

##  <a name="m_ptransitionlibrary"></a>CAnimationController:: m_pTransitionLibrary

存储指向转换库 COM 对象的指针。

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

##  <a name="onafterschedule"></a>CAnimationController:: OnAfterSchedule

当刚计划指定组的动画时, 由框架调用。

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>参数

*pGroup*<br/>
指向已计划的动画组的指针。

### <a name="remarks"></a>备注

默认实现从指定的组中删除关键帧, 并从属于指定组的动画变量转换。 可以在派生类中重写, 以便在动画计划时执行任何其他操作。

##  <a name="onanimationintegervaluechanged"></a>CAnimationController:: OnAnimationIntegerValueChanged

当动画变量的整数值已更改时由框架调用。

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
一个指针, 指向包含其值已更改的动画对象的动画组。

*pObject*<br/>
一个指向动画对象的指针, 该对象包含其值已更改的动画变量。

*variable*<br/>
指向动画变量的指针。

*newValue*<br/>
指定新值。

*prevValue*<br/>
指定上一个值。

### <a name="remarks"></a>备注

如果为特定动画变量或动画对象启用了 EnableIntegerValueChangedEvent 调用的动画变量事件, 则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

##  <a name="onanimationmanagerstatuschanged"></a>CAnimationController:: OnAnimationManagerStatusChanged

由框架调用, 以响应动画管理器中的 StatusChanged 事件。

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>参数

*newStatus*<br/>
新的动画管理器状态。

*previousStatus*<br/>
先前的动画管理器状态。

### <a name="remarks"></a>备注

如果使用 EnableAnimationManagerEvent 启用动画管理器事件, 则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 如果已使用 SetRelatedWnd 设置了相关窗口, 则默认实现将更新该窗口。

##  <a name="onanimationtimerpostupdate"></a>CAnimationController:: OnAnimationTimerPostUpdate

动画更新完成后, 由框架调用。

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>备注

如果使用 EnableAnimationTimerEventHandler 启用计时器事件处理程序, 则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

##  <a name="onanimationtimerpreupdate"></a>CAnimationController:: OnAnimationTimerPreUpdate

在动画更新开始之前由框架调用。

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>备注

如果使用 EnableAnimationTimerEventHandler 启用计时器事件处理程序, 则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

##  <a name="onanimationtimerrenderingtooslow"></a>CAnimationController:: OnAnimationTimerRenderingTooSlow

当动画的呈现帧速率低于最小理想帧速率时由框架调用。

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>参数

*fps*<br/>
当前帧速率 (以帧/秒为单位)。

### <a name="remarks"></a>备注

如果使用 EnableAnimationTimerEventHandler 启用计时器事件处理程序, 则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 需要的最小帧速率是通过调用 IUIAnimationTimer:: SetFrameRateThreshold 来指定的。

##  <a name="onanimationvaluechanged"></a>CAnimationController:: OnAnimationValueChanged

当动画变量的值已更改时由框架调用。

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
一个指针, 指向包含其值已更改的动画对象的动画组。

*pObject*<br/>
一个指向动画对象的指针, 该对象包含其值已更改的动画变量。

*variable*<br/>
指向动画变量的指针。

*newValue*<br/>
指定新值。

*prevValue*<br/>
指定上一个值。

### <a name="remarks"></a>备注

如果为特定动画变量或动画对象启用了 EnableValueChangedEvent 调用的动画变量事件, 则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

##  <a name="onbeforeanimationstart"></a>CAnimationController:: OnBeforeAnimationStart

在计划动画之前由框架调用。

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>参数

*pGroup*<br/>
指向动画要开始的动画组的指针。

### <a name="remarks"></a>备注

此调用路由到相关 CWnd, 可在派生类中重写, 以便在为指定组启动动画之前执行任何其他操作。

##  <a name="onhasprioritycancel"></a>CAnimationController:: OnHasPriorityCancel

由框架调用以便解决计划冲突。

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>参数

*pGroupScheduled*<br/>
拥有当前已计划的情节提要的组。

*pGroupNew*<br/>
拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。

*priorityEffect*<br/>
如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。

### <a name="return-value"></a>返回值

如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TRUE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。

### <a name="remarks"></a>备注

如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_CANCEL，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关[冲突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的详细信息, 请参阅 WINDOWS 动画 API 文档。

##  <a name="onhasprioritycompress"></a>CAnimationController:: OnHasPriorityCompress

由框架调用以便解决计划冲突。

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>参数

*pGroupScheduled*<br/>
拥有当前已计划的情节提要的组。

*pGroupNew*<br/>
拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。

*priorityEffect*<br/>
如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。

### <a name="return-value"></a>返回值

如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TRUE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。

### <a name="remarks"></a>备注

如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_COMPRESS，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关[冲突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的详细信息, 请参阅 WINDOWS 动画 API 文档。

##  <a name="onhaspriorityconclude"></a>CAnimationController:: OnHasPriorityConclude

由框架调用以便解决计划冲突。

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>参数

*pGroupScheduled*<br/>
拥有当前已计划的情节提要的组。

*pGroupNew*<br/>
拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。

*priorityEffect*<br/>
如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。

### <a name="return-value"></a>返回值

如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TRUE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。

### <a name="remarks"></a>备注

如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_CONCLUDE，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关[冲突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的详细信息, 请参阅 WINDOWS 动画 API 文档。

##  <a name="onhasprioritytrim"></a>CAnimationController:: OnHasPriorityTrim

由框架调用以便解决计划冲突。

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>参数

*pGroupScheduled*<br/>
拥有当前已计划的情节提要的组。

*pGroupNew*<br/>
拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。

*priorityEffect*<br/>
如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。

### <a name="return-value"></a>返回值

如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TRUE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。

### <a name="remarks"></a>备注

如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_TRIM，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关[冲突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的详细信息, 请参阅 WINDOWS 动画 API 文档。

##  <a name="onstoryboardstatuschanged"></a>CAnimationController:: OnStoryboardStatusChanged

当情节提要状态发生更改时由框架调用。

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>参数

*pGroup*<br/>
一个指针, 它指向拥有其状态已更改的情节提要的动画组。

*newStatus*<br/>
指定新状态。

*previousStatus*<br/>
指定以前的状态。

### <a name="remarks"></a>备注

如果使用 CAnimationController:: EnableStoryboardEventHandler 启用情节提要事件, 则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

##  <a name="onstoryboardupdated"></a>CAnimationController:: OnStoryboardUpdated

当情节提要已更新时由框架调用。

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>参数

*pGroup*<br/>
指向拥有情节提要的组的指针。

### <a name="remarks"></a>备注

如果使用 CAnimationController:: EnableStoryboardEventHandler 启用情节提要事件, 则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

##  <a name="removeallanimationgroups"></a>  CAnimationController::RemoveAllAnimationGroups

从动画控制器中移除所有动画组。

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>备注

将删除所有组, 其指针 (如果存储在应用程序级别) 必须失效。 如果要删除的组的 CAnimationGroup:: m_bAutodestroyAnimationObjects 为 TRUE, 则将删除属于该组的所有动画对象;否则, 对父动画控制器的引用将设置为 NULL, 并且可以将其添加到另一个控制器。

##  <a name="removeanimationgroup"></a>  CAnimationController::RemoveAnimationGroup

从动画控制器中删除具有指定 ID 的动画组。

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定动画组 ID。

### <a name="remarks"></a>备注

此方法从组的内部列表中删除动画组并将其删除, 因此, 如果您存储了指向该动画组的指针, 则该动画组必须失效。 如果 CAnimationGroup:: m_bAutodestroyAnimationObjects 为 TRUE, 则将删除属于该组的所有动画对象;否则, 对父动画控制器的引用将设置为 NULL, 并且可以将其添加到另一个控制器。

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
如果此参数为 TRUE, 则删除时不会删除对象。

### <a name="remarks"></a>备注

从动画控制器和动画组中移除动画对象。 如果特定对象不应进行动画处理, 或者需要将对象移动到另一个动画控制器, 请调用此函数。 在最后一种情况下, bNoDelete 必须为 TRUE。

##  <a name="removetransitions"></a>CAnimationController:: RemoveTransitions

从属于指定组的动画对象中移除转换。

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定组 ID。

### <a name="remarks"></a>备注

该组循环切换其动画对象, 并对每个动画对象调用 ClearTransitions (FALSE)。 此方法由框架在计划动画后调用。

##  <a name="schedulegroup"></a>CAnimationController:: ScheduleGroup

计划动画。

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>参数

*nGroupID*<br/>
指定要计划的动画组 ID。

*time*<br/>
指定计划的时间。

### <a name="return-value"></a>返回值

如果动画已成功计划, 则为 TRUE。 如果尚未创建情节提要或发生其他错误, 则为 FALSE。

### <a name="remarks"></a>备注

必须先调用 AnimateGroup, 并将 bScheduleNow 参数设置为 FALSE, 然后再 ScheduleGroup。 可以指定从 IUIAnimationTimer:: GetTime 获取的所需动画时间。 如果时间参数为 0.0, 则会将动画计划为当前时间。

##  <a name="setrelatedwnd"></a>CAnimationController:: SetRelatedWnd

在动画控制器和窗口之间建立关系。

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pWnd*<br/>
指向要设置的 window 对象的指针。

### <a name="remarks"></a>备注

如果设置了相关的 CWnd 对象, 动画控制器可以在动画管理器状态发生更改或计时器更新事件发生时自动对其进行更新 (发送 WM_PAINT 消息)。

##  <a name="updateanimationmanager"></a>CAnimationController:: UpdateAnimationManager

指示动画管理器更新所有动画变量的值。

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>备注

调用此方法会使动画管理器前进到当前时间, 并根据需要更改情节提要的状态, 并将所有动画变量更新为适当的内插值。 此方法在内部调用 IUIAnimationTimer:: GetTime (timeNow) 和 IUIAnimationManager:: Update (timeNow)。 在派生类中重写此方法以自定义此行为。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
