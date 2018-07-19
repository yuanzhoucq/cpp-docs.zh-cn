---
title: MSG 结构 1 |Microsoft Docs
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
ms.openlocfilehash: 5fe629c2f279b6b258f4824229490f7b72b4ce4d
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338807"
---
# <a name="msg-structure1"></a>MSG 结构 1
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
 *hwnd*  
 标识其窗口过程接收消息的窗口。  
  
 *message*  
 指定的消息号。  
  
 *wParam*  
 指定消息有关的其他信息。 值的确切含义取决于`message`成员。  
  
 *lParam*  
 指定消息有关的其他信息。 值的确切含义取决于`message`成员。  
  
 *time*  
 指定发送消息之后的时间。  
  
 *pt*  
 发送消息之后，请指定的游标位置，以屏幕坐标。  
  
## <a name="requirements"></a>要求  
 **标头：** winuser.h  
  
## <a name="see-also"></a>请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

