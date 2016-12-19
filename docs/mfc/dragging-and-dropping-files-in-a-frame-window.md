---
title: "拖放框架窗口中的文件 | Microsoft Docs"
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
  - "拖放 [C++], 文件管理器"
  - "拖放 [C++], 文件"
  - "拖放 [C++], Windows Explorer"
  - "文件管理器拖放支持"
  - "文件 [C++], 拖放"
  - "框架窗口 [C++], 拖放文件"
  - "Windows 资源管理器 [C++]"
ms.assetid: 85560fe9-121b-4105-bd7b-216b966e19fa
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 拖放框架窗口中的文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

框架窗口管理用于文件管理器或文件管理器的关系。  
  
 通过将 `CWinApp` 成员函数 `InitInstance`的替代数组初始化的调用按 [CWinApp:应用程序类](../mfc/cwinapp-the-application-class.md)所描述的，因此，可以间接在框架窗口将文件资源管理器或文件管理器和删除的框架窗口打开文件。  参见 [文件管理器拖放](../mfc/special-cwinapp-services.md)。  
  
## 请参阅  
 [使用框架窗口](../mfc/using-frame-windows.md)