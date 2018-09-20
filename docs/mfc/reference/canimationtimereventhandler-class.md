---
title: CAnimationTimerEventHandler 类 |Microsoft Docs
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
ms.openlocfilehash: ad48c372043c06c2bc3a64537734a30d79e81a50
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46394993"
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
|[CAnimationTimerEventHandler::OnPostUpdate](#onpostupdate)|处理的动画更新完成后发生的事件。 （重写 `CUIAnimationTimerEventHandlerBase::OnPostUpdate`。）|
|[CAnimationTimerEventHandler::OnPreUpdate](#onpreupdate)|处理动画更新开始之前发生的事件。 （重写 `CUIAnimationTimerEventHandlerBase::OnPreUpdate`。）|
|[CAnimationTimerEventHandler::OnRenderingTooSlow](#onrenderingtooslow)|处理动画呈现帧速率低于最小的理想帧速率时发生的事件。 （重写 `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`。）|
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|存储指向动画控制器的路由事件。|

## <a name="remarks"></a>备注

创建并传递给 IUIAnimationTimer::SetTimerEventHandler 调用 CAnimationController::EnableAnimationTimerEventHandler 时此事件处理程序。

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

*pAnimationController*<br/>
一个指向动画控制器，它将接收事件。

*ppTimerEventHandler*

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。

##  <a name="onpostupdate"></a>  CAnimationTimerEventHandler::OnPostUpdate

处理的动画更新完成后发生的事件。

```
IFACEMETHOD(OnPostUpdate)();
```

### <a name="return-value"></a>返回值

如果方法成功，则为 S_OK否则为 E_FAIL。

##  <a name="onpreupdate"></a>  CAnimationTimerEventHandler::OnPreUpdate

处理动画更新开始之前发生的事件。

```
IFACEMETHOD(OnPreUpdate)();
```

### <a name="return-value"></a>返回值

如果方法成功，则为 S_OK否则为 E_FAIL。

##  <a name="onrenderingtooslow"></a>  CAnimationTimerEventHandler::OnRenderingTooSlow

处理动画呈现帧速率低于最小的理想帧速率时发生的事件。

```
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```

### <a name="parameters"></a>参数

*每秒帧数*

### <a name="return-value"></a>返回值

如果方法成功，则为 S_OK否则为 E_FAIL。

##  <a name="setanimationcontroller"></a>  CAnimationTimerEventHandler::SetAnimationController

存储指向动画控制器的路由事件。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>参数

*pAnimationController*<br/>
一个指向动画控制器，它将接收事件。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
