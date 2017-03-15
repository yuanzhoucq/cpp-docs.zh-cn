---
title: "如何：从 MFC 应用程序中加载功能区资源 | Microsoft Docs"
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
  - "功能区资源, 加载"
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 如何：从 MFC 应用程序中加载功能区资源
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

若要使用功能区资源位于应用程序，请修改应用程序加载功能区资源。  
  
### 加载功能区资源  
  
1.  在 `Ribbon Control` 命名空间中，声明 `CMainFrame` 类。  
  
    ```  
    CMFCRibbonBar m_wndRibbonBar;   
    ```  
  
2.  在 `CMainFrame::OnCreate`中，请创建并初始化功能区控件。  
  
    ```  
    if (!m_wndRibbonBar.Create (this))  
    {  
        return -1;  
    }  
  
    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))  
    {  
        return -1;  
    }  
    ```  
  
## 请参阅  
 [功能区设计器 \(MFC\)](../mfc/ribbon-designer-mfc.md)