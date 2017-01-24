---
title: "将公共控件用作子窗口 | Microsoft Docs"
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
  - "子窗口, 公共控件"
  - "公共控件 [C++], 子窗口"
  - "控件 [MFC], 用作子窗口"
  - "窗口 [C++], 公共控件"
  - "Windows 公共控件 [C++], 子窗口"
ms.assetid: 608f7d47-7854-4fce-bde9-856c51e76753
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 将公共控件用作子窗口
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

任何一个 Windows 公共控件可用作一个子窗口的其他窗口。  以下过程描述如何以动态方式创建一个普通控制随后使用它。  
  
### 将公共控件用作子窗口  
  
1.  定义相关类或处理程序的控件。  
  
2.  使用 [CWnd::Create](../Topic/CWnd::Create.md) 方法的控件之外创建 Windows 控件。  
  
3.  创建控件 \(早在 `OnCreate` 处理程序，则您子类控件\) 之后，可以使用其成员函数，可以操作控件。  参见各个控件的描述。[控件](../mfc/controls-mfc.md) 有关方法的详细信息。  
  
4.  在完成这一部分控件时，请使用 [CWnd::DestroyWindow](../Topic/CWnd::DestroyWindow.md) 销毁控件。  
  
## 请参阅  
 [创建和使用控件](../mfc/making-and-using-controls.md)   
 [控件](../mfc/controls-mfc.md)