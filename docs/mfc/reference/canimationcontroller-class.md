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
ms.openlocfilehash: 34a02567bfeb76666cc38ccf05dcc285a1f658f5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369758"
---
# <a name="canimationcontroller-class"></a>CAnimationController 类

实现动画控制器，它为创建和管理动画提供了中央接口。

## <a name="syntax"></a>语法

```
class CAnimationController : public CObject;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[动画控制器：：动画控制器](#canimationcontroller)|构造动画控制器。|
|[动画控制器：：~动画控制器](#_dtorcanimationcontroller)|析构函数。 销毁动画控制器对象时调用。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[动画控制器：：添加动画对象](#addanimationobject)|将动画对象添加到属于动画控制器的组。|
|[动画控制器：：将关键帧添加到组](#addkeyframetogroup)|将关键帧添加到组。|
|[动画控制器：：动画组](#animategroup)|准备一个组来运行动画，并选择性地安排它。|
|[动画控制器：：清理组](#cleanupgroup)|已重载。 由框架调用，以在计划动画时清理组。|
|[CAnimationController::CreateKeyframe](#createkeyframe)|已重载。 创建取决于过渡的关键帧并将其添加到指定的组。|
|[动画控制器：：启用动画管理器事件](#enableanimationmanagerevent)|设置或释放在动画管理器状态更改时调用的处理程序。|
|[动画控制器：：启用动画计时器事件处理程序](#enableanimationtimereventhandler)|设置或释放计时事件处理程序和计时更新处理程序。|
|[动画控制器：：启用优先级比较处理程序](#enableprioritycomparisonhandler)|设置或释放要调用的优先级比较处理程序，以确定是否可以取消、完成、修剪或压缩计划情节提要。|
|[动画控制器：：启用故事板事件处理程序](#enablestoryboardeventhandler)|设置或释放情节提要状态和更新事件的处理程序。|
|[动画控制器：：查找动画组](#findanimationgroup)|已重载。 按情节提要查找动画组。|
|[动画控制器：：查找动画对象](#findanimationobject)|查找包含指定动画变量的动画对象。|
|[动画控制器：：获取关键帧故事板启动](#getkeyframestoryboardstart)|返回标识情节提要开头的关键帧。|
|[动画控制器：：获取动画管理器](#getuianimationmanager)|提供对封装的 IUI动画管理器对象的访问。|
|[动画控制器：：获取动画计时器](#getuianimationtimer)|提供对封装的 IUI动画定时对象的访问。|
|[动画控制器：：获取 UI 转换工厂](#getuitransitionfactory)|如果创建过渡库失败，则指向 IUIAnimation 转换工厂接口或 NULL 的指针。|
|[动画控制器：：获取 UI 转换库](#getuitransitionlibrary)|提供对封装的 IUI 动画转换库对象的访问。|
|[动画控制器：：动画在进行中](#isanimationinprogress)|告诉是否至少有一个组正在播放动画。|
|[动画控制器：：有效](#isvalid)|告诉动画控制器是否有效。|
|[动画控制器：：在动画中值已更改](#onanimationintegervaluechanged)|当动画变量的整数值发生更改时，由框架调用。|
|[动画控制器：：打开动画管理器状态已更改](#onanimationmanagerstatuschanged)|由框架调用以响应动画管理器中的状态更改事件。|
|[动画控制器：：打开动画计时器后更新](#onanimationtimerpostupdate)|动画更新完成后由框架调用。|
|[动画控制器：：打开动画计时器预更新](#onanimationtimerpreupdate)|在动画更新开始之前由框架调用。|
|[动画控制器：：动画计时器渲染速度慢](#onanimationtimerrenderingtooslow)|当动画的渲染帧速率低于所需的最小帧速率时，由框架调用。|
|[动画控制器：：打开动画值已更改](#onanimationvaluechanged)|当动画变量的值发生更改时，由框架调用。|
|[动画控制器：：在动画启动之前打开](#onbeforeanimationstart)|在计划动画之前由框架调用。|
|[动画控制器：：onHas优先取消](#onhasprioritycancel)|由框架调用以便解决计划冲突。|
|[动画控制器：：打开哈斯优先压缩](#onhasprioritycompress)|由框架调用以便解决计划冲突。|
|[动画控制器：：onHas优先结束](#onhaspriorityconclude)|由框架调用以便解决计划冲突。|
|[动画控制器：：onHas优先修剪](#onhasprioritytrim)|由框架调用以便解决计划冲突。|
|[动画控制器：：在故事板状态更改](#onstoryboardstatuschanged)|情节提要状态更改时由框架调用。|
|[动画控制器：：在故事板上更新](#onstoryboardupdated)|更新情节提要时由框架调用。|
|[动画控制器：：删除所有动画组](#removeallanimationgroups)|从动画控制器中删除所有动画组。|
|[动画控制器：：删除动画组](#removeanimationgroup)|从动画控制器中删除具有指定 ID 的动画组。|
|[动画控制器：：删除动画对象](#removeanimationobject)|从动画控制器中删除动画对象。|
|[动画控制器：：删除转换](#removetransitions)|从属于指定组的动画对象中删除过渡。|
|[动画控制器：：计划组](#schedulegroup)|计划动画。|
|[动画控制器：：设置相关](#setrelatedwnd)|在动画控制器和窗口之间建立关系。|
|[动画控制器：：更新动画管理器](#updateanimationmanager)|指示动画管理器更新所有动画变量的值。|

### <a name="protected-methods"></a>受保护的方法

|名称|说明|
|----------|-----------------|
|[动画控制器：：清理组](#cleanupgroup)|已重载。 清理组的帮助者。|
|[动画控制器：：在计划后](#onafterschedule)|当指定组的动画刚刚计划时，由框架调用。|

### <a name="protected-data-members"></a>受保护的数据成员

|名称|说明|
|----------|-----------------|
|[动画控制器：：关键帧故事板启动](#g_keyframestoryboardstart)|表示情节提要开头的关键帧。|
|[动画控制器：：m_bIsValid](#m_bisvalid)|指定动画控制器是否有效。 如果当前操作系统不支持 Windows 动画 API，则此成员设置为 FALSE。|
|[动画控制器：：m_lstAnimationGroups](#m_lstanimationgroups)|属于此动画控制器的动画组的列表。|
|[动画控制器：：m_pAnimationManager](#m_panimationmanager)|存储指向动画管理器 COM 对象的指针。|
|[动画控制器：：m_pAnimationTimer](#m_panimationtimer)|存储指向动画计时器 COM 对象的指针。|
|[动画控制器：：m_pRelatedWnd](#m_prelatedwnd)|指向相关 CWnd 对象的指针，可在动画管理器的状态更改或更新后事件发生时自动重绘。 可以为 NULL。|
|[动画控制器：：m_pTransitionFactory](#m_ptransitionfactory)|存储指向过渡工厂 COM 对象的指针。|
|[动画控制器：：m_pTransitionLibrary](#m_ptransitionlibrary)|存储指向过渡库 COM 对象的指针。|

## <a name="remarks"></a>备注

CAnimationController 类是管理动画的键类。 您可以在应用程序中创建一个或多个动画控制器实例，也可以使用 CAnimationController：：SetNdnd 将动画控制器的实例连接到 CWnd 对象。 当动画管理器状态发生更改或动画计时器更新时，需要此连接自动将WM_PAINT消息发送到相关窗口。 如果不启用此关系，则必须重新绘制手动显示动画的窗口。 为此，可以从 CAnimationController 派生一个类，并重写 OnAnimationManagerStatus 已更改和/或 OnAnimationTimerPostUpdate，并在必要时使一个或多个窗口无效。

## <a name="inheritance-hierarchy"></a>继承层次结构

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="canimationcontrollercanimationcontroller"></a><a name="_dtorcanimationcontroller"></a>动画控制器：：~动画控制器

析构函数。 销毁动画控制器对象时调用。

```
virtual ~CAnimationController(void);
```

## <a name="canimationcontrolleraddanimationobject"></a><a name="addanimationobject"></a>动画控制器：：添加动画对象

将动画对象添加到属于动画控制器的组。

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>参数

*pObject*<br/>
指向动画对象的指针。

### <a name="return-value"></a>返回值

指向现有或新动画组的指针，其中已添加 pObject（如果函数成功）;如果函数成功，则指向现有动画组或新动画组。如果 pObject 已添加到属于另一个动画控制器的组，则为 NULL。

### <a name="remarks"></a>备注

调用此方法以向动画控制器添加动画对象。 对象将根据对象的组 ID 添加到组（请参阅 CAnimationBaseObject：SetID）。 如果动画控制器是使用指定的 GroupID 添加的第一个对象，则该组将创建新组。 动画对象只能添加到一个动画控制器。 如果需要将对象添加到其他控制器，请先调用删除动画对象。 如果为已添加到组的对象调用 SetID，则该对象将从旧组中删除，并添加到具有指定 ID 的另一个组中。

## <a name="canimationcontrolleraddkeyframetogroup"></a><a name="addkeyframetogroup"></a>动画控制器：：将关键帧添加到组

将关键帧添加到组。

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>参数

*n集团ID*<br/>
指定组 ID。

*p键框*<br/>
指向关键帧的指针。

### <a name="return-value"></a>返回值

如果函数成功，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

通常不需要调用此方法，而是使用 CAnimationController：：createKeyframe，它会自动创建已创建的关键帧并将其添加到组中。

## <a name="canimationcontrolleranimategroup"></a><a name="animategroup"></a>动画控制器：：动画组

准备一个组来运行动画，并选择性地安排它。

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>参数

*n集团ID*<br/>
指定组 ID。

*b时间表现在*<br/>
指定是否直接运行动画。

### <a name="return-value"></a>返回值

如果动画已成功计划并运行，则为 TRUE。

### <a name="remarks"></a>备注

此方法执行创建情节提要、添加动画变量、应用过渡和设置关键帧的实际工作。 如果将 b-计划现在设置为 FALSE，则可以延迟计划。 在这种情况下，指定的组将保存已为动画设置的情节提要。 此时，您可以为情节提要和动画变量设置事件。 当您实际需要运行动画调用 CAnimation 控制器：：计划组。

## <a name="canimationcontrollercanimationcontroller"></a><a name="canimationcontroller"></a>动画控制器：：动画控制器

构造动画控制器。

```
CAnimationController(void);
```

## <a name="canimationcontrollercleanupgroup"></a><a name="cleanupgroup"></a>动画控制器：：清理组

由框架调用，以在计划动画时清理组。

```
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>参数

*n集团ID*<br/>
指定组 ID。

*p组*<br/>
要清理的动画组的指针。

### <a name="remarks"></a>备注

此方法从指定的组中删除所有过渡和关键帧，因为它们在计划动画后不相关。

## <a name="canimationcontrollercreatekeyframe"></a><a name="createkeyframe"></a>动画控制器：：创建关键帧

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

*n集团ID*<br/>
指定要为其创建关键帧的组 ID。

*p 转换*<br/>
指向过渡的指针。 关键帧将插入到此过渡后的情节提要。

*p键框*<br/>
指向此关键帧的基关键帧的指针。

*偏移量*<br/>
由 pKeyframe 指定的基关键帧的偏移量（以秒为单位）。

### <a name="return-value"></a>返回值

指向新创建的关键帧（如果函数成功）的指针。

### <a name="remarks"></a>备注

可以存储返回的指针，也可以在新创建的关键帧的基础上创建其他关键帧（请参阅第二个重载）。 可以在关键帧处开始过渡 - 请参阅 CBaseTransition::SetKeyframes。 不需要删除以这种方式创建的关键帧，因为动画组会自动删除它们。 基于其他关键帧和过渡创建关键帧时请小心，避免循环引用。

## <a name="canimationcontrollerenableanimationmanagerevent"></a><a name="enableanimationmanagerevent"></a>动画控制器：：启用动画管理器事件

设置或释放在动画管理器状态更改时调用的处理程序。

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
指定是设置还是释放处理程序。

### <a name="return-value"></a>返回值

如果处理程序已成功设置或释放，则为 TRUE。

### <a name="remarks"></a>备注

设置（启用）处理程序时，Windows 动画在动画管理器的状态更改时调用 OnAnimationManager 状态更改。

## <a name="canimationcontrollerenableanimationtimereventhandler"></a><a name="enableanimationtimereventhandler"></a>动画控制器：：启用动画计时器事件处理程序

设置或释放计时事件处理程序和计时更新处理程序。

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>参数

*b 启用*<br/>
指定是设置还是释放处理程序。

*空闲行为*<br/>
为计时器更新处理程序指定空闲行为。

### <a name="return-value"></a>返回值

如果已成功设置或释放处理程序，则为 TRUE;如果操作器已成功设置或释放，则为 TRUE。如果在不首先释放处理程序的情况下第二次调用此方法，或者发生任何其他错误，则 FALSE。

### <a name="remarks"></a>备注

当处理程序设置（启用）Windows 动画 API 调用上动画计时器预更新、上动画计时器更新、"渲染太慢"方法。 您需要启用动画计时器以允许 Windows 动画 API 更新情节提要。 否则，您需要调用 CAnimationController：：更新动画管理器，以便指示动画管理器更新所有动画变量的值。

## <a name="canimationcontrollerenableprioritycomparisonhandler"></a><a name="enableprioritycomparisonhandler"></a>动画控制器：：启用优先级比较处理程序

设置或释放要调用的优先级比较处理程序，以确定是否可以取消、完成、修剪或压缩计划情节提要。

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>参数

*德汉德勒型*<br/>
UI_ANIMATION_PHT_标志（请参阅备注）的组合，它指定要设置或释放的处理程序。

### <a name="return-value"></a>返回值

如果处理程序已成功设置或释放，则为 TRUE。

### <a name="remarks"></a>备注

设置（启用）处理程序时，Windows 动画会根据 dwHandlerType 调用以下虚拟方法：OnHas优先取消、OnHas优先结束、OnHas优先修剪、OnHas优先压缩。 dwHandler 可以是以下标志的组合： UI_ANIMATION_PHT_NONE - 释放UI_ANIMATION_PHT_CANCEL - 设置取消比较处理程序UI_ANIMATION_PHT_CONCLUDE - 设置"结束比较处理程序UI_ANIMATION_PHT_COMPRESS - 设置压缩比较处理程序 UI_ANIMATION_PHT_TRIM - 设置修剪比较处理程序UI_ANIMATION_PHT_CANCEL_REMOVE - 删除取消比较处理程序UI_ANIMATION_PHT_CONCLUDE_REMOVE - 删除UI_ANIMATION_PHT_COMPRESS_REMOVE结束比较处理程序 - 删除压缩比较处理程序UI_ANIMATION_PHT_TRIM_REMOVE -删除修剪比较处理程序

## <a name="canimationcontrollerenablestoryboardeventhandler"></a><a name="enablestoryboardeventhandler"></a>动画控制器：：启用故事板事件处理程序

设置或释放情节提要状态和更新事件的处理程序。

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>参数

*n集团ID*<br/>
指定组 ID。

*b 启用*<br/>
指定是设置还是释放处理程序。

### <a name="return-value"></a>返回值

如果处理程序已成功设置或释放，则为 TRUE;如果处理程序已成功设置或释放该处理程序，则为 TRUE。如果现在找到指定的动画组，或者尚未启动指定组的动画，并且其内部情节提要为 NULL，则 FALSE。

### <a name="remarks"></a>备注

设置（启用）处理程序时，Windows 动画 API 将调用 OnStoryboard 状态更改和 OnStoryboard 更新的虚拟方法。 处理程序必须在 CAnimationController：：Animate 为指定的动画组调用，因为它创建封装的 IUIAnimateStoryboard 对象。

## <a name="canimationcontrollerfindanimationgroup"></a><a name="findanimationgroup"></a>动画控制器：：查找动画组

按组 ID 查找动画组。

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>参数

*n集团ID*<br/>
指定组 ID。

*板*<br/>
指向情节提要的指针。

### <a name="return-value"></a>返回值

如果找不到具有指定 ID 的组，则指向动画组或 NULL 的指针。

### <a name="remarks"></a>备注

使用此方法在运行时查找动画组。 将具有特定 GroupID 的第一个动画对象添加到动画控制器时，将创建组并将其添加到动画组的内部列表中。

## <a name="canimationcontrollerfindanimationobject"></a><a name="findanimationobject"></a>动画控制器：：查找动画对象

查找包含指定动画变量的动画对象。

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>参数

*pvariable*<br/>
指向动画变量的指针。

*ppObject*<br/>
输出。 包含指向动画对象或 NULL 的指针。

*ppGroup*<br/>
输出。 包含指向保存动画对象的动画组的指针，或 NULL。

### <a name="return-value"></a>返回值

如果找到对象，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

从事件处理程序调用，当它需要从传入动画变量查找动画对象时。

## <a name="canimationcontrollergkeyframestoryboardstart"></a><a name="g_keyframestoryboardstart"></a>动画控制器：：关键帧故事板启动

表示情节提要开头的关键帧。

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

## <a name="canimationcontrollergetkeyframestoryboardstart"></a><a name="getkeyframestoryboardstart"></a>动画控制器：：获取关键帧故事板启动

返回标识情节提要开头的关键帧。

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>返回值

指向基本关键帧的指针，用于标识情节提要的开头。

### <a name="remarks"></a>备注

获取此关键帧以基于情节提要启动时的时间时刻设置任何其他关键帧或过渡。

## <a name="canimationcontrollergetuianimationmanager"></a><a name="getuianimationmanager"></a>动画控制器：：获取动画管理器

提供对封装的 IUI动画管理器对象的访问。

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>返回值

如果动画管理器的创建失败，则指向 IUI动画管理器接口或 NULL 的指针。

### <a name="remarks"></a>备注

如果当前操作系统不支持 Windows 动画 API，则此方法将返回 NULL，之后 CAnimationController 上的所有后续调用：有效返回 FALSE。 您可能需要访问 IUI动画管理器才能调用其接口方法，这些方法不是由动画控制器包装的。

## <a name="canimationcontrollergetuianimationtimer"></a><a name="getuianimationtimer"></a>动画控制器：：获取动画计时器

提供对封装的 IUI动画定时对象的访问。

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>返回值

如果动画计时器的创建失败，则指向 IUIAnimationTimer 接口或 NULL 的指针。

### <a name="remarks"></a>备注

如果当前操作系统不支持 Windows 动画 API，则此方法将返回 NULL，之后 CAnimationController 上的所有后续调用：有效返回 FALSE。

## <a name="canimationcontrollergetuitransitionfactory"></a><a name="getuitransitionfactory"></a>动画控制器：：获取 UI 转换工厂

如果创建过渡库失败，则指向 IUIAnimation 转换工厂接口或 NULL 的指针。

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>返回值

如果转换工厂的创建失败，则指向 IUIAnimation 转换工厂或 NULL 的指针。

### <a name="remarks"></a>备注

如果当前操作系统不支持 Windows 动画 API，则此方法将返回 NULL，之后 CAnimationController 上的所有后续调用：有效返回 FALSE。

## <a name="canimationcontrollergetuitransitionlibrary"></a><a name="getuitransitionlibrary"></a>动画控制器：：获取 UI 转换库

提供对封装的 IUI 动画转换库对象的访问。

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>返回值

如果创建过渡库失败，则指向 IUIAnimation 转换库接口或 NULL 的指针。

### <a name="remarks"></a>备注

如果当前操作系统不支持 Windows 动画 API，则此方法将返回 NULL，之后 CAnimationController 上的所有后续调用：有效返回 FALSE。

## <a name="canimationcontrollerisanimationinprogress"></a><a name="isanimationinprogress"></a>动画控制器：：动画在进行中

告诉是否至少有一个组正在播放动画。

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>返回值

如果此动画控制器正在进行动画，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

检查动画管理器的状态，如果状态为UI_ANIMATION_MANAGER_BUSY，则返回 TRUE。

## <a name="canimationcontrollerisvalid"></a><a name="isvalid"></a>动画控制器：：有效

告诉动画控制器是否有效。

```
BOOL IsValid() const;
```

### <a name="return-value"></a>返回值

如果动画控制器有效，则为 TRUE;否则 FALSE。

### <a name="remarks"></a>备注

仅当当前操作系统不支持 Windows 动画 API 且动画管理器的创建失败，因为它未注册时，此方法才会返回 FALSE。 在 COM 库初始化后，需要至少调用 GetUI动画管理器一次，以便设置此标志。

## <a name="canimationcontrollerm_bisvalid"></a><a name="m_bisvalid"></a>动画控制器：：m_bIsValid

指定动画控制器是否有效。 如果当前操作系统不支持 Windows 动画 API，则此成员设置为 FALSE。

```
BOOL m_bIsValid;
```

## <a name="canimationcontrollerm_lstanimationgroups"></a><a name="m_lstanimationgroups"></a>动画控制器：：m_lstAnimationGroups

属于此动画控制器的动画组的列表。

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

## <a name="canimationcontrollerm_panimationmanager"></a><a name="m_panimationmanager"></a>动画控制器：：m_pAnimationManager

存储指向动画管理器 COM 对象的指针。

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

## <a name="canimationcontrollerm_panimationtimer"></a><a name="m_panimationtimer"></a>动画控制器：：m_pAnimationTimer

存储指向动画计时器 COM 对象的指针。

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

## <a name="canimationcontrollerm_prelatedwnd"></a><a name="m_prelatedwnd"></a>动画控制器：：m_pRelatedWnd

指向相关 CWnd 对象的指针，可在动画管理器的状态更改或更新后事件发生时自动重绘。 可以为 NULL。

```
CWnd* m_pRelatedWnd;
```

## <a name="canimationcontrollerm_ptransitionfactory"></a><a name="m_ptransitionfactory"></a>动画控制器：：m_pTransitionFactory

存储指向过渡工厂 COM 对象的指针。

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

## <a name="canimationcontrollerm_ptransitionlibrary"></a><a name="m_ptransitionlibrary"></a>动画控制器：：m_pTransitionLibrary

存储指向过渡库 COM 对象的指针。

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

## <a name="canimationcontrolleronafterschedule"></a><a name="onafterschedule"></a>动画控制器：：在计划后

当指定组的动画刚刚计划时，由框架调用。

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>参数

*p组*<br/>
指向已计划的动画组的指针。

### <a name="remarks"></a>备注

默认实现从指定组中删除关键帧，并从属于指定组的动画变量转换。 可以在派生类中重写，以便根据动画计划执行任何其他操作。

## <a name="canimationcontrolleronanimationintegervaluechanged"></a><a name="onanimationintegervaluechanged"></a>动画控制器：：在动画中值已更改

当动画变量的整数值发生更改时，由框架调用。

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>参数

*p组*<br/>
指向包含其值已更改的动画对象的动画组的指针。

*pObject*<br/>
指向动画对象的指针，该对象包含其值已更改的动画变量。

*可变*<br/>
指向动画变量的指针。

*新值*<br/>
指定新值。

*前置值*<br/>
指定以前的值。

### <a name="remarks"></a>备注

如果启用启用启用 IntegerValue改变事件为特定动画变量或动画对象启用动画变量事件，则调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

## <a name="canimationcontrolleronanimationmanagerstatuschanged"></a><a name="onanimationmanagerstatuschanged"></a>动画控制器：：打开动画管理器状态已更改

由框架调用以响应动画管理器中的状态更改事件。

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>参数

*新状态*<br/>
新的动画管理器状态。

*上一个状态*<br/>
以前的动画管理器状态。

### <a name="remarks"></a>备注

如果使用启用动画管理器事件启用动画管理器事件，则调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 如果已使用 SetTheNd 设置相关窗口，则默认实现将更新该窗口。

## <a name="canimationcontrolleronanimationtimerpostupdate"></a><a name="onanimationtimerpostupdate"></a>动画控制器：：打开动画计时器后更新

动画更新完成后由框架调用。

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>备注

如果使用启用动画计时器事件处理程序启用计时器事件处理程序，则调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

## <a name="canimationcontrolleronanimationtimerpreupdate"></a><a name="onanimationtimerpreupdate"></a>动画控制器：：打开动画计时器预更新

在动画更新开始之前由框架调用。

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>备注

如果使用启用动画计时器事件处理程序启用计时器事件处理程序，则调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

## <a name="canimationcontrolleronanimationtimerrenderingtooslow"></a><a name="onanimationtimerrenderingtooslow"></a>动画控制器：：动画计时器渲染速度慢

当动画的渲染帧速率低于所需的最小帧速率时，由框架调用。

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>参数

*Fps*<br/>
当前帧速率（以帧/秒表示）。

### <a name="remarks"></a>备注

如果使用启用动画计时器事件处理程序启用计时器事件处理程序，则调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 通过调用 IUI动画计时器：：设置FrameRate阈值来指定所需的最小帧速率。

## <a name="canimationcontrolleronanimationvaluechanged"></a><a name="onanimationvaluechanged"></a>动画控制器：：打开动画值已更改

当动画变量的值发生更改时，由框架调用。

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>参数

*p组*<br/>
指向包含其值已更改的动画对象的动画组的指针。

*pObject*<br/>
指向动画对象的指针，该对象包含其值已更改的动画变量。

*可变*<br/>
指向动画变量的指针。

*新值*<br/>
指定新值。

*前置值*<br/>
指定以前的值。

### <a name="remarks"></a>备注

如果启用动画变量事件，启用启用ValueChangedEvent为特定动画变量或动画对象调用，则调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

## <a name="canimationcontrolleronbeforeanimationstart"></a><a name="onbeforeanimationstart"></a>动画控制器：：在动画启动之前打开

在计划动画之前由框架调用。

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>参数

*p组*<br/>
指向其动画即将开始的动画组的指针。

### <a name="remarks"></a>备注

此调用路由到相关的 CWnd，并且可以在派生类中重写，以在指定组的动画启动之前执行任何其他操作。

## <a name="canimationcontrolleronhasprioritycancel"></a><a name="onhasprioritycancel"></a>动画控制器：：onHas优先取消

由框架调用以便解决计划冲突。

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>参数

*p组计划*<br/>
拥有当前已计划的情节提要的组。

*p组新*<br/>
拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。

*优先级效果*<br/>
如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。

### <a name="return-value"></a>返回值

如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TURE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。

### <a name="remarks"></a>备注

如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_CANCEL，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关[冲突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的详细信息，请阅读 Windows 动画 API 文档。

## <a name="canimationcontrolleronhasprioritycompress"></a><a name="onhasprioritycompress"></a>动画控制器：：打开哈斯优先压缩

由框架调用以便解决计划冲突。

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>参数

*p组计划*<br/>
拥有当前已计划的情节提要的组。

*p组新*<br/>
拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。

*优先级效果*<br/>
如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。

### <a name="return-value"></a>返回值

如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TURE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。

### <a name="remarks"></a>备注

如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_COMPRESS，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关[冲突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的详细信息，请阅读 Windows 动画 API 文档。

## <a name="canimationcontrolleronhaspriorityconclude"></a><a name="onhaspriorityconclude"></a>动画控制器：：onHas优先结束

由框架调用以便解决计划冲突。

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>参数

*p组计划*<br/>
拥有当前已计划的情节提要的组。

*p组新*<br/>
拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。

*优先级效果*<br/>
如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。

### <a name="return-value"></a>返回值

如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TURE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。

### <a name="remarks"></a>备注

如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_CONCLUDE，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关[冲突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的详细信息，请阅读 Windows 动画 API 文档。

## <a name="canimationcontrolleronhasprioritytrim"></a><a name="onhasprioritytrim"></a>动画控制器：：onHas优先修剪

由框架调用以便解决计划冲突。

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>参数

*p组计划*<br/>
拥有当前已计划的情节提要的组。

*p组新*<br/>
拥有计划中的新情节提要的组与 pGroupScheduled 所拥有的已计划的情节提要发生冲突。

*优先级效果*<br/>
如果 pGroupScheduled 具有更高的优先级，则对 pGroupNew 会有潜在影响。

### <a name="return-value"></a>返回值

如果 pGroupNew 所拥有的情节提要具有优先级，则应返回 TURE。 如果 pGroupScheduled 所拥有的情节提要具有优先级，则应返回 FALSE。

### <a name="remarks"></a>备注

如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_TRIM，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关[冲突管理](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)的详细信息，请阅读 Windows 动画 API 文档。

## <a name="canimationcontrolleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>动画控制器：：在故事板状态更改

情节提要状态更改时由框架调用。

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>参数

*p组*<br/>
指向具有状态已更改的情节提要的动画组的指针。

*新状态*<br/>
指定新状态。

*上一个状态*<br/>
指定上一个状态。

### <a name="remarks"></a>备注

如果使用 C动画控制器：：启用 Storyboard事件处理程序启用情节提要事件，则调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

## <a name="canimationcontrolleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>动画控制器：：在故事板上更新

更新情节提要时由框架调用。

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>参数

*p组*<br/>
指向拥有情节提要的组的指针。

### <a name="remarks"></a>备注

如果使用 C动画控制器：：启用 Storyboard事件处理程序启用情节提要事件，则调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。

## <a name="canimationcontrollerremoveallanimationgroups"></a><a name="removeallanimationgroups"></a>动画控制器：：删除所有动画组

从动画控制器中删除所有动画组。

```
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>备注

所有组都将被删除，如果存储在应用程序级别，其指针必须失效。 如果 CAnimationGroup：：m_bAutodestroyAnimationObjects删除的组为 TRUE，则属于该组的所有动画对象都将被删除;如果 CAnimationGroup：m_bAutodestroyAnimationObjects 为要删除的组，则属于该组的所有动画对象都将被删除。否则，它们对父动画控制器的引用将设置为 NULL，并且可以添加到其他控制器。

## <a name="canimationcontrollerremoveanimationgroup"></a><a name="removeanimationgroup"></a>动画控制器：：删除动画组

从动画控制器中删除具有指定 ID 的动画组。

```
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>参数

*n集团ID*<br/>
指定动画组 ID。

### <a name="remarks"></a>备注

此方法从组的内部列表中删除动画组并删除它，因此，如果您存储了指向该动画组的指针，则必须将其失效。 如果 CAnimationGroup：：m_bAutodestroyAnimationObjects 为 TRUE，则属于该组的所有动画对象都将被删除;如果 CAnimationGroup：：m_bAutodestroyAnimationObjects 为 TRUE，则属于该组的所有动画对象都将被删除。否则，它们对父动画控制器的引用将设置为 NULL，并且可以添加到其他控制器。

## <a name="canimationcontrollerremoveanimationobject"></a><a name="removeanimationobject"></a>动画控制器：：删除动画对象

从动画控制器中删除动画对象。

```
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>参数

*pObject*<br/>
指向动画对象的指针。

*b 不删除*<br/>
如果此参数为 TRUE，则删除后不会删除对象。

### <a name="remarks"></a>备注

从动画控制器和动画组中删除动画对象。 如果不应再对特定对象进行动画处理，或者需要将对象移动到其他动画控制器，请调用此函数。 在最后一种情况下，bNoDelete 必须为 TRUE。

## <a name="canimationcontrollerremovetransitions"></a><a name="removetransitions"></a>动画控制器：：删除转换

从属于指定组的动画对象中删除过渡。

```
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>参数

*n集团ID*<br/>
指定组 ID。

### <a name="remarks"></a>备注

该组循环在其动画对象上，并为每个动画对象调用 ClearTransition（FALSE）。 计划动画后，框架将调用此方法。

## <a name="canimationcontrollerschedulegroup"></a><a name="schedulegroup"></a>动画控制器：：计划组

计划动画。

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>参数

*n集团ID*<br/>
指定要计划动画组 ID。

*time*<br/>
指定计划时间。

### <a name="return-value"></a>返回值

如果动画计划成功，则为 TRUE。 如果未创建情节提要，或者发生其他错误，则 FALSE。

### <a name="remarks"></a>备注

您必须调用 AnimateGroup，参数 b"计划现在"设置为 FALSE，提前计划组。 您可以指定从 IUI 动画计时器获得所需的动画时间：：获取时间。 如果时间参数为 0.0，则动画将安排在当前时间。

## <a name="canimationcontrollersetrelatedwnd"></a><a name="setrelatedwnd"></a>动画控制器：：设置相关

在动画控制器和窗口之间建立关系。

```
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>参数

*pwnd*<br/>
要设置的窗口对象的指针。

### <a name="remarks"></a>备注

如果设置了相关的 CWnd 对象，则动画控制器可以在动画管理器的状态发生或更新事件后计时器发生时自动更新它（发送WM_PAINT消息）。

## <a name="canimationcontrollerupdateanimationmanager"></a><a name="updateanimationmanager"></a>动画控制器：：更新动画管理器

指示动画管理器更新所有动画变量的值。

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>备注

调用此方法会将动画管理器提升为当前时间，根据需要更改情节提要的状态，并将任何动画变量更新为适当的插值。 在内部，此方法调用 IUI动画计时器：：获取时间（现在）和 IUI动画管理器：更新（现在）。 重写派生类中的此方法以自定义此行为。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
