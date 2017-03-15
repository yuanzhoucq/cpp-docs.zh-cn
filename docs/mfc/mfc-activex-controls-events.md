---
title: "MFC ActiveX 控件：事件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleControl 类, 事件的处理"
  - "容器事件"
  - "自定义事件, 添加到 ActiveX 控件"
  - "事件 [C++], ActiveX 控件"
  - "事件 [C++], 映射"
  - "映射, 事件"
  - "MFC ActiveX 控件, 事件"
  - " [C++], 通知事件容器"
  - "OLE 事件"
  - "常用事件"
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# MFC ActiveX 控件：事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

ActiveX 控件使用事件通知内容发生控件的容器。  事件的通用示例包括在控件状态单击控件，使用键盘输入的数据，并且更改。  在这些操作时，控件引发事件通知容器。  
  
 事件还调用消息。  
  
 MFC 支持两个事件：常用和自定义。  常用事件是自动的 [COleControl](../mfc/reference/colecontrol-class.md) 类处理这些事件。  有关常用事件的完整列表，请参见的文章 [MFC ActiveX 控件：添加股票事件](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)。  当该控件特定的操作发生时，自定义事件提供了通知控件容器。  某些示例在以下某一窗口消息的控件或接收的内部状态的更改。  
  
 为了能够将相应地激发的控件事件，控件类必须映射每个控件的事件。应调用的成员相关函数，当发生事件时。  此映射机制 \(称为事件映射\) 焦点有关事件的信息并使 Visual Studio 很容易地访问和操作该控件的事件。  此事件由映射以下宏声明，在标题 \(。H 控件类\) 声明的文件：  
  
 [!code-cpp[NVC_MFC_AxUI#2](../mfc/codesnippet/CPP/mfc-activex-controls-events_1.h)]  
  
 在事件声明映射后，在控件的实现 \(.cpp\) 文件必须定义它。  以下代码行定义事件映射，允许控件触发给定事件：  
  
 [!code-cpp[NVC_MFC_AxUI#3](../mfc/codesnippet/CPP/mfc-activex-controls-events_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#4](../mfc/codesnippet/CPP/mfc-activex-controls-events_3.cpp)]  
  
 如若使用 MFC ActiveX 控件向导创建项目时，它自动添加这些行。  如果不使用 MFC ActiveX 控件向导，您必须手动添加这些行。  
  
 类视图，可以将定义类支持的库存事件 `COleControl` 或自定义事件。  对于每个新事件，类视图自动将适当的输入到控件的事件映射和控件的 .idl 文件。  
  
 其他两个情景详细介绍事件：  
  
-   [MFC ActiveX 控件：添加股票事件](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [MFC ActiveX 控件：添加自定义事件](../mfc/mfc-activex-controls-adding-custom-events.md)  
  
## 请参阅  
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [MFC ActiveX 控件：方法](../mfc/mfc-activex-controls-methods.md)   
 [COleControl Class](../mfc/reference/colecontrol-class.md)