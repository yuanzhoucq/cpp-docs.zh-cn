---
title: "消息 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d03eed129fd5a2a7c73f7c7948cb766813f63c34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="messages"></a>消息
中的消息循环**运行**类的成员函数`CWinApp`检索排队生成的各种事件消息。 例如，当用户单击鼠标时，Windows 将发送若干与鼠标有关的消息，如 `WM_LBUTTONDOWN`（按鼠标左键时）和 `WM_LBUTTONUP`（按鼠标右键时）。 应用程序消息循环的框架的实现会将消息调度到合适的窗口。  
  
 中介绍的消息的重要类别[消息类别](../mfc/message-categories.md)。  
  
## <a name="see-also"></a>请参阅  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)

