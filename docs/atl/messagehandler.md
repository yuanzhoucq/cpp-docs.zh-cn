---
title: "消息处理程序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- MessageHandler
dev_langs:
- C++
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7247868f85a30cbecef416c690f181f068f7eaf2
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="messagehandler"></a>MessageHandler
**消息处理程序**是标识的第二个参数的函数的名称`MESSAGE_HANDLER`消息映射中的宏。  
  
## <a name="syntax"></a>语法  
  
```  
 
    LRESULT 
    MessageHandler 
 (
    UINT uMsg,  
    WPARAM wParam,  
    LPARAM lParam,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>参数  
 `uMsg`  
 指定的消息。  
  
 `wParam`  
 消息特定的附加信息。  
  
 `lParam`  
 消息特定的附加信息。  
  
 `bHandled`  
 消息映射集`bHandled`到**TRUE**之前`MessageHandler`调用。 如果`MessageHandler`并不完全处理消息，它应设置`bHandled`到**FALSE**以指示消息需要进一步处理。  
  
## <a name="return-value"></a>返回值  
 消息处理的结果。 如果成功，则为 0。  
  
## <a name="remarks"></a>备注  
 有关消息映射中使用此消息处理程序的示例，请参阅[MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler)。  
  
## <a name="see-also"></a>请参阅  
 [实现一个窗口](../atl/implementing-a-window.md)   
 [消息映射](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)

