---
title: "CAnimationTimerEventHandler 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::SetAnimationController
dev_langs:
- C++
helpviewer_keywords:
- CAnimationTimerEventHandler class
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 5412c215caf85440e923e8a083ed310f8960849a
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="canimationtimereventhandler-class"></a>CAnimationTimerEventHandler 类
实现回调，它在计时事件发生时由动画 API 调用。  
  
## <a name="syntax"></a>语法  
  
```  
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|说明|  
|----------|-----------------|  
|[CAnimationTimerEventHandler::CreateInstance](#createinstance)|创建的一个实例`CAnimationTimerEventHandler`回调。|  
|[CAnimationTimerEventHandler::OnPostUpdate](#onpostupdate)|处理动画更新完成之后发生的事件。 （重写 `CUIAnimationTimerEventHandlerBase::OnPostUpdate`。）|  
|[CAnimationTimerEventHandler::OnPreUpdate](#onpreupdate)|处理动画更新开始之前发生的事件。 （重写 `CUIAnimationTimerEventHandlerBase::OnPreUpdate`。）|  
|[CAnimationTimerEventHandler::OnRenderingTooSlow](#onrenderingtooslow)|处理一个动画的呈现帧速率低于最小的理想帧速率时发生的事件。 （重写 `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`。）|  
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|存储事件路由的动画控制器的指针。|  
  
## <a name="remarks"></a>备注  
 此事件处理程序被创建并传递到 IUIAnimationTimer::SetTimerEventHandler，当您调用 CAnimationController::EnableAnimationTimerEventHandler。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationTimerEventHandlerBase`  
  
 `CAnimationTimerEventHandler`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="createinstance"></a>CAnimationTimerEventHandler::CreateInstance  
 创建 CAnimationTimerEventHandler 回调的实例。  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```  
  
### <a name="parameters"></a>参数  
 `pAnimationController`  
 一个指向动画控制器，它将接收此事件。  
  
 `ppTimerEventHandler`  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
##  <a name="onpostupdate"></a>CAnimationTimerEventHandler::OnPostUpdate  
 处理动画更新完成之后发生的事件。  
  
```  
IFACEMETHOD(OnPostUpdate)();
```  
  
### <a name="return-value"></a>返回值  
 如果方法成功，则为 S_OK否则为 E_FAIL。  
  
##  <a name="onpreupdate"></a>CAnimationTimerEventHandler::OnPreUpdate  
 处理动画更新开始之前发生的事件。  
  
```  
IFACEMETHOD(OnPreUpdate)();
```  
  
### <a name="return-value"></a>返回值  
 如果方法成功，则为 S_OK否则为 E_FAIL。  
  
##  <a name="onrenderingtooslow"></a>CAnimationTimerEventHandler::OnRenderingTooSlow  
 处理一个动画的呈现帧速率低于最小的理想帧速率时发生的事件。  
  
```  
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```  
  
### <a name="parameters"></a>参数  
 `fps`  
  
### <a name="return-value"></a>返回值  
 如果方法成功，则为 S_OK否则为 E_FAIL。  
  
##  <a name="setanimationcontroller"></a>CAnimationTimerEventHandler::SetAnimationController  
 存储事件路由的动画控制器的指针。  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>参数  
 `pAnimationController`  
 一个指向动画控制器，它将接收此事件。  
  
## <a name="see-also"></a>另请参阅  
 [类](../../mfc/reference/mfc-classes.md)

