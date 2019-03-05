---
title: Windows 消息宏
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: 7bb5e2fa265c3a5dcabcc16d8343d5b86a4aaf42
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273904"
---
# <a name="windows-messages-macros"></a>Windows 消息宏

此宏将窗口消息转发。

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|使用转发到另一个窗口中进行处理的窗口收到的消息。|

## <a name="requirements"></a>要求

**标头：** atlbase.h

##  <a name="wm_forwardmsg"></a>  WM_FORWARDMSG

此宏将转发到另一个窗口中进行处理的窗口收到的消息。

```
WM_FORWARDMSG
```

### <a name="return-value"></a>返回值

非零值处理该消息，如果数值为零则不。

### <a name="remarks"></a>备注

使用 WM_FORWARDMSG 转发到另一个窗口中进行处理的窗口收到的消息。 按如下所示使用 LPARAM 和 WPARAM 参数：

|参数|用法|
|---------------|-----------|
|WPARAM|由用户定义的数据|
|LPARAM|一个指向`MSG`结构，其中包含有关消息的信息|

### <a name="example"></a>示例

在以下示例中，`m_hWndOther`表示收到此消息的其他窗口。

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>请参阅

[宏](../../atl/reference/atl-macros.md)
