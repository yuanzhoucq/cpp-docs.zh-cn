---
title: "用于创建 OLE 应用程序的操作顺序 | Microsoft Docs"
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
  - "应用程序 [OLE]"
  - "应用程序 [OLE], 创建"
  - "OLE 应用程序 [C++]"
  - "OLE 应用程序 [C++], 创建"
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用于创建 OLE 应用程序的操作顺序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表显示了角色和框架的角色在创建链接和 OLE 嵌入应用程序。  这些表示选项可用而不是执行步骤序列。  
  
### 创建应用程序  
  
|任务|You do|框架|  
|--------|------------|--------|  
|创建 COM 组件|运行神奇应用程序。  选择 **Full\-server** 或 **Mini\-server**。**复合文档支持** 选项卡。|框架生成启用了 COM 组件功能的主干应用程序。  所有 COM 功能可以传输到仅使用稍作修改现有应用程序。|  
|从头创建容器应用程序。|运行神奇应用程序。  选择 **复合文档支持** 选项卡中的 **容器 \(O\)**。  使用类视图，进入源代码编辑器。  填写 COM 处理程序函数的代码。|框架生成可以将 COM 组件的主干应用程序 \(\) 服务器应用程序创建的 COM 对象。|  
|从头创建支持自动化的应用程序。|运行神奇应用程序。  从 **高级功能** 选项卡选择 **自动化 \(U\)**。  使用类视图公开方法和属性。应用程序自动化。|框架生成可能由其他应用激活和自动化程序的主干应用程序。|  
  
## 请参阅  
 [基于框架生成](../mfc/building-on-the-framework.md)   
 [用于生成 MFC 应用程序的操作顺序](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [用于创建 ActiveX 控件的操作顺序](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [用于创建数据库应用程序的操作顺序](../mfc/sequence-of-operations-for-creating-database-applications.md)