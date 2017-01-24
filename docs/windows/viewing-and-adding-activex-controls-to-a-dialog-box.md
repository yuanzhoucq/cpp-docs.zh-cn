---
title: "Viewing and Adding ActiveX Controls to a Dialog Box | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.controls.activex"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "dialog boxes [C++], adding ActiveX controls"
  - "Insert ActiveX Control command"
  - "ActiveX controls [C++], adding to dialog boxes"
ms.assetid: e1c2e3ae-e1b0-40d3-9766-623007073856
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Viewing and Adding ActiveX Controls to a Dialog Box
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual Studio 使你可以将 ActiveX 控件插入对话框中。  
  
### 查看你可使用的 ActiveX 控件  
  
1.  在对话框编辑器中打开一个对话框。  
  
2.  右键单击该对话框主体中的任何位置。  
  
3.  在快捷菜单上，单击“插入 ActiveX 控件”。  
  
     [“插入 ActiveX 控件”对话框](../mfc/insert-activex-control-dialog-box.md)随即出现，其中显示你系统上的所有 ActiveX 控件。 在该对话框底部，会显示 ActiveX 控件文件的路径。  
  
### 将 ActiveX 控件添加到对话框  
  
1.  在[“插入 ActiveX 控件”对话框](../mfc/insert-activex-control-dialog-box.md)中，选择要添加到对话框中的控件，然后单击“确定”。  
  
     该控件会出现在对话框中，可以在其中编辑它或为它创建处理程序，就如同处理任何其他控件一样。  
  
    > [!NOTE]
    >  可以将 ActiveX 控件添加到[工具箱窗口](../Topic/Toolbox.md)。 有关详细信息，请参阅[管理工具箱中的项目和选项卡](http://msdn.microsoft.com/zh-cn/21285050-cadd-455a-b1f5-a2289a89c4db)。  
  
    > [!CAUTION]
    >  分发系统上的每个 ActiveX 控件可能并非都是合法的。 请参阅安装了控件的软件的许可协议，或与软件公司联系。  
  
     可以在工具箱窗口中放置控件以方便访问。 有关详细信息，请参阅[自定义工具箱对话框](http://msdn.microsoft.com/zh-cn/bd07835f-18a8-433e-bccc-7141f65263bb)。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 Win32  
  
## 请参阅  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)   
 [MFC ActiveX 控件](../mfc/mfc-activex-controls.md)   
 [ActiveX 控件容器](../mfc/activex-control-containers.md)