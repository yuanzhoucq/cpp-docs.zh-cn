---
title: "管理当前视图 | Microsoft Docs"
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
  - "框架窗口中的当前视图"
  - "停用视图"
  - "框架窗口, 当前视图"
  - "OnActivateView 方法"
  - "视图, 激活"
  - "视图, 和 OnActivateView 方法"
  - "视图, 当前"
  - "视图, 停用"
ms.assetid: 0a1cc22d-d646-4536-9ad2-3cb6d7092e4a
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 管理当前视图
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在框架窗口的默认实现的一部分，框架窗口记录个当前活动的视图。  如果框架窗口包含多个视图，例如在拆分窗口，当前视图最近视图正在使用。  活动视图是活动窗口的独立窗口中输入当前或点。  
  
 当活动视图更改时，框架通过调用 [OnActivateView](../Topic/CView::OnActivateView.md) 成员函数通知当前视图。  可以为视图是通过检查参数 `OnActivateView` `bActivate` 激活或停用。  默认情况下，`OnActivateView` 将焦点设置上的当前活动的视图。  可以重写 `OnActivateView` 执行任何特殊处理视图在停用或重新激活。  例如，您可能需要提供特定可视化提示与其他所有行区活动视图，停用视图。  
  
 框架窗口 \(\) 为当前活动视图的"命令，如 [命令传送](../mfc/command-routing.md)所述，在标准命令传送一部分。  
  
## 请参阅  
 [使用框架窗口](../mfc/using-frame-windows.md)