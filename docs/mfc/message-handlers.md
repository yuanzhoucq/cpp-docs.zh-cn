---
title: "消息处理程序 |Microsoft 文档"
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
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d1b906a49d7da7ed8505252a1759d7ea00fcda1f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="message-handlers"></a>消息处理程序
在 MFC 中，专用*处理程序*函数处理每个单独的消息。 消息处理程序函数是类的成员函数。 本文档使用的词汇*消息处理程序成员函数*，*消息处理程序函数*，*消息处理程序*，和*处理程序*互换。 某些类型的消息处理程序也称为“命令处理程序”。  
  
 编写消息处理程序时，您的大部分精力都将耗在编写框架应用程序上。 本文章系列介绍消息处理机制的工作方式。  
  
 所执行的操作的消息处理程序执行此操作没有任何你希望执行的响应该消息。 你可以使用类的“属性”窗口创建处理程序，然后使用源代码编辑器填写处理程序的代码。  
  
 您可以使用 Microsoft Visual C++ 和 MFC 的所有工具编写处理程序。 所有类的列表，请参阅[类库概述](../mfc/class-library-overview.md)中*MFC 参考*。  
  
## <a name="see-also"></a>请参阅  
 [框架中的消息和命令](../mfc/messages-and-commands-in-the-framework.md)

