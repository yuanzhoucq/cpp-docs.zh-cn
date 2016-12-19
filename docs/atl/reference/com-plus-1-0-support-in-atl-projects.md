---
title: "ATL 项目中的 COM+ 1.0 支持 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.ATL.MTS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 项目, COM+ 1.0 支持"
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 项目中的 COM+ 1.0 支持
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以使用 [ATL 项目向导](../../atl/reference/creating-an-atl-project.md)创建具有基本 COM\+ 1.0 组件支持的项目。  
  
 COM\+ 1.0 旨在开发基于组件的分布式应用程序。  它还提供用于部署和管理这些应用程序的运行时结构。  
  
 如果选择“支持 COM\+ 1.0”复选框，向导将修改链接步骤中的生成脚本。  具体说来，COM\+ 1.0 项目链接到下列库：  
  
-   comsvcs.lib  
  
-   Mtxguid.lib  
  
 如果选择“支持 COM\+ 1.0”复选框，则也可以选择“支持部件注册器”。  组件注册器使 COM\+ 1.0 对象得以获取组件列表、注册组件或注销组件（个别或同时）。  
  
## 请参阅  
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)