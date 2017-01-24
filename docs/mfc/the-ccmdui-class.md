---
title: "CCmdUI 类 | Microsoft Docs"
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
  - "CCmdUI"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CCmdUI 类, 菜单更新"
  - "工具栏 [C++], 更新"
  - "更新处理程序"
  - "更新用户界面对象"
  - "用户界面对象, 更新"
ms.assetid: 2f2bae62-8c29-45a4-bbce-490eb01907d5
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CCmdUI 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当发送更新命令给其处理程序时，框架会传递给处理程序一个指向 `CCmdUI` 对象的指针 \(或 `CCmdUI`的对象派生类\)。  此对象表示发出命令的菜单项或工具栏按钮或其他用户界面对象。  更新处理程序是通过指针调用 `CCmdUI` 结构中成员函数来更新用户界面对象。  例如，这是一个用来清除所有菜单项的更新程序的例子：  
  
 [!code-cpp[NVC_MFCDocView#3](../mfc/codesnippet/CPP/the-ccmdui-class_1.cpp)]  
  
 此处理程序调用一个对象的 **启用** 成员函数，用于访问菜单项。  **启用** 使项可以使用。  
  
## 请参阅  
 [如何：更新用户界面对象](../mfc/how-to-update-user-interface-objects.md)