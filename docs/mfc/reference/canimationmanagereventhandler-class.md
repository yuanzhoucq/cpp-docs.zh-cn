---
title: CAnimationManagerEventHandler 类
ms.date: 11/04/2016
f1_keywords:
- CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::OnManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationManagerEventHandler [MFC], CAnimationManagerEventHandler
- CAnimationManagerEventHandler [MFC], CreateInstance
- CAnimationManagerEventHandler [MFC], OnManagerStatusChanged
- CAnimationManagerEventHandler [MFC], SetAnimationController
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
ms.openlocfilehash: a4e97c2a1188071b5bde0781630d0dfe52e8a72f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369724"
---
# <a name="canimationmanagereventhandler-class"></a>CAnimationManagerEventHandler 类

实现回调，它在动画管理器状态更改时由动画 API 调用。

## <a name="syntax"></a>语法

```
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[动画管理器事件处理程序：：动画管理器事件处理程序](#canimationmanagereventhandler)|构造 `CAnimationManagerEventHandler` 对象。|

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[C动画管理器事件处理程序：：创建实例](#createinstance)|创建`CAnimationManagerEventHandler`对象的实例。|
|[C动画管理器操作器：：在管理器状态更改](#onmanagerstatuschanged)|当动画管理器的状态已更改时调用。 （重写 `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`。）|
|[C动画管理器处理程序：：设置动画控制器](#setanimationcontroller)|存储指向动画控制器的指针以路由事件。|

## <a name="remarks"></a>备注

此事件处理程序创建并传递给 IUIAnimationManager：：setManagerEventHandler 方法，当您调用 C动画控制器：：启用动画管理器事件时。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CUIAnimationCallbackBase`

`CUIAnimationManagerEventHandlerBase`

`CAnimationManagerEventHandler`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

## <a name="canimationmanagereventhandlercanimationmanagereventhandler"></a><a name="canimationmanagereventhandler"></a>动画管理器事件处理程序：：动画管理器事件处理程序

需要 Visual Studio 2010 SP1。

构造 CAnimationManager事件处理程序对象。

```
CAnimationManagerEventHandler();
```

## <a name="canimationmanagereventhandlercreateinstance"></a><a name="createinstance"></a>C动画管理器事件处理程序：：创建实例

需要 Visual Studio 2010 SP1。

创建 CAnimationManager事件处理程序对象的实例。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```

### <a name="parameters"></a>参数

*动画控制器*<br/>
指向动画控制器的指针，该控制器将接收事件。

*ppManagerEventHandler*<br/>
输出。 如果该方法成功，它包含指向 COM 对象的指针，该指针将处理动画管理器的状态更新。

### <a name="return-value"></a>返回值

如果该方法成功，则它会返回 S_OK。 否则，它将返回一个 HRESULT 错误代码。

## <a name="canimationmanagereventhandleronmanagerstatuschanged"></a><a name="onmanagerstatuschanged"></a>C动画管理器操作器：：在管理器状态更改

需要 Visual Studio 2010 SP1。

当动画管理器的状态已更改时调用。

```
IFACEMETHOD(OnManagerStatusChanged)(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>参数

*新状态*<br/>
新状态。

*上一个状态*<br/>
上一个状态。

### <a name="return-value"></a>返回值

当前实现始终返回S_OK;

## <a name="canimationmanagereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>C动画管理器处理程序：：设置动画控制器

需要 Visual Studio 2010 SP1。

存储指向动画控制器的指针以路由事件。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>参数

*动画控制器*<br/>
指向动画控制器的指针，该控制器将接收事件。

## <a name="see-also"></a>另请参阅

[类](../../mfc/reference/mfc-classes.md)
