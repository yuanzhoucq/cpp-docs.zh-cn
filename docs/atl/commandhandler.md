---
title: CommandHandler |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CommandHandler
dev_langs:
- C++
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ad124f0819dbfd9cfd0117cb91fbcffba05a400
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43201271"
---
# <a name="commandhandler"></a>CommandHandler
`CommandHandler` 函数是通过消息映射中的 COMMAND_HANDLER 宏的第三个参数标识。  
  
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
 *wNotifyCode*  
 通知代码。  
  
 *wID*  
 菜单项、 控件或加速器的标识符。  
  
 *hWndCtl*  
 窗口控件的句柄。  
  
 *bHandled*  
 消息映射集*bHandled*为 TRUE，然后才能`CommandHandler`调用。 如果`CommandHandler`不完全处理该消息，应设置*bHandled*为 FALSE 以指示该消息需要进一步处理。  
  
## <a name="return-value"></a>返回值  
 消息处理的结果。 如果成功，则为 0。  
  
## <a name="remarks"></a>备注  
 消息映射中使用此消息处理程序的示例，请参阅[COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler)。  
  
## <a name="see-also"></a>请参阅  
 [实现窗口](../atl/implementing-a-window.md)   
 [消息映射](../atl/message-maps-atl.md)   
 [WM_NOTIFY](https://msdn.microsoft.com/library/windows/desktop/bb775583)

