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
ms.openlocfilehash: bd13ba4d0dd60f65372b2c1f51d70d338566301e
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916258"
---
# <a name="canimationmanagereventhandler-class"></a>CAnimationManagerEventHandler 类

实现回调，它在动画管理器状态更改时由动画 API 调用。

## <a name="syntax"></a>语法

```
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;
```

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|描述|
|----------|-----------------|
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](#canimationmanagereventhandler)|构造 `CAnimationManagerEventHandler` 对象。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[CAnimationManagerEventHandler::CreateInstance](#createinstance)|创建对象的`CAnimationManagerEventHandler`实例。|
|[CAnimationManagerEventHandler::OnManagerStatusChanged](#onmanagerstatuschanged)|动画管理器状态更改时调用。 （重写 `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`。）|
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|存储指向用于路由事件的动画控制器的指针。|

## <a name="remarks"></a>备注

当你调用 CAnimationController:: EnableAnimationManagerEvent 时, 将创建此事件处理程序并将其传递给 IUIAnimationManager:: SetManagerEventHandler 方法。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CUIAnimationCallbackBase`

`CUIAnimationManagerEventHandlerBase`

`CAnimationManagerEventHandler`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="canimationmanagereventhandler"></a>CAnimationManagerEventHandler:: CAnimationManagerEventHandler

需要 Visual Studio 2010 SP1。

构造 CAnimationManagerEventHandler 对象。

```
CAnimationManagerEventHandler();
```

##  <a name="createinstance"></a>CAnimationManagerEventHandler:: CreateInstance

需要 Visual Studio 2010 SP1。

创建 CAnimationManagerEventHandler 对象的实例。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```

### <a name="parameters"></a>参数

*pAnimationController*<br/>
指向将接收事件的动画控制器的指针。

*ppManagerEventHandler*<br/>
输出. 如果该方法成功, 则它包含指向 COM 对象的指针, 该对象将处理动画管理器的状态更新。

### <a name="return-value"></a>返回值

如果该方法成功, 则返回 S_OK。 否则, 它将返回 HRESULT 错误代码。

##  <a name="onmanagerstatuschanged"></a>CAnimationManagerEventHandler:: OnManagerStatusChanged

需要 Visual Studio 2010 SP1。

动画管理器状态更改时调用。

```
IFACEMETHOD(OnManagerStatusChanged)(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>参数

*newStatus*<br/>
新状态。

*previousStatus*<br/>
以前的状态。

### <a name="return-value"></a>返回值

当前实现始终返回 S_OK;

##  <a name="setanimationcontroller"></a>  CAnimationManagerEventHandler::SetAnimationController

需要 Visual Studio 2010 SP1。

存储指向用于路由事件的动画控制器的指针。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>参数

*pAnimationController*<br/>
指向将接收事件的动画控制器的指针。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
