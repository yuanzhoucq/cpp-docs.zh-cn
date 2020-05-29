---
title: Windows 消息宏
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: a5a6d45c64d6123128ae362c1ef5643392439f41
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329412"
---
# <a name="windows-messages-macros"></a>Windows 消息宏

此宏转发窗口消息。

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|用于将窗口收到的消息转发到另一个窗口进行处理。|

## <a name="requirements"></a>要求

**标题：** atlbase.h

## <a name="wm_forwardmsg"></a><a name="wm_forwardmsg"></a>WM_FORWARDMSG

此宏将窗口接收到的消息转发到另一个窗口进行处理。

```
WM_FORWARDMSG
```

### <a name="return-value"></a>返回值

如果处理消息，则非零，如果不是，则为零。

### <a name="remarks"></a>备注

使用WM_FORWARDMSG将窗口收到的消息转发到另一个窗口进行处理。 LPARAM 和 WPARAM 参数的使用如下：

|参数|使用情况|
|---------------|-----------|
|WPARAM|用户定义的数据|
|LPARAM|指向包含消息信息`MSG`的结构的指针|

### <a name="example"></a>示例

在下面的示例中，`m_hWndOther`表示接收此消息的其他窗口。

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>另请参阅

[宏](../../atl/reference/atl-macros.md)
