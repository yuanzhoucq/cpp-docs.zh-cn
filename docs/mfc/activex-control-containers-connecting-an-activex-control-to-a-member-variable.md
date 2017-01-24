---
title: "ActiveX 控件容器：将 ActiveX 控件连接到成员变量 | Microsoft Docs"
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
  - "ActiveX 控件容器 [C++], 访问 ActiveX 控件"
  - "ActiveX 控件容器 [C++], ActiveX 控件作为成员变量"
  - "ActiveX 控件 [C++], 访问"
  - "ActiveX 控件 [C++], 项目的成员变量"
  - "将 ActiveX 控件与容器成员变量相连接"
  - "成员变量 [C++], 项目中的 ActiveX 控件"
ms.assetid: 7898a336-440d-4a60-be43-cb062b807aee
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActiveX 控件容器：将 ActiveX 控件连接到成员变量
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

简单的访问方法 ActiveX 控件从其控件容器应用程序内部会与 ActiveX 控件使用将包含控件对话框类的成员变量。  
  
> [!NOTE]
>  这不是唯一的方法访问嵌入的控件从容器类的内部，但对于，本文满足的。  
  
### 将成员变量添加到的对话框类  
  
1.  从类视图，请右击主对话框类打开快捷菜单。  例如 `CContainerDlg`。  
  
2.  在快捷菜单上，单击**“添加”**，再单击**“添加变量”**。  
  
3.  在"添加成员变量向导，单击 **控件变量 \(O\)**。  
  
4.  在 **控件 ID** 列表框，选择嵌入一个 ActiveX 控件的控件 ID。  例如 `IDC_CIRCCTRL1`。  
  
5.  在“变量名”框中，键入名称。  
  
     例如 `m_circctl`。  
  
6.  单击 **完成** 接受选择并退出"添加成员变量向导"  
  
## 请参阅  
 [ActiveX 控件容器](../mfc/activex-control-containers.md)