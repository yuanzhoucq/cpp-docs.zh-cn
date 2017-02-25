---
title: "对对话框中的控件进行类型安全的访问 | Microsoft Docs"
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
  - "公共控件 [C++], 在对话框中"
  - "控件 [MFC], 在对话框中访问"
  - "对话框 [C++], 对控件的类型安全访问"
  - "MFC 对话框, 对控件的类型安全访问"
  - "对对话框控件的安全访问"
  - "对对话框控件的类型安全访问"
  - "Windows 公共控件 [C++], 在对话框中"
ms.assetid: 67021025-dd93-4d6a-8bed-a1348fe50685
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 对对话框中的控件进行类型安全的访问
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

对话框中的控件可以使用 MFC 控件类的接口，如 `CListBox` 和 `CEdit`。  您可以创建控件对象并将其附加到对话框控件。  然后，可以通过控件的类接口访问该控件，并调用成员函数以操作该控件。  此处介绍的方法旨在为您提供对控件的类型安全访问。  这对诸如编辑框和列表框之类的控件特别有用。  
  
 可通过两种方法在对话框中的控件和 `CDialog` 派生的类中的 C\+\+ 控件成员变量之间建立连接。  
  
-   [不使用代码向导](../mfc/type-safe-access-to-controls-without-code-wizards.md)  
  
-   [使用代码向导](../mfc/type-safe-access-to-controls-with-code-wizards.md)  
  
## 请参阅  
 [对话框](../mfc/dialog-boxes.md)