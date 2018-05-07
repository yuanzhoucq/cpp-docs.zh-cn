---
title: 非命令消息如何到达其处理程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3999c74bf7a612acb998e7a044c12948d7679d9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>非命令消息如何到达其处理程序
与命令不同，标准 Windows 消息执行不获取通过链的命令目标路由，但通常由 Windows 将消息发送到窗口。 窗口可能是主框架窗口、 MDI 子窗口、 标准控件、 对话框中、 视图或其他一些种类的子窗口。  
  
 在运行时，每个 Windows 窗口连接到的窗口对象 (直接或间接派生自`CWnd`)，其自己的关联的消息映射和处理程序函数。 框架将使用消息映射 — 像对待命令 — 将传入消息映射到处理程序。  
  
## <a name="see-also"></a>请参阅  
 [框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)

