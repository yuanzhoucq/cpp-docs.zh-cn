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
ms.openlocfilehash: a658af47723a9c19218b205a17cb46919d7abd59
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932281"
---
# <a name="run-member-function"></a>运行成员函数
框架应用程序花费其大部分时间中[运行](../mfc/reference/cwinapp-class.md#run)类的成员函数[CWinApp](../mfc/reference/cwinapp-class.md)。 初始化之后，`WinMain`调用`Run`来处理消息循环。  
  
 `Run` 通过检查有可用消息的消息队列的消息循环的周期。 如果可用，消息则`Run`将该消息调度的操作。 如果任何消息不都不可用，这是通常为 true，`Run`调用`OnIdle`执行您或框架可能需要完成任何空闲时间处理。 如果没有要执行的消息和空闲处理，则应用程序将进行等待，直到发生某些情况。 当应用程序终止时，`Run`调用`ExitInstance`。 在图[OnIdle 成员函数](../mfc/onidle-member-function.md)显示在消息循环的操作的顺序。  
  
 消息调度取决于消息类型。 有关详细信息，请参阅[消息和框架中的命令](../mfc/messages-and-commands-in-the-framework.md)。  
  
## <a name="see-also"></a>请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)
