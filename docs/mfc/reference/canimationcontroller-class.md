---
title: "CAnimationController 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAnimationController"
  - "afxanimationcontroller/CAnimationController"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAnimationController 类"
ms.assetid: ed294c98-695e-40a6-b940-33ef1d40aa6b
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAnimationController 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

实现动画控制器，它为创建和管理动画提供了中央接口。  
  
## 语法  
  
```  
class CAnimationController : public CObject;  
```  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[CAnimationController::CAnimationController](../Topic/CAnimationController::CAnimationController.md)|构造动画控制器。|  
|[CAnimationController::~CAnimationController](../Topic/CAnimationController::~CAnimationController.md)|该析构函数。  当动画控制器对象被销毁时调用。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationController::AddAnimationObject](../Topic/CAnimationController::AddAnimationObject.md)|将动画对象添加到属于该动画控制器的组。|  
|[CAnimationController::AddKeyframeToGroup](../Topic/CAnimationController::AddKeyframeToGroup.md)|将关键帧添加到组。|  
|[CAnimationController::AnimateGroup](../Topic/CAnimationController::AnimateGroup.md)|准备用来运行动画的组，并可有选择地对其进行安排。|  
|[CAnimationController::CleanUpGroup](../Topic/CAnimationController::CleanUpGroup.md)|已重载。  由框架调用以在动画已计划好时清理组。|  
|[CAnimationController::CreateKeyframe](../Topic/CAnimationController::CreateKeyframe.md)|已重载。  创建取决于转换并将其添加到指定组的关键帧。|  
|[CAnimationController::EnableAnimationManagerEvent](../Topic/CAnimationController::EnableAnimationManagerEvent.md)|设置或释放在动画管理器的状态更改时调用的处理程序。|  
|[CAnimationController::EnableAnimationTimerEventHandler](../Topic/CAnimationController::EnableAnimationTimerEventHandler.md)|设置或释放计时事件处理程序和定时更新处理程序。|  
|[CAnimationController::EnablePriorityComparisonHandler](../Topic/CAnimationController::EnablePriorityComparisonHandler.md)|设置或释放要调用的优先级比较处理程序，以确定计划的情节提要是否可以取消、结束、剪裁或压缩。|  
|[CAnimationController::EnableStoryboardEventHandler](../Topic/CAnimationController::EnableStoryboardEventHandler.md)|设置或释放情节提要状态以及更新事件的处理程序。|  
|[CAnimationController::FindAnimationGroup](../Topic/CAnimationController::FindAnimationGroup.md)|已重载。  依据其情节提要查找动画组。|  
|[CAnimationController::FindAnimationObject](../Topic/CAnimationController::FindAnimationObject.md)|查找包含指定的动画变量的动画对象。|  
|[CAnimationController::GetKeyframeStoryboardStart](../Topic/CAnimationController::GetKeyframeStoryboardStart.md)|返回标志情节提要的开头的关键帧。|  
|[CAnimationController::GetUIAnimationManager](../Topic/CAnimationController::GetUIAnimationManager.md)|提供对封装 IUIAnimationManager 对象的访问权。|  
|[CAnimationController::GetUIAnimationTimer](../Topic/CAnimationController::GetUIAnimationTimer.md)|提供对封装 IUIAnimationTimer 对象的访问权。|  
|[CAnimationController::GetUITransitionFactory](../Topic/CAnimationController::GetUITransitionFactory.md)|指向 IUIAnimationTransitionFactory 接口的，或者如果创建转换库失败则为 NULL 的指针。|  
|[CAnimationController::GetUITransitionLibrary](../Topic/CAnimationController::GetUITransitionLibrary.md)|提供对封装 IUIAnimationTransitionLibrary 对象的访问权。|  
|[CAnimationController::IsAnimationInProgress](../Topic/CAnimationController::IsAnimationInProgress.md)|指示是否至少一个组在播放动画。|  
|[CAnimationController::IsValid](../Topic/CAnimationController::IsValid.md)|指示动画控制器是否有效。|  
|[CAnimationController::OnAnimationIntegerValueChanged](../Topic/CAnimationController::OnAnimationIntegerValueChanged.md)|由框架在动画变量的整数值更改后调用。|  
|[CAnimationController::OnAnimationManagerStatusChanged](../Topic/CAnimationController::OnAnimationManagerStatusChanged.md)|由框架调用以响应来自动画管理器的 StatusChanged 事件。|  
|[CAnimationController::OnAnimationTimerPostUpdate](../Topic/CAnimationController::OnAnimationTimerPostUpdate.md)|由框架在动画更新完成后调用。|  
|[CAnimationController::OnAnimationTimerPreUpdate](../Topic/CAnimationController::OnAnimationTimerPreUpdate.md)|由框架在动画更新开始之前调用。|  
|[CAnimationController::OnAnimationTimerRenderingTooSlow](../Topic/CAnimationController::OnAnimationTimerRenderingTooSlow.md)|当动画的呈现帧速率低于最小的理想帧速率时，由框架调用。|  
|[CAnimationController::OnAnimationValueChanged](../Topic/CAnimationController::OnAnimationValueChanged.md)|由框架在动画变量的值更改后调用。|  
|[CAnimationController::OnBeforeAnimationStart](../Topic/CAnimationController::OnBeforeAnimationStart.md)|由框架在该动画安排好之前调用。|  
|[CAnimationController::OnHasPriorityCancel](../Topic/CAnimationController::OnHasPriorityCancel.md)|由框架调用此方法来解决安排冲突。|  
|[CAnimationController::OnHasPriorityCompress](../Topic/CAnimationController::OnHasPriorityCompress.md)|由框架调用此方法来解决安排冲突。|  
|[CAnimationController::OnHasPriorityConclude](../Topic/CAnimationController::OnHasPriorityConclude.md)|由框架调用此方法来解决安排冲突。|  
|[CAnimationController::OnHasPriorityTrim](../Topic/CAnimationController::OnHasPriorityTrim.md)|由框架调用此方法来解决安排冲突。|  
|[CAnimationController::OnStoryboardStatusChanged](../Topic/CAnimationController::OnStoryboardStatusChanged.md)|由框架在情节提要状态更改后调用。|  
|[CAnimationController::OnStoryboardUpdated](../Topic/CAnimationController::OnStoryboardUpdated.md)|由框架在情节提要更新后调用。|  
|[CAnimationController::RemoveAllAnimationGroups](../Topic/CAnimationController::RemoveAllAnimationGroups.md)|从动画控制器中删除所有动画组。|  
|[CAnimationController::RemoveAnimationGroup](../Topic/CAnimationController::RemoveAnimationGroup.md)|从动画控制器中删除具有指定 ID 的动画组。|  
|[CAnimationController::RemoveAnimationObject](../Topic/CAnimationController::RemoveAnimationObject.md)|从动画控制器中删除动画对象。|  
|[CAnimationController::RemoveTransitions](../Topic/CAnimationController::RemoveTransitions.md)|从属于指定的组的动画对象中删除转换。|  
|[CAnimationController::ScheduleGroup](../Topic/CAnimationController::ScheduleGroup.md)|安排动画。|  
|[CAnimationController::SetRelatedWnd](../Topic/CAnimationController::SetRelatedWnd.md)|建立动画控制器和窗口之间的关系。|  
|[CAnimationController::UpdateAnimationManager](../Topic/CAnimationController::UpdateAnimationManager.md)|指引动画管理器更新所有动画变量的值。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[CAnimationController::CleanUpGroup](../Topic/CAnimationController::CleanUpGroup.md)|已重载。  清除该组的帮助器。|  
|[CAnimationController::OnAfterSchedule](../Topic/CAnimationController::OnAfterSchedule.md)|由框架在指定组的动画刚刚安排好时调用。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[CAnimationController::g\_KeyframeStoryboardStart](../Topic/CAnimationController::g_KeyframeStoryboardStart.md)|表示情节提要的开头的关键帧。|  
|[CAnimationController::m\_bIsValid](../Topic/CAnimationController::m_bIsValid.md)|指定动画控制器是否有效。  如果当前操作系统不支持 Windows 动画 API，则该成员会设置为 FALSE。|  
|[CAnimationController::m\_lstAnimationGroups](../Topic/CAnimationController::m_lstAnimationGroups.md)|属于此动画控制器的动画组列表。|  
|[CAnimationController::m\_pAnimationManager](../Topic/CAnimationController::m_pAnimationManager.md)|存储指向动画管理器 COM 对象的指针。|  
|[CAnimationController::m\_pAnimationTimer](../Topic/CAnimationController::m_pAnimationTimer.md)|存储指向动画计时器 COM 对象的指针。|  
|[CAnimationController::m\_pRelatedWnd](../Topic/CAnimationController::m_pRelatedWnd.md)|指向相关 CWnd 对象的指针，该指针可在动画管理器状态更改时或更新后事件发生时自动重新绘制。  可以为 NULL。|  
|[CAnimationController::m\_pTransitionFactory](../Topic/CAnimationController::m_pTransitionFactory.md)|存储指向转换工厂 COM 对象的指针。|  
|[CAnimationController::m\_pTransitionLibrary](../Topic/CAnimationController::m_pTransitionLibrary.md)|存储指向转换库 COM 对象的指针。|  
  
## 备注  
 CAnimationController 类是管理动画的关键类。  您可能会在应用程序中创建一个或多个动画控制器实例，并（可选）将动画控制器实例连接到使用 CAnimationController::SetRelatedWnd 的 CWnd 对象。  当动画管理器状态更改时或动画计时器已更新时，要自动将 WM\_PAINT 消息发送到相关的窗口，需要此连接。  如果您不启用此关系，则必须重绘手动显示动画的窗口。  为此，您可以从 CAnimationController 派生类，重写 OnAnimationManagerStatusChanged 和\/或 OnAnimationTimerPostUpdate，在必要时可使一个或多个窗口无效。  
  
## 继承层次结构  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CAnimationController](../../mfc/reference/canimationcontroller-class.md)  
  
## 要求  
 **标头：** afxanimationcontroller.h  
  
## 请参阅  
 [类](../../mfc/reference/mfc-classes.md)