---
title: "CommandHandler |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CommandHandler
dev_langs:
- C++
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2750f1e089ce5b6b3ef34325276a508ea0b80ddb
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="commandhandler"></a>CommandHandler
`CommandHandler` 是由第三个参数的函数`COMMAND_HANDLER`消息映射中的宏。  
  
## <a name="syntax"></a>语法  
  
```  
 
    LRESULT 
    CommandHandler 
 (
    WORD wNotifyCode,  
    WORD wID,  
    HWND hWndCtl,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>参数  
 `wNotifyCode`  
 通知代码中。  
  
 *wID*  
 菜单项、 控件或快捷键的标识符。  
  
 *hWndCtl*  
 窗口控件的句柄。  
  
 `bHandled`  
 消息映射集`bHandled`到**TRUE**之前`CommandHandler`调用。 如果`CommandHandler`并不完全处理消息，它应设置`bHandled`到**FALSE**以指示消息需要进一步处理。  
  
## <a name="return-value"></a>返回值  
 消息处理的结果。 如果成功，则为 0。  
  
## <a name="remarks"></a>备注  
 有关消息映射中使用此消息处理程序的示例，请参阅[COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler)。  
  
## <a name="see-also"></a>请参阅  
 [实现一个窗口](../atl/implementing-a-window.md)   
 [消息映射](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)

