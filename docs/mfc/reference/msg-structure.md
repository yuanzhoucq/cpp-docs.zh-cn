---
title: MSG 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- MSG
dev_langs:
- C++
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2b2f58af3bcf3eef524b95d25579e5bc233f9108
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2018
ms.locfileid: "49334505"
---
# <a name="msg-structure"></a>MSG 结构

`MSG`结构包含来自线程的消息队列的消息信息。

## <a name="syntax"></a>语法

```
typedef struct tagMSG {     // msg
    HWND hwnd;
    UINT message;
    WPARAM wParam;
    LPARAM lParam;
    DWORD time;
    POINT pt;
} MSG;
```

#### <a name="parameters"></a>参数

*hwnd*<br/>
标识其窗口过程接收消息的窗口。

*message*<br/>
指定的消息号。

*wParam*<br/>
指定消息有关的其他信息。 值的确切含义取决于`message`成员。

*lParam*<br/>
指定消息有关的其他信息。 值的确切含义取决于`message`成员。

*time*<br/>
指定发送消息之后的时间。

*pt*<br/>
发送消息之后，请指定的游标位置，以屏幕坐标。

## <a name="requirements"></a>要求

**标头：** winuser.h

## <a name="see-also"></a>请参阅

[结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

