---
title: NotifyHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
ms.openlocfilehash: d875a039b01b7458a1df46a2539cf5c68aa67e41
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915933"
---
# <a name="notifyhandler"></a>NotifyHandler

由消息映射中的 NOTIFY_HANDLER 宏的第三个参数标识的函数的名称。

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
包含通知代码和其他信息的[NMHDR](/windows/desktop/api/richedit/ns-richedit-nmhdr)结构的地址。 对于某些通知消息, 此参数指向结构作为其第一个成员的`NMHDR`更大结构。

*bHandled*<br/>
消息映射将*bHandled*设置为 TRUE, 然后调用*NotifyHandler* 。 如果*NotifyHandler*未完全处理消息, 则应将*BHandled*设置为**FALSE**以指示消息需要进一步处理。

## <a name="return-value"></a>返回值

消息处理的结果。 如果成功, 则为0。

## <a name="remarks"></a>备注

有关在消息映射中使用此消息处理程序的示例, 请参阅[NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler))。

## <a name="see-also"></a>请参阅

[实现窗口](../atl/implementing-a-window.md)<br/>
[消息映射](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)
