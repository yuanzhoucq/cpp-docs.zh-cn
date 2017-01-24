---
title: "是否存在无法用于 MFC DLL 的 MFC 类或函数？ | Microsoft Docs"
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
  - "DLL [C++], MFC"
  - "DLL [C++], 限制"
  - "MFC DLL [C++], 限制"
ms.assetid: 18e2f1cb-4f72-4d3a-a951-3488208872c7
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 是否存在无法用于 MFC DLL 的 MFC 类或函数？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

扩展 DLL 使用客户端应用程序的 `CWinApp` 派生类。  它们不能有自己的 `CWinApp` 派生类。  
  
 与 MFC 应用程序相同，规则 DLL 必须有一个 `CWinApp` 派生的类和此应用程序类的单个对象。  与应用程序的 `CWinApp` 对象不同，DLL 的 `CWinApp` 对象没有主消息泵。  
  
 请注意，由于`CWinApp::Run` 机制不适用于 DLL，因此应用程序拥有主消息泵。  如果 DLL 打开无模式对话框或有自己的主框架窗口，则应用程序的主消息泵必须调用由 DLL 导出的例程，该例程则调用 DLL 应用程序对象的 `CWinApp::PreTranslateMessage` 成员函数。  
  
## 请参阅  
 [DLL 常见问题](../build/dll-frequently-asked-questions.md)