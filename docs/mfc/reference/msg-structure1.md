---
title: MSG 结构 1 |Microsoft 文档
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
ms.openlocfilehash: 41dbbcdd3404705a9ac7c6c7969a9ebeeb0238f8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33372252"
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
  
## <a name="requirements"></a>要求  
 **标头：** winuser.h  
  
## <a name="see-also"></a>请参阅  
 [结构、样式、回调和消息映射](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

