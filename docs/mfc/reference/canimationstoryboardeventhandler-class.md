---
title: CAnimationStoryboardEventHandler 类
ms.date: 11/04/2016
f1_keywords:
- CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationStoryboardEventHandler [MFC], CAnimationStoryboardEventHandler
- CAnimationStoryboardEventHandler [MFC], CreateInstance
- CAnimationStoryboardEventHandler [MFC], OnStoryboardStatusChanged
- CAnimationStoryboardEventHandler [MFC], OnStoryboardUpdated
- CAnimationStoryboardEventHandler [MFC], SetAnimationController
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
ms.openlocfilehash: 36b8b524591693775403d66fdc1f0754aaf67778
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365002"
---
# <a name="canimationstoryboardeventhandler-class"></a>CAnimationStoryboardEventHandler 类

实现回调，它在演示图板状态更改时或演示图板更新时由动画 API 调用。

## <a name="syntax"></a>语法

```
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[动画故事板事件处理程序：：动画故事板事件处理程序](#canimationstoryboardeventhandler)|构造 `CAnimationStoryboardEventHandler` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[动画故事板事件处理程序：：创建实例](#createinstance)|创建回调实例`CAnimationStoryboardEventHandler`。|
|[C动画故事板事件处理程序：：在故事板状态更改](#onstoryboardstatuschanged)|处理`OnStoryboardStatusChanged`情节提要的状态更改时发生的事件（覆盖`CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`. ）|
|[C动画故事板事件处理程序：：在故事板上更新](#onstoryboardupdated)|处理`OnStoryboardUpdated`更新情节提要时发生的事件（覆盖`CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`.）|
|[动画故事板事件处理程序：：设置动画控制器](#setanimationcontroller)|存储指向动画控制器的指针以路由事件。|

## <a name="remarks"></a>备注

当您调用`CAnimationController::EnableStoryboardEventHandler`时，将创建此`IUIAnimationStoryboard::SetStoryboardEventHandler`事件处理程序并传递给方法。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CUIAnimationCallbackBase`

`CUIAnimationStoryboardEventHandlerBase`

`CAnimationStoryboardEventHandler`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="canimationstoryboardeventhandlercanimationstoryboardeventhandler"></a><a name="canimationstoryboardeventhandler"></a>动画故事板事件处理程序：：动画故事板事件处理程序

构造 CAnimationStoryboard 事件处理程序对象。

```
CAnimationStoryboardEventHandler();
```

## <a name="canimationstoryboardeventhandlercreateinstance"></a><a name="createinstance"></a>动画故事板事件处理程序：：创建实例

创建 CAnimationStoryboard 事件处理程序回调的实例。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationStoryboardEventHandler** ppHandler);
```

### <a name="parameters"></a>参数

*动画控制器*<br/>
指向动画控制器的指针，该控制器将接收事件。

*普汉德勒*

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="canimationstoryboardeventhandleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>C动画故事板事件处理程序：：在故事板状态更改

处理故事板状态更改事件，这些事件发生在情节提要的状态更改时

```
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>参数

*脚本*<br/>
指向状态已更改的情节提要的指针。

*新状态*<br/>
指定新的情节提要状态。

*上一个状态*<br/>
指定以前的情节提要状态。

### <a name="return-value"></a>返回值

如果方法成功，S_OK;否则E_FAIL。

## <a name="canimationstoryboardeventhandleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>C动画故事板事件处理程序：：在故事板上更新

处理更新情节提要时发生的更新事件

```
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```

### <a name="parameters"></a>参数

*脚本*<br/>
指向故事板的指针，已更新。

### <a name="return-value"></a>返回值

如果方法成功，S_OK;否则E_FAIL。

## <a name="canimationstoryboardeventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>动画故事板事件处理程序：：设置动画控制器

存储指向动画控制器的指针以路由事件。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>参数

*动画控制器*<br/>
指向动画控制器的指针，该控制器将接收事件。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
