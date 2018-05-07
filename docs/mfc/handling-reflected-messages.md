---
title: 处理反射消息 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05b5f62169d2b65010ec75ab8c8b5c30959b77b2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="handling-reflected-messages"></a>处理反射消息
消息反射可以让您处理消息的控件，如`WM_CTLCOLOR`， **WM_COMMAND**，和**WM_NOTIFY**，控件自身。 这使得控件更独立和可移植。 此机制适用于 Windows 公共控件以及 ActiveX 控件（之前称为 OLE 控件）。  
  
 消息反射可以让您轻松地重用 `CWnd` 派生类。 消息反射通过[CWnd::OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)，使用特殊**ON_XXX_REFLECT**消息映射条目： 例如， **ON_CTLCOLOR_REFLECT**和**ON_CONTROL_REFLECT**。 [技术说明 62](../mfc/tn062-message-reflection-for-windows-controls.md)介绍了消息反射更多详细信息。  
  
## <a name="what-do-you-want-to-do"></a>你希望做什么  
  
-   [了解有关消息反射](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [实现公共控件的消息的反射](../mfc/tn062-message-reflection-for-windows-controls.md)  
  
-   [实现 ActiveX 控件的消息反射](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)  
  
## <a name="see-also"></a>请参阅  
 [声明消息处理程序函数](../mfc/declaring-message-handler-functions.md)
