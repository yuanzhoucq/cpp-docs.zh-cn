---
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageHandler
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: deb217e2f889d30ab5c4caa7d9812d5e612dcb62
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57299343"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler` 是由消息映射中的 MESSAGE_HANDLER 宏的第二个参数标识的名称。

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
指定的消息。

*wParam*<br/>
其他特定于消息的信息。

*lParam*<br/>
其他特定于消息的信息。

*bHandled*<br/>
消息映射集*bHandled*为 TRUE，然后才能`MessageHandler`调用。 如果`MessageHandler`不完全处理该消息，应设置*bHandled*为 FALSE 以指示该消息需要进一步处理。

## <a name="return-value"></a>返回值

消息处理的结果。 如果成功，则为 0。

## <a name="remarks"></a>备注

消息映射中使用此消息处理程序的示例，请参阅[MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler)。

## <a name="see-also"></a>请参阅

[实现窗口](../atl/implementing-a-window.md)<br/>
[消息映射](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)
