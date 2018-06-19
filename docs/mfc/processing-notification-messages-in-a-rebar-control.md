---
title: 处理 Rebar 控件中的通知消息 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a06df0bdfe8d1b81b4285fc86378f3da99882698
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348411"
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>处理 Rebar 控件中的通知消息
在 rebar 控件的父类中，为所有需要处理的 rebar 控件 (`OnChildNotify`) 通知消息创建一个带有 switch 语句的 `CReBarCtrl` 处理程序函数。 当用户在 rebar 控件上拖动对象、更改 rebar 带区的布局、从 rebar 控件中删除带区等时，将向其父窗口发送通知。  
  
 可通过 rebar 控件对象发送以下通知消息：  
  
-   **RBN_AUTOSIZE** ，由 rebar 控件发送 (使用创建**RBS_AUTOSIZE**样式) 当 rebar 自动调整自身大小。  
  
-   **RBN_BEGINDRAG**在用户开始拖动带区时，由 rebar 控件发送。  
  
-   **RBN_CHILDSIZE**调整带区的子窗口的大小时，由 rebar 控件发送。  
  
-   **RBN_DELETEDBAND**在删除带区后，由 rebar 控件发送。  
  
-   **RBN_DELETINGBAND**将要删除带区时，由 rebar 控件发送。  
  
-   **RBN_ENDDRAG**用户停止拖动带区时，由 rebar 控件发送。  
  
-   **RBN_GETOBJECT** ，由 rebar 控件发送 (使用创建**RBS_REGISTERDROP**样式) 时将对象拖到控件中的带。  
  
-   **RBN_HEIGHTCHANGE**窗体的高度已更改时，由 rebar 控件发送。  
  
-   **RBN_LAYOUTCHANGED**在用户更改控件的带区布局时，由 rebar 控件发送。  
  
 有关这些通知的详细信息，请参阅[Rebar 控件参考](http://msdn.microsoft.com/library/windows/desktop/bb774375)Windows SDK 中。  
  
## <a name="see-also"></a>请参阅  
 [使用 CReBarCtrl](../mfc/using-crebarctrl.md)   
 [控件](../mfc/controls-mfc.md)

