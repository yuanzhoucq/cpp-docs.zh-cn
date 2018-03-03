---
title: "MSG 结构 1 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MSG
dev_langs:
- C++
helpviewer_keywords:
- MSG structure [MFC]
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b504f116dcbff7fa45e741ff9715070ee0c74583
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="msg-structure1"></a>MSG 结构 1
`MSG`结构包含从线程的消息队列的消息信息。  
  
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
 标识其窗口过程中接收的消息窗口。  
  
 `message`  
 指定的消息数。  
  
 `wParam`  
 指定有关该消息的其他信息。 值的确切含义取决于**消息**成员。  
  
 `lParam`  
 指定有关该消息的其他信息。 值的确切含义取决于**消息**成员。  
  
 `time`  
 指定发送消息之后的时间。  
  
 `pt`  
 当发送消息之后，请指定光标位置，在屏幕坐标。  
  
## <a name="requirements"></a>惠?  
 **标头：** winuser.h  
  
## <a name="see-also"></a>请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

