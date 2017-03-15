---
title: "Creating a Dialog Box That Users Cannot Exit | Microsoft Docs"
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
  - "dialog boxes, creating"
  - "modal dialog boxes, logon screens"
  - "logon screens"
ms.assetid: 54823c27-1658-4388-bd12-0a1ce8f3899e
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Creating a Dialog Box That Users Cannot Exit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以创建用户无法退出的运行时对话框。 这种类型的对话框对于登录、应用程序或文档锁定非常有用。  
  
### 创建用户无法退出的对话框  
  
1.  在对话框的“属性”窗格中，将“系统菜单”属性设置为“false”。  
  
     这样会禁用对话框系统菜单和“关闭”按钮。  
  
2.  在对话框窗体中，删除“取消”和“确定”按钮。  
  
     在运行时，用户无法退出具有以下特征的模式对话框。  
  
 要对这种对话框进行测试，测试对话框函数可以在按下 Esc 键时检测。 （ESC 是也称为 VK\_ESCAPE 虚拟键。） 不论如何设计运行时的对话框行为，都可以通过在测试模式下按 Esc 键终止。  
  
> [!NOTE]
>  对于 MFC 应用程序，要创建一个用户无法退出的对话框，必须重写 `OnOK`和 `OnCancel` 的默认行为，因为即使删除关联按钮，仍可通过按 ENTER 或 ESC 键来取消对话框。  
  
 有关如何向托管项目中添加资源的信息，请参阅 [桌面应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。  
  
## 要求  
 Win32  
  
## 请参阅  
 [How to: Create a Resource](../windows/how-to-create-a-resource.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Dialog Editor](../mfc/dialog-editor.md)