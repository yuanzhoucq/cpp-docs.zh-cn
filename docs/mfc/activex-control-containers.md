---
title: "ActiveX 控件容器 | Microsoft Docs"
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
  - "ActiveX 控件容器 [C++]"
  - "OLE 控件 [C++], 容器"
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActiveX 控件容器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ActiveX 控件容器是完全支持 ActiveX 控件，可以将它们放入各自的窗口或对话框中。  ActiveX 控件是可以在多开发项目使用的可重用的软件元素。  控件允许应用程序的用户访问数据库，监视数据，并在应用程序中作出各种选择。  有关注册 ActiveX 控件的更多信息，请参见[注册 MFC 控件](../mfc/mfc-activex-controls.md)。  
  
 控制容器通常采用项目中两种形式：  
  
-   对话框和类似于对话框的窗口 ，ActiveX 控件在对画框中使用。  
  
-   在一个应用程序窗口，ActiveX 控件在工具栏或者用户窗口的其他位置中使用。  
  
 ActiveX 控件容器与控件交互通过公开的 [方法](../mfc/mfc-activex-controls-methods.md)和 [属性](../mfc/mfc-activex-controls-properties.md)。  这些方法和属性，可以通过控件容器进行访问和修改，在 ActiveX 控件容器项目的包装类访问。  嵌入的 ActiveX 控件可与容器进行交互，通过激发 \(发送\) [事件](../mfc/mfc-activex-controls-events.md) 通知容器操作的发生。  控件容器中选择操作处理这些通知。  
  
 讨论多个主题的其他文章，从创建ActiveX 控件项目到基本的实现问题都与用Visual C\+\+创建的ActiveX 控件容器有关:  
  
-   [创建 MFC ActiveX 控件容器](../mfc/reference/creating-an-mfc-activex-control-container.md)  
  
-   [ActiveX 控件的容器](../mfc/containers-for-activex-controls.md)  
  
-   [ActiveX 控件容器：手动启用 ActiveX 控件容量](../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)  
  
-   [ActiveX 控件容器：将控件插入控件容器应用程序](../mfc/inserting-a-control-into-a-control-container-application.md)  
  
-   [ActiveX 控件容器：将 ActiveX 控件连接到成员变量](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)  
  
-   [ActiveX 控件容器：处理 ActiveX 控件中的事件](../mfc/activex-control-containers-handling-events-from-an-activex-control.md)  
  
-   [ActiveX 控件容器：查看和修改控件属性](../mfc/activex-control-containers-viewing-and-modifying-control-properties.md)  
  
-   [ActiveX 控件容器：对 ActiveX 控件容器中的 ActiveX 控件编程](../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
-   [ActiveX 控件容器：使用非对话框容器中的控件](../mfc/activex-control-containers-using-controls-in-a-non-dialog-container.md)  
  
 有关对话框中使用 ActiveX 控件的更多信息，请参见 [对话框编辑器](../mfc/dialog-editor.md) 主题。  
  
 有关说明使用Visual C\+\+和MFC ActiveX 控件类开发 ActiveX 控件详细信息，请参见 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)。  情景按功能类别分组。  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)