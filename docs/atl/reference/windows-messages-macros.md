---
title: Windows 消息宏 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
dev_langs:
- C++
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f9d312104254323e98f6b2fd031adf1064ecfac
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078214"
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
