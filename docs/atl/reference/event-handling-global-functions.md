---
title: 事件处理全局函数
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: f2f8269dcf0f59a5d0794d3f16d4c4f85d8841ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330135"
---
# <a name="event-handling-global-functions"></a>事件处理全局函数

此函数提供事件处理程序。

> [!IMPORTANT]
> 下表中列出的函数不能在 Windows 运行时中执行的应用程序中使用。

|||
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|等待对象发出信号，同时根据需要调度窗口消息。|

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="atlwaitwithmessageloop"></a><a name="atlwaitwithmessageloop"></a>AtlWait与消息循环

等待发出对象信号，同时根据需要调度窗口消息。

> [!IMPORTANT]
> 此函数不能在 Windows 运行时中执行的应用程序中使用。

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>参数

*hEvent*<br/>
[在]要等待的对象的句柄。

### <a name="return-value"></a>返回值

如果对象已发出信号，则返回 TRUE。

### <a name="remarks"></a>备注

如果要等待对象的事件发生并收到通知，但允许在等待时调度窗口消息，则此功能非常有用。

## <a name="see-also"></a>另请参阅

[函数](../../atl/reference/atl-functions.md)
