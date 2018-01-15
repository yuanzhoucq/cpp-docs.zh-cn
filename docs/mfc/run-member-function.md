---
title: "运行成员函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 90436e3b775cd547a67be49c120d1fb94b32a5dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="run-member-function"></a>运行成员函数
框架应用程序花费其大部分时间中[运行](../mfc/reference/cwinapp-class.md#run)类的成员函数[CWinApp](../mfc/reference/cwinapp-class.md)。 初始化之后，`WinMain`调用**运行**来处理消息循环。  
  
 **运行**检查是否有可用消息的消息队列的消息循环将循环。 如果可用，消息则**运行**将该消息调度的操作。 如果任何消息不都不可用，这是通常为 true，**运行**调用`OnIdle`执行您或框架可能需要完成任何空闲时间处理。 如果没有要执行的消息和空闲处理，则应用程序将进行等待，直到发生某些情况。 当应用程序终止时，**运行**调用`ExitInstance`。 在图[OnIdle 成员函数](../mfc/onidle-member-function.md)显示在消息循环的操作的顺序。  
  
 消息调度取决于消息类型。 有关详细信息，请参阅[消息和框架中的命令](../mfc/messages-and-commands-in-the-framework.md)。  
  
## <a name="see-also"></a>请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)
