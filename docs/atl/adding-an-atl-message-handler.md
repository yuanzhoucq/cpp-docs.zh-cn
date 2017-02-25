---
title: "添加 ATL 消息处理程序 | Microsoft Docs"
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
  - "ATL, 消息处理程序"
  - "ATL, 窗口"
  - "message handlers [C++]"
  - "message handling [C++], ATL message handler"
  - "windows [C++], ATL"
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 添加 ATL 消息处理程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要添加消息处理程序\(成员函数处理Windows消息\)到控件，请首先选择在选件类视图的控件。  然后打开 **属性** 窗口中，选择 **Messages** 图标，然后单击框中的下拉式控件在需的消息相反。  这将添加消息处理程序的声明控件的标头文件和处理程序的一个主干实现的控件的.cpp文件中。  它还将添加消息映射并添加处理程序的项。  
  
 添加ATL的消息处理程序类似于添加消息处理程序添加到MFC选件类。  请参见 [添加MFC消息处理程序](../mfc/reference/adding-an-mfc-message-handler.md) 有关更多信息。  
  
 以下条件仅适用于添加ATL消息处理程序:  
  
-   消息处理程序遵循命名约定和MFC相同。  
  
-   新消息映射项添加到主消息映射。  向导不识别替换消息映射和绑定。  
  
## 请参阅  
 [Implementing a Window](../atl/implementing-a-window.md)