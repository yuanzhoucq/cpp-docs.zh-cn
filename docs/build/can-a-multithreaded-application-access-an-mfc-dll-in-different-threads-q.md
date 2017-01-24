---
title: "多线程应用程序是否可以通过不同的线程访问 MFC DLL？ | Microsoft Docs"
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
  - "DLL [C++], 多线程处理"
  - "MFC DLL [C++], 多线程处理"
  - "多线程处理 [C++], DLL"
  - "线程处理 [MFC], DLL"
ms.assetid: e3452e62-021e-4d23-9cce-cff41eb8b46b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 多线程应用程序是否可以通过不同的线程访问 MFC DLL？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

多线程应用程序可以通过不同的线程访问动态链接到 MFC 的规则 DLL 和扩展 DLL。  自 Visual C\+\+ 4.2 版起，应用程序可以通过在此应用程序中创建的多线程，访问静态链接到 MFC 的规则 DLL。  
  
 在 4.2 版之前，只有一个外部线程可以附加到静态链接到 MFC 的规则 DLL。  有关（在 Visual C\+\+ 4.2 版之前的版本中）通过多线程访问静态链接到 MFC 的规则 DLL 的限制的更多信息，请参见知识库文章“Multiple Threads and MFC \_USRDLLs”\(Q122676\)。  
  
 请注意，Visual C\+\+ 文档中不再使用 USRDLL 一词。  静态链接到 MFC 的规则 DLL 具有与原来的 USRDLL 相同的特性。  
  
## 请参阅  
 [DLL 常见问题](../build/dll-frequently-asked-questions.md)