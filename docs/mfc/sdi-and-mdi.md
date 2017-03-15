---
title: "SDI 和 MDI | Microsoft Docs"
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
  - "框架窗口, MDI 应用程序"
  - "框架窗口, SDI 应用程序"
  - "MDI, 与 SDI"
  - "MFC, 窗口"
  - "单文档界面 (SDI), 应用程序"
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# SDI 和 MDI
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 轻松地与单文档界面 \(MDI\) \(SDI\) 和多文档界面 \(MDI\) \(MDI\) 应用程序一起使用。  
  
 SDI 应用程序一次只允许一种开放文档框架窗口。  MDI 应用程序使用多文档框架窗口在应用程序中打开的同一实例。  MDI 应用程序内存在多个，MDI 子窗口是框架窗口，中打开的窗口，在包含单独的文档中的每个元素。  在某些应用程序，子窗口可以是不同的类型，例如窗口图表和电子表格窗口。  在这种情况下，那么，当 MDI 子窗口不同类型的激活，菜单栏可以更改。  
  
> [!NOTE]
>  在 Windows 95 下，因为操作系统的文档采用“居中”视图，然后后，应用程序通常是 SDI。  
  
 有关更多信息，请参见 [文档、视图和框架](../mfc/documents-views-and-the-framework.md)。  
  
## 请参阅  
 [使用类编写 Windows 应用程序](../mfc/using-the-classes-to-write-applications-for-windows.md)