---
title: "非命令消息如何到达其处理程序 |Microsoft 文档"
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
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 33d0d65c9916cfc571ecfd623138938c0c883ba5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>非命令消息如何到达其处理程序
与命令不同，标准 Windows 消息执行不获取通过链的命令目标路由，但通常由 Windows 将消息发送到窗口。 窗口可能是主框架窗口、 MDI 子窗口、 标准控件、 对话框中、 视图或其他一些种类的子窗口。  
  
 在运行时，每个 Windows 窗口连接到的窗口对象 (直接或间接派生自`CWnd`)，其自己的关联的消息映射和处理程序函数。 框架将使用消息映射 — 像对待命令 — 将传入消息映射到处理程序。  
  
## <a name="see-also"></a>请参阅  
 [框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)

