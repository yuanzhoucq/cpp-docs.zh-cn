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
ms.openlocfilehash: 6661da55d1091394cff9db4589bc05c721b5ab7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151214"
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
|[CAnimationManagerEventHandler::CreateInstance](#createinstance)|创建的实例`CAnimationManagerEventHandler`对象。|
|[CAnimationManagerEventHandler::OnManagerStatusChanged](#onmanagerstatuschanged)|动画管理器的状态发生更改时调用。 （重写 `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`。）|
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|存储指向动画控制器的路由事件。|

## <a name="remarks"></a>备注

创建此事件处理程序并将其传递给 IUIAnimationManager::SetManagerEventHandler 方法时调用 CAnimationController::EnableAnimationManagerEvent。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CUIAnimationCallbackBase`

`CUIAnimationManagerEventHandlerBase`

`CAnimationManagerEventHandler`

## <a name="requirements"></a>要求

**标头：** afxanimationcontroller.h

##  <a name="canimationmanagereventhandler"></a>  CAnimationManagerEventHandler::CAnimationManagerEventHandler

需要 Visual Studio 2010 SP1。

构造一个 CAnimationManagerEventHandler 对象。

```
CAnimationManagerEventHandler();
```

##  <a name="createinstance"></a>  CAnimationManagerEventHandler::CreateInstance

需要 Visual Studio 2010 SP1。

创建 CAnimationManagerEventHandler 对象的实例。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```

### <a name="parameters"></a>参数

*pAnimationController*<br/>
一个指向动画控制器，它将接收事件。

*ppManagerEventHandler*<br/>
输出。 如果该方法成功，则包含指向将处理状态更新动画管理器的 COM 对象的指针。

### <a name="return-value"></a>返回值

如果该方法成功，它会返回 S_OK。 否则，它返回一个 HRESULT 错误代码。

##  <a name="onmanagerstatuschanged"></a>  CAnimationManagerEventHandler::OnManagerStatusChanged

需要 Visual Studio 2010 SP1。

动画管理器的状态发生更改时调用。

```
IFACEMETHOD(OnManagerStatusChanged)(
  UI_ANIMATION_MANAGER_STATUS newStatus,
  UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>参数

*newStatus*<br/>
新的状态。

*previousStatus*<br/>
以前的状态。

### <a name="return-value"></a>返回值

当前实现始终返回 S_OK;

##  <a name="setanimationcontroller"></a>  CAnimationManagerEventHandler::SetAnimationController

需要 Visual Studio 2010 SP1。

存储指向动画控制器的路由事件。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>参数

*pAnimationController*<br/>
一个指向动画控制器，它将接收事件。

## <a name="see-also"></a>请参阅

[类](../../mfc/reference/mfc-classes.md)
