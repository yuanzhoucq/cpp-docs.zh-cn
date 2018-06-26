---
title: 消息 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d7544d92d55ec4a1f6d15f3c1d4358970bf2deb
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928336"
---
# <a name="messages"></a>消息
中的消息循环`Run`类的成员函数`CWinApp`检索排队生成的各种事件消息。 例如，当用户单击鼠标时，Windows 将发送若干与鼠标相关消息，如 WM_LBUTTONDOWN 按下鼠标左键时和 WM_LBUTTONUP 释放鼠标左键时。 应用程序消息循环的框架的实现会将消息调度到合适的窗口。  
  
 中介绍的消息的重要类别[消息类别](../mfc/message-categories.md)。  
  
## <a name="see-also"></a>请参阅  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)

