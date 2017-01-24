---
title: "Connecting a Pop-up Menu to Your Application | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "pop-up menus, connecting to applications"
  - "context menus, connecting to applications"
  - "menus, pop-up"
  - "shortcut menus, connecting to applications"
ms.assetid: 295cbf0e-6416-478e-bc3d-472fb98e0e52
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Connecting a Pop-up Menu to Your Application
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### 将弹出菜单连接到应用程序  
  
1.  为 [WM\_CONTEXTMENU](_win32_WM_CONTEXTMENU) 添加消息处理程序（示例）。  有关详细信息，请参阅[将消息映射到函数](../mfc/reference/mapping-messages-to-functions.md)。  
  
2.  将以下代码添加到消息处理程序：  
  
    ```  
    CMenu menu;  
    VERIFY(menu.LoadMenu(IDR_MENU1));  
    CMenu* pPopup = menu.GetSubMenu(0);  
    ASSERT(pPopup != NULL);  
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());  
    ```  
  
    > [!NOTE]
    >  **消息处理程序传递的 [CPoint](../atl-mfc-shared/reference/cpoint-class.md) 位于屏幕坐标中。**  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。 有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
 **要求**  
  
 MFC  
  
## 请参阅  
 [Creating Pop\-up Menus](../windows/creating-pop-up-menus.md)   
 [Menu Editor](../mfc/menu-editor.md)   
 [菜单](_win32_Menus)