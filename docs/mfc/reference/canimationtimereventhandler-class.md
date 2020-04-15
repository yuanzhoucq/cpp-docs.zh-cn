---
title: CAnimationTimerEventHandler 类
ms.date: 11/04/2016
f1_keywords:
- CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationTimerEventHandler [MFC], CreateInstance
- CAnimationTimerEventHandler [MFC], OnPostUpdate
- CAnimationTimerEventHandler [MFC], OnPreUpdate
- CAnimationTimerEventHandler [MFC], OnRenderingTooSlow
- CAnimationTimerEventHandler [MFC], SetAnimationController
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
ms.openlocfilehash: 72b6e5d8d9d4823795a1fb053c5f2374cb80fba4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320015"
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
|[动画计时器事件处理程序：：创建实例](#createinstance)|创建回调实例`CAnimationTimerEventHandler`。|
|[动画计时器事件处理程序：：在发布更新](#onpostupdate)|处理动画更新完成后发生的事件。 （重写 `CUIAnimationTimerEventHandlerBase::OnPostUpdate`。）|
|[动画计时器事件处理程序：：打开预更新](#onpreupdate)|处理动画更新开始之前发生的事件。 （重写 `CUIAnimationTimerEventHandlerBase::OnPreUpdate`。）|
|[动画计时器事件处理程序：：打开渲染速度](#onrenderingtooslow)|处理动画渲染帧速率低于最低理想帧速率时发生的事件。 （重写 `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`。）|
|[动画计时器事件处理程序：：设置动画控制器](#setanimationcontroller)|存储指向动画控制器的指针以路由事件。|

## <a name="remarks"></a>备注

此事件处理程序被创建并传递给 IUIAnimationTimer：：当您调用 C动画控制器：：启用动画TimerEventHandler时，设置TimerEventHandler。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CUIAnimationCallbackBase`

`CUIAnimationTimerEventHandlerBase`

`CAnimationTimerEventHandler`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="canimationtimereventhandlercreateinstance"></a><a name="createinstance"></a>动画计时器事件处理程序：：创建实例

创建 CAnimationTimer事件处理程序回调的实例。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```

### <a name="parameters"></a>参数

*动画控制器*<br/>
指向动画控制器的指针，该控制器将接收事件。

*ppTimerEventHandler*

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="canimationtimereventhandleronpostupdate"></a><a name="onpostupdate"></a>动画计时器事件处理程序：：在发布更新

处理动画更新完成后发生的事件。

```
IFACEMETHOD(OnPostUpdate)();
```

### <a name="return-value"></a>返回值

如果方法成功，S_OK;否则E_FAIL。

## <a name="canimationtimereventhandleronpreupdate"></a><a name="onpreupdate"></a>动画计时器事件处理程序：：打开预更新

处理动画更新开始之前发生的事件。

```
IFACEMETHOD(OnPreUpdate)();
```

### <a name="return-value"></a>返回值

如果方法成功，S_OK;否则E_FAIL。

## <a name="canimationtimereventhandleronrenderingtooslow"></a><a name="onrenderingtooslow"></a>动画计时器事件处理程序：：打开渲染速度

处理动画渲染帧速率低于最低理想帧速率时发生的事件。

```
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```

### <a name="parameters"></a>参数

*Fps*

### <a name="return-value"></a>返回值

如果方法成功，S_OK;否则E_FAIL。

## <a name="canimationtimereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>动画计时器事件处理程序：：设置动画控制器

存储指向动画控制器的指针以路由事件。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>参数

*动画控制器*<br/>
指向动画控制器的指针，该控制器将接收事件。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
