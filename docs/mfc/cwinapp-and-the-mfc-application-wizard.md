---
title: "CWinApp 和 MFC 应用程序向导 | Microsoft Docs"
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
  - "CWinApp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序向导 [C++], 和 CWinApp"
  - "CWinApp 类, 和 MFC 应用程序向导"
  - "MFC [C++], 向导"
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWinApp 和 MFC 应用程序向导
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在创建主干应用程序时，MFC 应用程序向导声明应用程序类从派生。[CWinApp](../mfc/reference/cwinapp-class.md) MFC 应用程序向导还生成包含以下项实现的文件：  
  
-   应用程序的消息类映射。  
  
-   空的类构造函数。  
  
-   声明类的唯一对象的变量。  
  
-   `InitInstance` 成员函数的标准实现。  
  
 应用程序项目类在页眉和主源文件中。  创建的类和文件的名称基于您在 MFC 应用程序向导提供的项目名称。  简单的方法显示这些类的代码是通过 [类视图](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)。  
  
 提供的标准实现和消息映射用于多种目的是不够的，但您可以修改它们根据需要。  最值得关注这些实现是 `InitInstance` 成员函数。  通常，将代码添加到 `InitInstance`的骨骼实现。  
  
## 请参阅  
 [CWinApp：应用程序类](../mfc/cwinapp-the-application-class.md)   
 [可重写 CWinApp 成员函数](../mfc/overridable-cwinapp-member-functions.md)   
 [特殊 CWinApp 服务](../mfc/special-cwinapp-services.md)