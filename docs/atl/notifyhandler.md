---
title: NotifyHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
ms.openlocfilehash: 292a1c6606585dc0694ee678ba8bc9b5fbc42681
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261441"
---
# <a name="notifyhandler"></a>NotifyHandler

消息映射中的 NOTIFY_HANDLER 宏的第三个参数标识的函数的名称。

## <a name="syntax"></a>语法

```cpp
LRESULT NotifyHandler(
    int idCtrl,
    LPNMHDR pnmh,
    BOOL& bHandled);
```

#### <a name="parameters"></a>参数

*idCtrl*<br/>
发送消息的控件的标识符。

*pnmh*<br/>
地址[NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr)结构，其中包含通知代码和其他信息。 对于某些通知消息，此参数指向具有较大结构`NMHDR`结构作为其第一个成员。

*bHandled*<br/>
消息映射集*bHandled*为 TRUE，然后才能*NotifyHandler*调用。 如果*NotifyHandler*不完全处理该消息，应设置*bHandled*到**FALSE**来指示该消息需要进一步处理。

## <a name="return-value"></a>返回值

消息处理的结果。 如果成功，则为 0。

## <a name="remarks"></a>备注

消息映射中使用此消息处理程序的示例，请参阅[NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler))。

## <a name="see-also"></a>请参阅

[实现窗口](../atl/implementing-a-window.md)<br/>
[消息映射](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)
