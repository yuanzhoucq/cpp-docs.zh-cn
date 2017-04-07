---
title: "CAnimationStoryboardEventHandler 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationStoryboardEventHandler class
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: bda8b0c941fd833bf821b563f4ca59cab9598cb8
ms.lasthandoff: 02/24/2017

---
# <a name="canimationstoryboardeventhandler-class"></a>CAnimationStoryboardEventHandler 类
实现回调，它在演示图板状态更改时或演示图板更新时由动画 API 调用。  
  
## <a name="syntax"></a>语法  
  
```  
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](#canimationstoryboardeventhandler)|构造 `CAnimationStoryboardEventHandler` 对象。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationStoryboardEventHandler::CreateInstance](#createinstance)|创建的一个实例`CAnimationStoryboardEventHandler`回调。|  
|[CAnimationStoryboardEventHandler::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|处理`OnStoryboardStatusChanged`演示图板的状态更改时发生的事件 (重写`CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`。)|  
|[CAnimationStoryboardEventHandler::OnStoryboardUpdated](#onstoryboardupdated)|处理`OnStoryboardUpdated`演示图板更新时可能发生的事件 (重写`CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`。)|  
|[CAnimationStoryboardEventHandler::SetAnimationController](#setanimationcontroller)|存储事件路由的动画控制器的指针。|  
  
## <a name="remarks"></a>备注  
 此事件处理程序被创建并传递到`IUIAnimationStoryboard::SetStoryboardEventHandler`方法中，当您调用`CAnimationController::EnableStoryboardEventHandler`。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationStoryboardEventHandlerBase`  
  
 `CAnimationStoryboardEventHandler`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="canimationstoryboardeventhandler"></a>CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler  
 构造 CAnimationStoryboardEventHandler 对象。  
  
```  
CAnimationStoryboardEventHandler();
```  
  
##  <a name="createinstance"></a>CAnimationStoryboardEventHandler::CreateInstance  
 创建 CAnimationStoryboardEventHandler 回调的实例。  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationStoryboardEventHandler** ppHandler);
```  
  
### <a name="parameters"></a>参数  
 `pAnimationController`  
 一个指向动画控制器，它将接收此事件。  
  
 `ppHandler`  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
##  <a name="onstoryboardstatuschanged"></a>CAnimationStoryboardEventHandler::OnStoryboardStatusChanged  
 处理发生在演示图板的状态更改时的 OnStoryboardStatusChanged 事件  
  
```  
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```  
  
### <a name="parameters"></a>参数  
 `storyboard`  
 已更改其状态的情节提要的指针。  
  
 `newStatus`  
 指定新的演示图板状态。  
  
 `previousStatus`  
 指定以前的演示图板状态。  
  
### <a name="return-value"></a>返回值  
 如果方法成功，则为 S_OK否则为 E_FAIL。  
  
##  <a name="onstoryboardupdated"></a>CAnimationStoryboardEventHandler::OnStoryboardUpdated  
 演示图板更新时，则的句柄 OnStoryboardUpdated 事件  
  
```  
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```  
  
### <a name="parameters"></a>参数  
 `storyboard`  
 情节提要的指针，它已更新。  
  
### <a name="return-value"></a>返回值  
 如果方法成功，则为 S_OK否则为 E_FAIL。  
  
##  <a name="setanimationcontroller"></a>CAnimationStoryboardEventHandler::SetAnimationController  
 存储事件路由的动画控制器的指针。  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>参数  
 `pAnimationController`  
 一个指向动画控制器，它将接收此事件。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

