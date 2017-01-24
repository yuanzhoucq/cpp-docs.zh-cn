---
title: "框架如何调用您的代码 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序特定的事件 [C++]"
  - "命令处理, 调用处理程序和 MFC 中的代码"
  - "命令传送, 框架"
  - "命令传送, MFC"
  - "控制流 [C++], MFC 框架和您的代码"
  - "事件 [C++], MFC 中的命令传送"
  - "事件 [C++], 事件驱动的编程"
  - "MFC [C++], 调用代码"
  - "MFC [C++], 调用代码自"
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 框架如何调用您的代码
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

了解源代码之间的关系对了解MFC 框架是关键的。  当应用程序运行时，大多数控件流位于框架的代码。  框架管理从窗口接收消息的消息循环，以便在用户选择命令并编辑视图中的数据。  框架可以单独处理事件的根本不依赖代码。  例如，框架会如何关闭窗口并退出应用程序响应用户命令。  因为该处理任务，这些框架使用消息处理程序和 C\+\+ 虚拟函数提供了机会响应这些事件。  但代码不是控件，然而框架是。  
  
 框架将调用特定于事件的代码。  例如，当用户选择菜单命令时，框架将沿 C\+\+ 对象序列的命令：当前的视图和框架窗口、文档与视图，文档的文档模板和应用程序对象。  如果其中某个对象可以处理命令，调用相应的消息处理函数。  对于所有给定命令，名为的代码可能是允许或可能是框架。  
  
 此排列是某些熟悉的体验的程序员传统编程或窗口的事件驱动编程。  
  
 在相关主题，将读取框架完成，但初始化并运行应用程序，然后清理时终止应用程序。  您还学习代码在何处编写条件。  
  
 有关更多信息，请参见 [类 CWinApp:应用程序类](../mfc/cwinapp-the-application-class.md) 和 [文档模板和文档\/视图创建过程](../mfc/document-templates-and-the-document-view-creation-process.md)。  
  
## 请参阅  
 [基于框架生成](../mfc/building-on-the-framework.md)