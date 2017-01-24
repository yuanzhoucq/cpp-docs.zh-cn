---
title: "框架窗口样式 (MFC) | Microsoft Docs"
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
  - "FWS_ADDTOTITLE"
  - "FWS_SNAPTOBARS"
  - "FWS_PREFIXTITLE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "框架窗口, 样式"
  - "FWS_ADDTOTITLE 常量"
  - "FWS_PREFIXTITLE 常量"
  - "FWS_SNAPTOBARS 常量"
  - "样式, 窗口"
ms.assetid: d21f270e-a088-4962-a2ae-8c03334b5a06
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 框架窗口样式 (MFC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **FWS\_ADDTOTITLE** 指定信息附加到框架窗口标题的末尾。  例如，“Microsoft Draw \- 在 Document1 绘制”。  在应用程序向导的文档模板字符串选项卡可以指定显示的字符串。  如果您需要关闭此选项，请重写 `CWnd::PreCreateWindow` 成员函数。  
  
-   **FWS\_PREFIXTITLE** 在框架窗口标题前显示文档名称，在应用程序名称。  例如，将“Doc " \-”。  在应用程序向导的文档模板字符串选项卡可以指定显示的字符串。  如果您需要关闭此选项，请重写 `CWnd::PreCreateWindow` 成员函数。  
  
-   **FWS\_SNAPTOBARS** 用一个控制条的控件大小框架窗口，则在一个浮动窗口而不是停靠到框架窗口。  此样式调整窗口大小以适应控件条。  
  
## 请参阅  
 [MFC 使用的样式](../../mfc/reference/styles-used-by-mfc.md)