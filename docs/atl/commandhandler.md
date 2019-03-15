---
title: CommandHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
ms.openlocfilehash: 743be3e0bc9cc96fc6b22d0806d399ab5e160a3f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807603"
---
# <a name="commandhandler"></a>CommandHandler

`CommandHandler` 函数是通过消息映射中的 COMMAND_HANDLER 宏的第三个参数标识。

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
菜单项、 控件或加速器的标识符。

*hWndCtl*<br/>
窗口控件的句柄。

*bHandled*<br/>
消息映射集*bHandled*为 TRUE，然后才能`CommandHandler`调用。 如果`CommandHandler`不完全处理该消息，应设置*bHandled*为 FALSE 以指示该消息需要进一步处理。

## <a name="return-value"></a>返回值

消息处理的结果。 如果成功，则为 0。

## <a name="remarks"></a>备注

消息映射中使用此消息处理程序的示例，请参阅[COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler)。

## <a name="see-also"></a>请参阅

[实现窗口](../atl/implementing-a-window.md)<br/>
[消息映射](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/desktop/controls/wm-notify)
