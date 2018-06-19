---
title: 运行成员函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be1d7d90b4c13a23e2e3456e7371abbae61be4e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379891"
---
# <a name="run-member-function"></a>运行成员函数
框架应用程序花费其大部分时间中[运行](../mfc/reference/cwinapp-class.md#run)类的成员函数[CWinApp](../mfc/reference/cwinapp-class.md)。 初始化之后，`WinMain`调用**运行**来处理消息循环。  
  
 **运行**检查是否有可用消息的消息队列的消息循环将循环。 如果可用，消息则**运行**将该消息调度的操作。 如果任何消息不都不可用，这是通常为 true，**运行**调用`OnIdle`执行您或框架可能需要完成任何空闲时间处理。 如果没有要执行的消息和空闲处理，则应用程序将进行等待，直到发生某些情况。 当应用程序终止时，**运行**调用`ExitInstance`。 在图[OnIdle 成员函数](../mfc/onidle-member-function.md)显示在消息循环的操作的顺序。  
  
 消息调度取决于消息类型。 有关详细信息，请参阅[消息和框架中的命令](../mfc/messages-and-commands-in-the-framework.md)。  
  
## <a name="see-also"></a>请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)
