---
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: aa044ef88ba3c872c2652cd774ac50024e52c68c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492313"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler`由消息映射中的 MESSAGE_HANDLER 宏的第二个参数标识的函数的名称。

## <a name="syntax"></a>语法

```
LRESULT MessageHandler(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>参数

*uMsg*<br/>
指定消息。

*wParam*<br/>
其他特定于消息的信息。

*lParam*<br/>
其他特定于消息的信息。

*bHandled*<br/>
消息映射在调用之前`MessageHandler`将 bHandled 设置为 TRUE。 如果`MessageHandler`未完全处理消息, 则应将*bHandled*设置为 FALSE, 以指示消息需要进一步处理。

## <a name="return-value"></a>返回值

消息处理的结果。 如果成功, 则为0。

## <a name="remarks"></a>备注

有关在消息映射中使用此消息处理程序的示例, 请参阅[MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler)。

## <a name="see-also"></a>请参阅

[实现窗口](../atl/implementing-a-window.md)<br/>
[消息映射](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
