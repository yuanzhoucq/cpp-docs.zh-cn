---
title: "事件处理程序向导 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.eventhandler.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "事件处理程序向导 [C++]"
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 事件处理程序向导
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

该向导向所选的类添加对话框控件的事件处理程序。  如果从[“属性”窗口](../Topic/Properties%20Window.md)添加事件处理程序，则只能将它添加到实现对话框的类。  有关更多信息，请参见[添加对话框控件的事件处理程序](../mfc/adding-event-handlers-for-dialog-box-controls.md)。  
  
 **命令名**  
 标识选定的控件，将为此控件添加事件处理程序。  此框不可用。  
  
 **消息类型**  
 显示选定控件的当前可能的消息处理程序列表。  
  
 **函数处理程序名称**  
 显示为处理事件而添加的函数的名称。  默认情况下，此名称基于消息类型和命令，并带“On”前置。  例如，对于名为 `IDC_BUTTON1` 的按钮，消息类型 `BN_CLICKED` 显示函数处理程序名称 `OnBnClickedButton1`。  
  
 **类列表**  
 显示可以向其添加事件处理程序的可用类。  选定对话框的类显示为红色。  
  
 **处理程序说明**  
 提供“消息类型”框中的选定项的说明。  此框不可用。  
  
 **添加编辑**  
 向选定的类或对象添加消息处理程序，然后以新函数打开文本编辑器，以便可以添加控件通知处理程序代码。  
  
 **编辑代码**  
 以选定的现有函数打开文本编辑器，以便可以添加或编辑控件通知处理程序代码。  
  
## 请参阅  
 [添加事件处理程序](../ide/adding-an-event-handler-visual-cpp.md)