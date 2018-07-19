---
title: 消息处理程序 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- MessageHandler
dev_langs:
- C++
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dcd02396fa76e9e68fce628783fb17bc6adab36e
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2018
ms.locfileid: "37848397"
---
# <a name="messagehandler"></a>消息处理程序
`MessageHandler` 是由消息映射中的 MESSAGE_HANDLER 宏的第二个参数标识的名称。  
  
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
 *uMsg*  
 指定的消息。  
  
 *wParam*  
 其他特定于消息的信息。  
  
 *lParam*  
 其他特定于消息的信息。  
  
 *bHandled*  
 消息映射集*bHandled*为 TRUE，然后才能`MessageHandler`调用。 如果`MessageHandler`不完全处理该消息，应设置*bHandled*为 FALSE 以指示该消息需要进一步处理。  
  
## <a name="return-value"></a>返回值  
 消息处理的结果。 如果成功，则为 0。  
  
## <a name="remarks"></a>备注  
 消息映射中使用此消息处理程序的示例，请参阅[MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler)。  
  
## <a name="see-also"></a>请参阅  
 [实现窗口](../atl/implementing-a-window.md)   
 [消息映射](../atl/message-maps-atl.md)   
 [WM_NOTIFY](http://msdn.microsoft.com/library/windows/desktop/bb775583)

