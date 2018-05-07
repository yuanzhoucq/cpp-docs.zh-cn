---
title: 命令传送示例 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command handling [MFC], routing commands
- command routing [MFC], OnCmdMsg handler
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a12a5cd19177761dfbf484c64f528d8def194ca5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="command-routing-illustration"></a>命令传送示例
为了说明，请考虑来自 MDI 应用程序的“编辑”菜单中“全部清除”菜单项的命令消息。 假设此命令的处理程序函数恰好是应用程序的文档类的成员函数。 下面演示了在用户选择菜单项后命令如何到达其处理程序：  
  
1.  主框架窗口首先收到命令消息。  
  
2.  主 MDI 框架窗口为当前处于活动状态的 MDI 子窗口提供处理命令的机会。  
  
3.  MDI 子框架窗口的标准传送在检查自己的消息映射前为其视图提供了一个执行命令的机会。  
  
4.  视图首先检查自己的消息映射，如果未找到处理程序，则会将命令传送到其关联文档。  
  
5.  该文档检查其消息映射并找到一个处理程序。 将调用此文档成员函数，然后传送停止。  
  
 如果文档没有处理程序，它会将命令传送到其文档模板。 接下来，命令将返回到视图，然后返回到框架窗口。 最后，框架窗口将检查其消息映射。 如果该检查也失败，命令将传送回主 MDI 框架窗口，然后传送到应用程序对象（未处理的命令的最终目标）。  
  
## <a name="see-also"></a>请参阅  
 [框架如何调用处理程序](../mfc/how-the-framework-calls-a-handler.md)

