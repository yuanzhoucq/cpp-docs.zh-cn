---
title: "不通过代码向导对控件进行类型安全的访问 | Microsoft Docs"
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
  - "对话框控件, 访问"
  - "对话框, 访问控件"
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 不通过代码向导对控件进行类型安全的访问
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建为类型安全访问权限的第一种方法为控件使用内联成员函数转换类 `CWnd` 的 `GetDlgItem` 成员函数的返回类型到 C\+\+ 控件适当的类型，如此示例所示：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/CPP/type-safe-access-to-controls-without-code-wizards_1.cpp)]  
  
 然后可以使用该成员函数访问控件以使用代码的类型安全方法如下所示：  
  
 [!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/CPP/type-safe-access-to-controls-without-code-wizards_2.cpp)]  
  
## 请参阅  
 [对对话框中的控件进行类型安全的访问](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [通过代码向导对控件进行类型安全的访问](../mfc/type-safe-access-to-controls-with-code-wizards.md)