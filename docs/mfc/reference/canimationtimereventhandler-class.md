---
title: CAnimationTimerEventHandler 类 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CAnimationTimerEventHandler [MFC], CreateInstance
- CAnimationTimerEventHandler [MFC], OnPostUpdate
- CAnimationTimerEventHandler [MFC], OnPreUpdate
- CAnimationTimerEventHandler [MFC], OnRenderingTooSlow
- CAnimationTimerEventHandler [MFC], SetAnimationController
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fc0fe5a59a5efedc00850da03be84bb212d4a51f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352094"
---
# <a name="canimationtimereventhandler-class"></a>CAnimationTimerEventHandler 类
实现回调，它在计时事件发生时由动画 API 调用。  
  
## <a name="syntax"></a>语法  
  
```  
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;  
```  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[CAnimationTimerEventHandler::CreateInstance](#createinstance)|创建的实例`CAnimationTimerEventHandler`回调。|  
|[CAnimationTimerEventHandler::OnPostUpdate](#onpostupdate)|处理后动画更新完成后会发生的事件。 （重写 `CUIAnimationTimerEventHandlerBase::OnPostUpdate`。）|  
|[CAnimationTimerEventHandler::OnPreUpdate](#onpreupdate)|处理发生的动画更新开始之前的事件。 （重写 `CUIAnimationTimerEventHandlerBase::OnPreUpdate`。）|  
|[CAnimationTimerEventHandler::OnRenderingTooSlow](#onrenderingtooslow)|处理动画呈现帧速率低于最小的理想帧速率时发生的事件。 （重写 `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`。）|  
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|将存储到动画控制器路由事件的指针。|  
  
## <a name="remarks"></a>备注  
 此事件处理程序是创建并传递给 IUIAnimationTimer::SetTimerEventHandler，当您调用 CAnimationController::EnableAnimationTimerEventHandler。  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `CUIAnimationCallbackBase`  
  
 `CUIAnimationTimerEventHandlerBase`  
  
 `CAnimationTimerEventHandler`  
  
## <a name="requirements"></a>要求  
 **标头：** afxanimationcontroller.h  
  
##  <a name="createinstance"></a>  CAnimationTimerEventHandler::CreateInstance  
 创建 CAnimationTimerEventHandler 回调的实例。  
  
```  
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,  
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```  
  
### <a name="parameters"></a>参数  
 `pAnimationController`  
 指向动画控制器，它将接收此事件的指针。  
  
 `ppTimerEventHandler`  
  
### <a name="return-value"></a>返回值  
 如果该方法成功，则返回，则为 S_OK。 否则，它返回一个 HRESULT 错误代码。  
  
##  <a name="onpostupdate"></a>  CAnimationTimerEventHandler::OnPostUpdate  
 处理后动画更新完成后会发生的事件。  
  
```  
IFACEMETHOD(OnPostUpdate)();
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功; 则为 S_OK否则为 E_FAIL。  
  
##  <a name="onpreupdate"></a>  CAnimationTimerEventHandler::OnPreUpdate  
 处理发生的动画更新开始之前的事件。  
  
```  
IFACEMETHOD(OnPreUpdate)();
```  
  
### <a name="return-value"></a>返回值  
 如果该方法成功; 则为 S_OK否则为 E_FAIL。  
  
##  <a name="onrenderingtooslow"></a>  CAnimationTimerEventHandler::OnRenderingTooSlow  
 处理动画呈现帧速率低于最小的理想帧速率时发生的事件。  
  
```  
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```  
  
### <a name="parameters"></a>参数  
 `fps`  
  
### <a name="return-value"></a>返回值  
 如果该方法成功; 则为 S_OK否则为 E_FAIL。  
  
##  <a name="setanimationcontroller"></a>  CAnimationTimerEventHandler::SetAnimationController  
 将存储到动画控制器路由事件的指针。  
  
```  
void SetAnimationController(CAnimationController* pAnimationController);
```  
  
### <a name="parameters"></a>参数  
 `pAnimationController`  
 指向动画控制器，它将接收此事件的指针。  
  
## <a name="see-also"></a>请参阅  
 [类](../../mfc/reference/mfc-classes.md)
