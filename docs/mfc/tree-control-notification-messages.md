---
title: 树控件通知消息 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], tree controls
- messages [MFC], notification
- CTreeCtrl class [MFC], notifications
- notifications [MFC], CTreeCtrl
- tree controls [MFC], notification messages
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f7c352da9f9283f53c926a8223984620ee7fa6ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385731"
---
# <a name="tree-control-notification-messages"></a>树控件通知消息
树控件 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 发送以下通知消息作为**WM_NOTIFY**消息：  
  
|通知消息|描述|  
|--------------------------|-----------------|  
|**TVN_BEGINDRAG**|用信号通知拖放操作开始|  
|**TVN_BEGINLABELEDIT**|用信号通知开始就地标签编辑|  
|**TVN_BEGINRDRAG**|用信号通知拖放操作，使用鼠标右键按钮开始|  
|**TVN_DELETEITEM**|用信号通知特定项目的删除|  
|**TVN_ENDLABELEDIT**|表示结束的标签编辑|  
|**TVN_GETDISPINFO**|树控件显示项所需的请求信息|  
|**TVN_ITEMEXPANDED**|父项的子项列表已展开或折叠的信号|  
|**TVN_ITEMEXPANDING**|父项的子项列表是要展开或折叠的信号|  
|**TVN_KEYDOWN**|用信号通知键盘事件|  
|**TVN_SELCHANGED**|所选内容已从一个项更改为另一个的信号|  
|**TVN_SELCHANGING**|选择是要从一个项更改为另一个的信号|  
|**TVN_SETDISPINFO**|若要维护的某个项目的信息更新的通知|  
  
## <a name="see-also"></a>请参阅  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控件](../mfc/controls-mfc.md)

