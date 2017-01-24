---
title: "ExitInstance 成员函数 | Microsoft Docs"
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
  - "CWinApp::ExitInstance"
  - "CWinApp.ExitInstance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWinApp 类, ExitInstance"
  - "ExitInstance 方法"
  - "程序 [C++], 终止"
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ExitInstance 成员函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CWinApp](../mfc/reference/cwinapp-class.md) [ExitInstance](../Topic/CWinApp::ExitInstance.md) 类的成员函数时通常调用，每次您的应用程序副本终止，可以退出应用程序的用户。  
  
 重写 `ExitInstance`，如果需要特殊处理清理，如释放图形设备接口 \(GDI\) 资源或释放在程序执行期间使用的内存。  \(文档和视图，而框架，提供标准清理项目，其他可重写的特定函数对执行清理特定于这些对象。  
  
## 请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)