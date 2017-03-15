---
title: "可重写 CWinApp 成员函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CWinApp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序类"
  - "CWinApp 类, 可重写"
  - "重写, CWinApp 中的可重写函数"
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 可重写 CWinApp 成员函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CWinApp](../mfc/reference/cwinapp-class.md) 提供若干关键可重写的成员函数 \(`CWinApp` 重写类的以下 [CWinThread](../mfc/reference/cwinthread-class.md)成员，`CWinApp` 派生\):  
  
-   [InitInstance](../mfc/initinstance-member-function.md)  
  
-   [运行](../mfc/run-member-function.md)  
  
-   [ExitInstance](../mfc/exitinstance-member-function.md)  
  
-   [OnIdle](../mfc/onidle-member-function.md)  
  
 必须重写的 `CWinApp` 成员函数为 `InitInstance`。  
  
## 请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)