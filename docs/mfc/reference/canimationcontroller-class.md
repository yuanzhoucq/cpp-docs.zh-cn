---
title: "CAnimationController 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationController
- afxanimationcontroller/CAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationController class
ms.assetid: ed294c98-695e-40a6-b940-33ef1d40aa6b
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 2cf243c25f14ba016f6f30af264322c658e7322c
ms.lasthandoff: 02/24/2017

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
|[CAnimationController::CAnimationController](#canimationcontroller)|构造动画控制器。|  
|[CAnimationController:: ~ CAnimationController](#canimationcontroller__~canimationcontroller)|析构函数。 当动画控制器对象被销毁时调用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationController::AddAnimationObject](#addanimationobject)|将动画对象添加到动画控制器所属的组。|  
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|向组添加关键帧。|  
|[CAnimationController::AnimateGroup](#animategroup)|准备要运行动画的组，并根据需要对其进行安排。|  
|[CAnimationController::CleanUpGroup](#cleanupgroup)|已重载。 由框架来清理组，在计划动画时调用。|  
|[CAnimationController::CreateKeyframe](#createkeyframe)|已重载。 创建取决于过渡的关键帧并将其添加到指定的组。|  
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|设置或释放调用动画管理器的状态更改时的处理程序。|  
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|设置或释放计时事件处理程序，并对于定时更新处理程序。|  
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|设置或释放优先级比较处理程序以调用以决定是否计划的情节提要可以取消、 得出的结论是，修整或压缩。|  
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|设置或释放用于演示图板状态以及更新事件处理程序。|  
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|已重载。 查找依据其情节提要动画组。|  
|[CAnimationController::FindAnimationObject](#findanimationobject)|查找包含指定的动画变量的动画对象。|  
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|返回一个标识情节提要的开头的关键帧。|  
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|提供对封装 IUIAnimationManager 对象的访问。|  
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|提供对封装 IUIAnimationTimer 对象的访问。|  
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|一个指向 IUIAnimationTransitionFactory 接口或 NULL，如果创建的转换库失败。|  
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|提供对封装 IUIAnimationTransitionLibrary 对象的访问。|  
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|指示是否在至少一个组在播放动画。|  
|[CAnimationController::IsValid](#isvalid)|告知动画控制器是否有效。|  
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|当动画变量的整数值发生更改时由框架调用。|  
|[CAnimationController::OnAnimationManagerStatusChanged](#onanimationmanagerstatuschanged)|由框架响应来自动画管理器 StatusChanged 事件中调用。|  
|[CAnimationController::OnAnimationTimerPostUpdate](#onanimationtimerpostupdate)|在完成动画更新后，由框架调用。|  
|[CAnimationController::OnAnimationTimerPreUpdate](#onanimationtimerpreupdate)|在动画更新开始之前，由框架调用。|  
|[CAnimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|由框架调用，当动画的呈现帧速率低于最小的理想帧速率。|  
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|当动画变量的值发生更改时由框架调用。|  
|[CAnimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|由框架调用正确计划动画之前。|  
|[CAnimationController::OnHasPriorityCancel](#onhasprioritycancel)|由框架调用以便解决计划冲突。|  
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|由框架调用以便解决计划冲突。|  
|[CAnimationController::OnHasPriorityConclude](#onhaspriorityconclude)|由框架调用以便解决计划冲突。|  
|[CAnimationController::OnHasPriorityTrim](#onhasprioritytrim)|由框架调用以便解决计划冲突。|  
|[CAnimationController::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|演示图板状态更改时由框架调用。|  
|[CAnimationController::OnStoryboardUpdated](#onstoryboardupdated)|在演示图板更新时由框架调用。|  
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|从动画控制器中删除所有动画组。|  
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|从动画控制器中删除具有指定 ID 的动画组。|  
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|从动画控制器中删除的动画对象。|  
|[CAnimationController::RemoveTransitions](#removetransitions)|从属于指定组的动画对象中删除转换。|  
|[CAnimationController::ScheduleGroup](#schedulegroup)|安排动画。|  
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|建立动画控制器和窗口之间的关系。|  
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|指示动画管理器，以更新所有动画变量的值。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationController::CleanUpGroup](#cleanupgroup)|已重载。 一个帮助程序，清除该组。|  
|[CAnimationController::OnAfterSchedule](#onafterschedule)|指定组的动画只是计划时，由框架调用。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|关键帧，表示情节提要的开头。|  
|[CAnimationController::m_bIsValid](#m_bisvalid)|指定动画控制器是否为有效。 如果当前操作系统不支持 Windows 动画 API，此成员设置为 FALSE。|  
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|属于此动画控制器的动画组的列表。|  
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|存储指向动画管理器 COM 对象的指针。|  
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|存储指向动画计时器 COM 对象的指针。|  
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|指向相关的 CWnd 对象，可以将自动重绘动画管理器的状态已更改，或后更新事件发生时的指针。 可以为 NULL。|  
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|存储转换工厂 COM 对象的指针。|  
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|存储转换库 COM 对象的指针。|  
  
## <a name="remarks"></a>备注  
 CAnimationController 类是管理动画的键类。 您可能创建的动画控制器的一个或多个实例应用程序中，并 （可选） 将动画控制器实例连接到使用 CAnimationController::SetRelatedWnd CWnd 对象。 自动将发送 WM_PAINT 消息到相关的窗口动画管理器状态已更改或已更新动画计时器时需要此连接。 如果不启用此关系，则必须重绘手动显示动画的窗口。 实现此目的，您可以从 CAnimationController 派生一个类并覆盖 OnAnimationManagerStatusChanged 和/或 OnAnimationTimerPostUpdate 并使之无效的一个或多个 windows 在必要时。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CAnimationController`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="a-namedtorcanimationcontrollera--canimationcontrollercanimationcontroller"></a><a name="_dtorcanimationcontroller"></a>CAnimationController:: ~ CAnimationController  
 析构函数。 当动画控制器对象被销毁时调用。  
  
```  
virtual ~CAnimationController(void);
```   
  
##  <a name="a-nameaddanimationobjecta--canimationcontrolleraddanimationobject"></a><a name="addanimationobject"></a>CAnimationController::AddAnimationObject  
 将动画对象添加到动画控制器所属的组。  
  
```  
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```  
  
### <a name="parameters"></a>参数  
 `pObject`  
 指向动画对象的指针。  
  
### <a name="return-value"></a>返回值  
 如果函数成功，则上添加 pObject 的现有或新动画组指向的指针如果已将 pObject 添加到的组中属于另一个动画控制器，则为 NULL。  
  
### <a name="remarks"></a>备注  
 调用此方法将动画对象添加到动画控制器。 一个对象将添加到对象的 GroupID 根据一组 （请参阅 CAnimationBaseObject::SetID）。 如果正在使用指定的 GroupID 添加的第一个对象，动画控制器将创建一个新组。 动画对象可以添加到一个动画控制器。 如果您需要将对象添加到另一个控制器，则应首先调用 RemoveAnimationObject。 如果使用新的 GroupID SetID 调用已添加到组的对象时，将从旧的组中删除并添加到具有指定 ID 的另一个组对象  
  
##  <a name="a-nameaddkeyframetogroupa--canimationcontrolleraddkeyframetogroup"></a><a name="addkeyframetogroup"></a>CAnimationController::AddKeyframeToGroup  
 向组添加关键帧。  
  
```  
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,  
    CBaseKeyFrame* pKeyframe);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定组的 id。  
  
 `pKeyframe`  
 指向一个关键帧的指针。  
  
### <a name="return-value"></a>返回值  
 如果该函数成功，则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 通常您不需要调用此方法，请改用 CAnimationController::CreateKeyframe，它创建并自动将创建关键帧添加到组。  
  
##  <a name="a-nameanimategroupa--canimationcontrolleranimategroup"></a><a name="animategroup"></a>CAnimationController::AnimateGroup  
 准备要运行动画的组，并根据需要对其进行安排。  
  
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
 如果动画已成功调度把那个运行，则为 TRUE。  
  
### <a name="remarks"></a>备注  
 此方法执行实际工作创建情节提要、 添加动画变量、 应用转换和设置关键帧。 就可以推迟计划如果 bScheduleNow 设置为 FALSE。 在这种情况下指定的组将包含已设置了动画情节提要。 此时，你可以设置的情节提要和动画变量的事件。 当您实际需要运行动画调用 CAnimationController::ScheduleGroup。  
  
##  <a name="a-namecanimationcontrollera--canimationcontrollercanimationcontroller"></a><a name="canimationcontroller"></a>CAnimationController::CAnimationController  
 构造动画控制器。  
  
```  
CAnimationController(void);
```   
  
##  <a name="a-namecleanupgroupa--canimationcontrollercleanupgroup"></a><a name="cleanupgroup"></a>CAnimationController::CleanUpGroup  
 由框架来清理组，在计划动画时调用。  
  
```  
void CleanUpGroup(UINT32 nGroupID);  
void CleanUpGroup(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定 GroupID。  
  
 `pGroup`  
 指向动画组要清理的指针。  
  
### <a name="remarks"></a>备注  
 此方法中删除所有转换以及关键帧从指定的组，因为已安排动画后，它们是不相关。  
  
##  <a name="a-namecreatekeyframea--canimationcontrollercreatekeyframe"></a><a name="createkeyframe"></a>CAnimationController::CreateKeyframe  
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
  
##  <a name="a-nameenableanimationmanagereventa--canimationcontrollerenableanimationmanagerevent"></a><a name="enableanimationmanagerevent"></a>CAnimationController::EnableAnimationManagerEvent  
 设置或释放调用动画管理器的状态更改时的处理程序。  
  
```  
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `bEnable`  
 指定是否要设置或释放一个处理程序。  
  
### <a name="return-value"></a>返回值  
 如果该处理程序已成功设置或释放，则为 TRUE。  
  
### <a name="remarks"></a>备注  
 一个处理程序设置 （已启用） 时 Windows 动画在动画管理器的状态更改时调用 OnAnimationManagerStatusChanged。  
  
##  <a name="a-nameenableanimationtimereventhandlera--canimationcontrollerenableanimationtimereventhandler"></a><a name="enableanimationtimereventhandler"></a>CAnimationController::EnableAnimationTimerEventHandler  
 设置或释放计时事件处理程序，并对于定时更新处理程序。  
  
```  
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,  
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```  
  
### <a name="parameters"></a>参数  
 `bEnable`  
 指定是否要设置或释放在处理程序。  
  
 `idleBehavior`  
 指定计时器更新处理程序的空闲行为。  
  
### <a name="return-value"></a>返回值  
 如果处理程序已成功设置或释放; 则为 TRUE如果此属性为 FALSE 调用第二次而不释放这些处理程序第一次，或如果任何其他发生错误。  
  
### <a name="remarks"></a>备注  
 在处理程序设置 （已启用） 的 Windows 动画 API 调用 OnAnimationTimerPreUpdate，OnAnimationTimerPostUpdate，OnRenderingTooSlow 方法。 您需要使动画计时器，以允许 Windows 动画 API 更新情节提要。 否则，您需要调用 CAnimationController::UpdateAnimationManager，以便直接在动画管理器来更新所有动画变量的值。  
  
##  <a name="a-nameenableprioritycomparisonhandlera--canimationcontrollerenableprioritycomparisonhandler"></a><a name="enableprioritycomparisonhandler"></a>CAnimationController::EnablePriorityComparisonHandler  
 设置或释放优先级比较处理程序以调用以决定是否计划的情节提要可以取消、 得出的结论是，修整或压缩。  
  
```  
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```  
  
### <a name="parameters"></a>参数  
 `dwHandlerType`  
 UI_ANIMATION_PHT_ 组合标志 （请参见备注），它指定要设置或释放何种处理程序。  
  
### <a name="return-value"></a>返回值  
 如果该处理程序已成功设置或释放，则为 TRUE。  
  
### <a name="remarks"></a>备注  
 Windows 动画一个处理程序设置 （已启用） 时调用的下面的虚方法，具体取决于 dwHandlerType: OnHasPriorityCancel、 OnHasPriorityConclude、 OnHasPriorityTrim、 OnHasPriorityCompress。 dwHandler 可以是下列标志的组合︰ UI_ANIMATION_PHT_NONE-发布所有处理程序 UI_ANIMATION_PHT_CANCEL-设置取消比较处理程序 UI_ANIMATION_PHT_CONCLUDE-设置结束提问比较处理程序，UI_ANIMATION_PHT_COMPRESS-设置取消比较处理程序 UI_ANIMATION_PHT_CONCLUDE_REMOVE 的 Compress 比较处理程序，UI_ANIMATION_PHT_TRIM 集剪裁比较处理程序 UI_ANIMATION_PHT_CANCEL_REMOVE-删除-删除结束提问比较处理程序 UI_ANIMATION_PHT_COMPRESS_REMOVE-删除 Compress 比较处理程序 UI_ANIMATION_PHT_TRIM_REMOVE-删除剪裁比较处理程序  
  
##  <a name="a-nameenablestoryboardeventhandlera--canimationcontrollerenablestoryboardeventhandler"></a><a name="enablestoryboardeventhandler"></a>CAnimationController::EnableStoryboardEventHandler  
 设置或释放用于演示图板状态以及更新事件处理程序。  
  
```  
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,  
    BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定组的 id。  
  
 `bEnable`  
 指定是否要设置或释放一个处理程序。  
  
### <a name="return-value"></a>返回值  
 如果该处理程序已成功设置或释放; 则为 TRUE如果现在找到指定的动画组或尚未启动指定的组的动画和其内部的情节提要为 NULL，则为 FALSE。  
  
### <a name="remarks"></a>备注  
 当设置一个处理程序 （已启用） 的 Windows 动画 API 调用 OnStoryboardStatusChanges 和 OnStoryboardUpdated 虚拟方法。 一个处理程序必须设置为指定的动画组中，在调用 CAnimationController::Animate 后因为这会创建封装的 IUIAnimationStoryboard 对象。  
  
##  <a name="a-namefindanimationgroupa--canimationcontrollerfindanimationgroup"></a><a name="findanimationgroup"></a>CAnimationController::FindAnimationGroup  
 查找动画组通过其组 id。  
  
```  
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);  
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定 GroupID。  
  
 `pStoryboard`  
 指向一个情节提要的指针。  
  
### <a name="return-value"></a>返回值  
 一个指向动画组或者为 NULL，如果找不到具有指定 ID 的组。  
  
### <a name="remarks"></a>备注  
 使用此方法在运行时查找动画组。 一组被创建，并具有特定 GroupID 的动画对象被添加到动画控制器时添加到动画组的内部列表。  
  
##  <a name="a-namefindanimationobjecta--canimationcontrollerfindanimationobject"></a><a name="findanimationobject"></a>CAnimationController::FindAnimationObject  
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
 输出。 包含指向动画对象或空值的指针。  
  
 `ppGroup`  
 输出。 包含指向包含动画对象，则为 NULL 的动画组。  
  
### <a name="return-value"></a>返回值  
 如果对象; 如果未找到，则返回 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 从事件处理程序时需要查找从传入的动画变量的动画对象调用。  
  
##  <a name="a-namegkeyframestoryboardstarta--canimationcontrollergkeyframestoryboardstart"></a><a name="g_keyframestoryboardstart"></a>CAnimationController::gkeyframeStoryboardStart  
 关键帧，表示情节提要的开头。  
  
```  
static CBaseKeyFrame gkeyframeStoryboardStart;  
```  
  
##  <a name="a-namegetkeyframestoryboardstarta--canimationcontrollergetkeyframestoryboardstart"></a><a name="getkeyframestoryboardstart"></a>CAnimationController::GetKeyframeStoryboardStart  
 返回一个标识情节提要的开头的关键帧。  
  
```  
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```  
  
### <a name="return-value"></a>返回值  
 指向标识情节提要的开头的基本关键帧的指针。  
  
### <a name="remarks"></a>备注  
 获取此关键帧，以建立在那一刻开始一个情节提要和时间的基础的任何其他关键帧或转换。  
  
##  <a name="a-namegetuianimationmanagera--canimationcontrollergetuianimationmanager"></a><a name="getuianimationmanager"></a>CAnimationController::GetUIAnimationManager  
 提供对封装 IUIAnimationManager 对象的访问。  
  
```  
IUIAnimationManager* GetUIAnimationManager();
```  
  
### <a name="return-value"></a>返回值  
 一个指向 IUIAnimationManager 接口或 NULL，如果动画管理器创建失败。  
  
### <a name="remarks"></a>备注  
 如果当前操作系统不支持 Windows 动画 API，此方法将返回 NULL 并在此之后 CAnimationController::IsValid 上的所有后续调用返回 FALSE。 您可能需要访问 IUIAnimationManager 以调用未包装的动画控制器及其接口方法。  
  
##  <a name="a-namegetuianimationtimera--canimationcontrollergetuianimationtimer"></a><a name="getuianimationtimer"></a>CAnimationController::GetUIAnimationTimer  
 提供对封装 IUIAnimationTimer 对象的访问。  
  
```  
IUIAnimationTimer* GetUIAnimationTimer();
```  
  
### <a name="return-value"></a>返回值  
 一个指向 IUIAnimationTimer 接口或 NULL，如果创建动画计时器失败。  
  
### <a name="remarks"></a>备注  
 如果当前操作系统不支持 Windows 动画 API，此方法将返回 NULL 并在此之后 CAnimationController::IsValid 上的所有后续调用返回 FALSE。  
  
##  <a name="a-namegetuitransitionfactorya--canimationcontrollergetuitransitionfactory"></a><a name="getuitransitionfactory"></a>CAnimationController::GetUITransitionFactory  
 一个指向 IUIAnimationTransitionFactory 接口或 NULL，如果创建的转换库失败。  
  
```  
IUIAnimationTransitionFactory* GetUITransitionFactory();
```  
  
### <a name="return-value"></a>返回值  
 一个指向 IUIAnimationTransitionFactory 或 NULL，如果转换工厂创建失败。  
  
### <a name="remarks"></a>备注  
 如果当前操作系统不支持 Windows 动画 API，此方法将返回 NULL 并在此之后 CAnimationController::IsValid 上的所有后续调用返回 FALSE。  
  
##  <a name="a-namegetuitransitionlibrarya--canimationcontrollergetuitransitionlibrary"></a><a name="getuitransitionlibrary"></a>CAnimationController::GetUITransitionLibrary  
 提供对封装 IUIAnimationTransitionLibrary 对象的访问。  
  
```  
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```  
  
### <a name="return-value"></a>返回值  
 一个指向 IUIAnimationTransitionLibrary 接口或 NULL，如果创建的转换库失败。  
  
### <a name="remarks"></a>备注  
 如果当前操作系统不支持 Windows 动画 API，此方法将返回 NULL 并在此之后 CAnimationController::IsValid 上的所有后续调用返回 FALSE。  
  
##  <a name="a-nameisanimationinprogressa--canimationcontrollerisanimationinprogress"></a><a name="isanimationinprogress"></a>CAnimationController::IsAnimationInProgress  
 指示是否在至少一个组在播放动画。  
  
```  
virtual BOOL IsAnimationInProgress();
```  
  
### <a name="return-value"></a>返回值  
 如果正在对此动画控制器; 动画则为 TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 检查动画管理器的状态，并返回 TRUE，如果状态为 UI_ANIMATION_MANAGER_BUSY。  
  
##  <a name="a-nameisvalida--canimationcontrollerisvalid"></a><a name="isvalid"></a>CAnimationController::IsValid  
 告知动画控制器是否有效。  
  
```  
BOOL IsValid() const;  
```  
  
### <a name="return-value"></a>返回值  
 如果动画控制器是否有效，则为，TRUE否则为 FALSE。  
  
### <a name="remarks"></a>备注  
 此方法将返回 FALSE，仅当 Windows 动画 API 不支持当前的操作系统和动画管理器创建失败，因为未注册。 您需要至少一次在初始化 COM 库，以使此标志设置后，调用 GetUIAnimationManager。  
  
##  <a name="a-namembisvalida--canimationcontrollermbisvalid"></a><a name="m_bisvalid"></a>CAnimationController::m_bIsValid  
 指定动画控制器是否为有效。 如果当前操作系统不支持 Windows 动画 API，此成员设置为 FALSE。  
  
```  
BOOL m_bIsValid;  
```  
  
##  <a name="a-namemlstanimationgroupsa--canimationcontrollermlstanimationgroups"></a><a name="m_lstanimationgroups"></a>CAnimationController::m_lstAnimationGroups  
 属于此动画控制器的动画组的列表。  
  
```  
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;  
```  
  
##  <a name="a-namempanimationmanagera--canimationcontrollermpanimationmanager"></a><a name="m_panimationmanager"></a>CAnimationController::m_pAnimationManager  
 存储指向动画管理器 COM 对象的指针。  
  
```  
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;  
```  
  
##  <a name="a-namempanimationtimera--canimationcontrollermpanimationtimer"></a><a name="m_panimationtimer"></a>CAnimationController::m_pAnimationTimer  
 存储指向动画计时器 COM 对象的指针。  
  
```  
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;  
```  
  
##  <a name="a-namemprelatedwnda--canimationcontrollermprelatedwnd"></a><a name="m_prelatedwnd"></a>CAnimationController::m_pRelatedWnd  
 指向相关的 CWnd 对象，可以将自动重绘动画管理器的状态已更改，或后更新事件发生时的指针。 可以为 NULL。  
  
```  
CWnd* m_pRelatedWnd;  
```  
  
##  <a name="a-namemptransitionfactorya--canimationcontrollermptransitionfactory"></a><a name="m_ptransitionfactory"></a>CAnimationController::m_pTransitionFactory  
 存储转换工厂 COM 对象的指针。  
  
```  
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;  
```  
  
##  <a name="a-namemptransitionlibrarya--canimationcontrollermptransitionlibrary"></a><a name="m_ptransitionlibrary"></a>CAnimationController::m_pTransitionLibrary  
 存储转换库 COM 对象的指针。  
  
```  
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;  
```  
  
##  <a name="a-nameonafterschedulea--canimationcontrolleronafterschedule"></a><a name="onafterschedule"></a>CAnimationController::OnAfterSchedule  
 指定组的动画只是计划时，由框架调用。  
  
```  
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>参数  
 `pGroup`  
 指向已安排的动画组的指针。  
  
### <a name="remarks"></a>备注  
 默认实现关键帧，则删除指定的组并将转换从属于指定组的动画变量。 可以重写在派生类才能根据动画安排任何其他操作。  
  
##  <a name="a-nameonanimationintegervaluechangeda--canimationcontrolleronanimationintegervaluechanged"></a><a name="onanimationintegervaluechanged"></a>CAnimationController::OnAnimationIntegerValueChanged  
 当动画变量的整数值发生更改时由框架调用。  
  
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
 已更改的指针指向包含其值的动画对象的动画组。  
  
 `pObject`  
 指向一个包含其值已更改的动画变量的动画对象的指针。  
  
 `variable`  
 指向动画变量的指针。  
  
 `newValue`  
 指定新值。  
  
 `prevValue`  
 指定前一个值。  
  
### <a name="remarks"></a>备注  
 如果与为特定的动画变量或动画对象调用 EnableIntegerValueChangedEvent 启用动画变量的事件，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。  
  
##  <a name="a-nameonanimationmanagerstatuschangeda--canimationcontrolleronanimationmanagerstatuschanged"></a><a name="onanimationmanagerstatuschanged"></a>CAnimationController::OnAnimationManagerStatusChanged  
 由框架响应来自动画管理器 StatusChanged 事件中调用。  
  
```  
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,  
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```  
  
### <a name="parameters"></a>参数  
 `newStatus`  
 新的动画管理器状态。  
  
 `previousStatus`  
 上一个动画管理器状态。  
  
### <a name="remarks"></a>备注  
 如果启用与 EnableAnimationManagerEvent 动画管理器事件，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 如果设置 SetRelatedWnd，默认实现将更新相关的窗口。  
  
##  <a name="a-nameonanimationtimerpostupdatea--canimationcontrolleronanimationtimerpostupdate"></a><a name="onanimationtimerpostupdate"></a>CAnimationController::OnAnimationTimerPostUpdate  
 在完成动画更新后，由框架调用。  
  
```  
virtual void OnAnimationTimerPostUpdate();
```  
  
### <a name="remarks"></a>备注  
 如果您启用使用 EnableAnimationTimerEventHandler 的计时器事件处理程序，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。  
  
##  <a name="a-nameonanimationtimerpreupdatea--canimationcontrolleronanimationtimerpreupdate"></a><a name="onanimationtimerpreupdate"></a>CAnimationController::OnAnimationTimerPreUpdate  
 在动画更新开始之前，由框架调用。  
  
```  
virtual void OnAnimationTimerPreUpdate();
```  
  
### <a name="remarks"></a>备注  
 如果您启用使用 EnableAnimationTimerEventHandler 的计时器事件处理程序，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。  
  
##  <a name="a-nameonanimationtimerrenderingtooslowa--canimationcontrolleronanimationtimerrenderingtooslow"></a><a name="onanimationtimerrenderingtooslow"></a>CAnimationController::OnAnimationTimerRenderingTooSlow  
 由框架调用，当动画的呈现帧速率低于最小的理想帧速率。  
  
```  
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```  
  
### <a name="parameters"></a>参数  
 `fps`  
 每秒帧数中的当前帧速率。  
  
### <a name="remarks"></a>备注  
 如果您启用使用 EnableAnimationTimerEventHandler 的计时器事件处理程序，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 通过调用 IUIAnimationTimer::SetFrameRateThreshold 指定最小的理想帧速率。  
  
##  <a name="a-nameonanimationvaluechangeda--canimationcontrolleronanimationvaluechanged"></a><a name="onanimationvaluechanged"></a>CAnimationController::OnAnimationValueChanged  
 当动画变量的值发生更改时由框架调用。  
  
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
 已更改的指针指向包含其值的动画对象的动画组。  
  
 `pObject`  
 指向一个包含其值已更改的动画变量的动画对象的指针。  
  
 `variable`  
 指向动画变量的指针。  
  
 `newValue`  
 指定新值。  
  
 `prevValue`  
 指定前一个值。  
  
### <a name="remarks"></a>备注  
 如果与为特定的动画变量或动画对象调用 EnableValueChangedEvent 启用动画变量的事件，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。  
  
##  <a name="a-nameonbeforeanimationstarta--canimationcontrolleronbeforeanimationstart"></a><a name="onbeforeanimationstart"></a>CAnimationController::OnBeforeAnimationStart  
 由框架调用正确计划动画之前。  
  
```  
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>参数  
 `pGroup`  
 一个指向其动画即将开始的动画组。  
  
### <a name="remarks"></a>备注  
 此调用将被路由到相关的 CWnd，并且可以在执行任何其他操作，在动画开始为指定的组前在派生类中重写。  
  
##  <a name="a-nameonhasprioritycancela--canimationcontrolleronhasprioritycancel"></a><a name="onhasprioritycancel"></a>CAnimationController::OnHasPriorityCancel  
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
 如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_CANCEL，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关冲突管理的详细信息，请阅读 Windows 动画 API 文档 (http://msdn.microsoft.com/library/dd371759(VS.85).aspx)。  
  
##  <a name="a-nameonhasprioritycompressa--canimationcontrolleronhasprioritycompress"></a><a name="onhasprioritycompress"></a>CAnimationController::OnHasPriorityCompress  
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
 如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_COMPRESS，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关冲突管理的详细信息，请阅读 Windows 动画 API 文档 (http://msdn.microsoft.com/library/dd371759(VS.85).aspx)。  
  
##  <a name="a-nameonhaspriorityconcludea--canimationcontrolleronhaspriorityconclude"></a><a name="onhaspriorityconclude"></a>CAnimationController::OnHasPriorityConclude  
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
 如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_CONCLUDE，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关冲突管理的详细信息，请阅读 Windows 动画 API 文档 (http://msdn.microsoft.com/library/dd371759(VS.85).aspx)。  
  
##  <a name="a-nameonhasprioritytrima--canimationcontrolleronhasprioritytrim"></a><a name="onhasprioritytrim"></a>CAnimationController::OnHasPriorityTrim  
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
 如果你使用 CAnimationController::EnablePriorityComparisonHandler 启用优先级比较事件，并指定 UI_ANIMATION_PHT_TRIM，则会调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。 有关冲突管理的详细信息，请阅读 Windows 动画 API 文档 (http://msdn.microsoft.com/library/dd371759(VS.85).aspx)。  
  
##  <a name="a-nameonstoryboardstatuschangeda--canimationcontrolleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>CAnimationController::OnStoryboardStatusChanged  
 演示图板状态更改时由框架调用。  
  
```  
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,  
    UI_ANIMATION_STORYBOARD_STATUS newStatus,  
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```  
  
### <a name="parameters"></a>参数  
 `pGroup`  
 已更改的动画组拥有对其状态的情节提要的指针。  
  
 `newStatus`  
 指定新状态。  
  
 `previousStatus`  
 指定的以前的状态。  
  
### <a name="remarks"></a>备注  
 如果您启用使用 CAnimationController::EnableStoryboardEventHandler 的情节提要事件，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。  
  
##  <a name="a-nameonstoryboardupdateda--canimationcontrolleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>CAnimationController::OnStoryboardUpdated  
 在演示图板更新时由框架调用。  
  
```  
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```  
  
### <a name="parameters"></a>参数  
 `pGroup`  
 指向一个组拥有该情节提要的指针。  
  
### <a name="remarks"></a>备注  
 如果您启用使用 CAnimationController::EnableStoryboardEventHandler 的情节提要事件，调用此方法。 它可以在派生类中重写以便执行特定于应用程序的操作。  
  
##  <a name="a-nameremoveallanimationgroupsa--canimationcontrollerremoveallanimationgroups"></a><a name="removeallanimationgroups"></a>CAnimationController::RemoveAllAnimationGroups  
 从动画控制器中删除所有动画组。  
  
```  
void RemoveAllAnimationGroups();
```  
  
### <a name="remarks"></a>备注  
 所有组都将被删除，其指针存储在应用程序级别中，如果必须使都其无效。 如果要删除的组的 CAnimationGroup::m_bAutodestroyAnimationObjects 为 TRUE，则将删除属于该组的所有动画对象;否则为父级动画控制器对其引用将设置为 NULL，并将它们添加到另一个控制器。  
  
##  <a name="a-nameremoveanimationgroupa--canimationcontrollerremoveanimationgroup"></a><a name="removeanimationgroup"></a>CAnimationController::RemoveAnimationGroup  
 从动画控制器中删除具有指定 ID 的动画组。  
  
```  
void RemoveAnimationGroup(UINT32 nGroupID);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定动画组 id。  
  
### <a name="remarks"></a>备注  
 此方法从内部的组列表中移除的动画组并将其删除，因此如果存储一个指向该动画组时，它必须使其无效。 如果 CAnimationGroup::m_bAutodestroyAnimationObjects 为 TRUE，则将删除属于该组的所有动画对象;否则为父级动画控制器对其引用将设置为 NULL，并将它们添加到另一个控制器。  
  
##  <a name="a-nameremoveanimationobjecta--canimationcontrollerremoveanimationobject"></a><a name="removeanimationobject"></a>CAnimationController::RemoveAnimationObject  
 从动画控制器中删除的动画对象。  
  
```  
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,  
    BOOL bNoDelete = FALSE);
```  
  
### <a name="parameters"></a>参数  
 `pObject`  
 指向动画对象的指针。  
  
 `bNoDelete`  
 如果此参数为 TRUE 时删除将不删除该对象。  
  
### <a name="remarks"></a>备注  
 从动画控制器和动画组中删除的动画对象。 如果某个特定对象应不进行动画处理，或者如果您需要将对象移动到另一个动画控制器，则调用此函数。 在最后一个事例 bNoDelete 必须为 TRUE。  
  
##  <a name="a-nameremovetransitionsa--canimationcontrollerremovetransitions"></a><a name="removetransitions"></a>CAnimationController::RemoveTransitions  
 从属于指定组的动画对象中删除转换。  
  
```  
void RemoveTransitions(UINT32 nGroupID);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定组的 id。  
  
### <a name="remarks"></a>备注  
 组中循环访问其动画对象，并为每个动画对象调用 ClearTransitions(FALSE)。 已安排动画后，将由框架调用此方法。  
  
##  <a name="a-nameschedulegroupa--canimationcontrollerschedulegroup"></a><a name="schedulegroup"></a>CAnimationController::ScheduleGroup  
 安排动画。  
  
```  
BOOL ScheduleGroup(
    UINT32 nGroupID,  
    UI_ANIMATION_SECONDS time = 0.0);
```  
  
### <a name="parameters"></a>参数  
 `nGroupID`  
 指定动画组 ID 来计划。  
  
 `time`  
 指定计划的时间。  
  
### <a name="return-value"></a>返回值  
 如果已成功安排动画，则为 TRUE。 如果尚未创建情节提要，或发生其他错误，则为 FALSE。  
  
### <a name="remarks"></a>备注  
 您必须设置为 FALSE 之前 ScheduleGroup 参数 bScheduleNow 调用 AnimateGroup。 您可以指定从 IUIAnimationTimer::GetTime 获取所需的动画的时间。 如果时间参数为 0.0，动画计划为当前时间。  
  
##  <a name="a-namesetrelatedwnda--canimationcontrollersetrelatedwnd"></a><a name="setrelatedwnd"></a>CAnimationController::SetRelatedWnd  
 建立动画控制器和窗口之间的关系。  
  
```  
void SetRelatedWnd(CWnd* pWnd);
```  
  
### <a name="parameters"></a>参数  
 `pWnd`  
 指向要设置的窗口对象的指针。  
  
### <a name="remarks"></a>备注  
 如果设置相关的 CWnd 对象，该动画控制器都会自动更新 （发送 WM_PAINT 消息） 动画管理器的状态已更改或计时器后更新事件发生时。  
  
##  <a name="a-nameupdateanimationmanagera--canimationcontrollerupdateanimationmanager"></a><a name="updateanimationmanager"></a>CAnimationController::UpdateAnimationManager  
 指示动画管理器，以更新所有动画变量的值。  
  
```  
virtual void UpdateAnimationManager();
```  
  
### <a name="remarks"></a>备注  
 调用此方法将推进动画管理器为当前时间、 根据需要更改情节提要的状态和所有动画变量都更新到适当插入值。 此方法在内部调用 IUIAnimationTimer::GetTime(timeNow) 和 IUIAnimationManager::Update(timeNow)。 重写此方法在派生类以自定义此行为。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

