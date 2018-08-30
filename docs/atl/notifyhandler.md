---
title: NotifyHandler |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- NotifyHandler
dev_langs:
- C++
helpviewer_keywords:
- NotifyHandler function
ms.assetid: 5ff953ec-de35-42bc-8b3c-d384d636c139
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e39b0b1ac94a759c4a8b30fce8c634ed49be4ff9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43209474"
---
# <a name="notifyhandler"></a>NotifyHandler
消息映射中的 NOTIFY_HANDLER 宏的第三个参数标识的函数的名称。  
  
## <a name="syntax"></a>语法  
  
```  
 
    LRESULT 
    NotifyHandler 
 (
    int idCtrl,  
    LPNMHDR pnmh,  
    BOOL& bHandled);
```  
  
#### <a name="parameters"></a>参数  
 *idCtrl*  
 发送消息的控件的标识符。  
  
 *pnmh*  
 地址[NMHDR](/windows/desktop/api/richedit/ns-richedit-_nmhdr)结构，其中包含通知代码和其他信息。 对于某些通知消息，此参数指向具有较大结构`NMHDR`结构作为其第一个成员。  
  
 *bHandled*  
 消息映射集*bHandled*为 TRUE，然后才能*NotifyHandler*调用。 如果*NotifyHandler*不完全处理该消息，应设置*bHandled*到**FALSE**来指示该消息需要进一步处理。  
  
## <a name="return-value"></a>返回值  
 消息处理的结果。 如果成功，则为 0。  
  
## <a name="remarks"></a>备注  
 消息映射中使用此消息处理程序的示例，请参阅[NOTIFY_HANDLER](reference/message-map-macros-atl.md#notify_handler))。  
  
## <a name="see-also"></a>请参阅  
 [实现窗口](../atl/implementing-a-window.md)   
 [消息映射](../atl/message-maps-atl.md)   
 [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)

