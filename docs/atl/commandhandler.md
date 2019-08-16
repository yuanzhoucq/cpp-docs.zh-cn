---
title: CommandHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
ms.openlocfilehash: 99a95228f6036e5f391395be367cdef39ca3dc3b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492459"
---
# <a name="commandhandler"></a>CommandHandler

`CommandHandler`由消息映射中的 COMMAND_HANDLER 宏的第三个参数标识的函数。

## <a name="syntax"></a>语法

```cpp
LRESULT CommandHandler(
    WORD wNotifyCode,
    WORD wID,
    HWND hWndCtl,
    BOOL& bHandled);
```

#### <a name="parameters"></a>参数

*wNotifyCode*<br/>
通知代码。

*wID*<br/>
菜单项、控件或快捷键的标识符。

*hWndCtl*<br/>
窗口控件的句柄。

*bHandled*<br/>
消息映射在调用之前`CommandHandler`将 bHandled 设置为 TRUE。 如果`CommandHandler`未完全处理消息, 则应将*bHandled*设置为 FALSE, 以指示消息需要进一步处理。

## <a name="return-value"></a>返回值

消息处理的结果。 如果成功, 则为0。

## <a name="remarks"></a>备注

有关在消息映射中使用此消息处理程序的示例, 请参阅[COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler)。

## <a name="see-also"></a>请参阅

[实现窗口](../atl/implementing-a-window.md)<br/>
[消息映射](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
