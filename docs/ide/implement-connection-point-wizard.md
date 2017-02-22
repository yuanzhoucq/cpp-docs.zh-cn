---
title: "实现连接点向导 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.impl.cp.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "实现连接点向导 [C++]"
ms.assetid: c117f6c6-30f0-4adb-82b4-b1f34e0f0fa8
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 实现连接点向导
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

该向导实现 COM 对象的连接点。  可连接对象（即源）可为它自己的接口或任何输出接口公开连接点。  Visual C\+\+ 和 Windows 都提供有输出接口的类型库。  每个输出接口可由客户端在对象（即接收器）上实现。  
  
 有关更多信息，请参见 [ATL 连接点](../atl/atl-connection-points.md)。  
  
 **可用的类型库**  
 显示包含可以实现连接点的接口定义的可用类型库。  单击省略号按钮以找到包含要使用的类型库的文件。  
  
 **位置**  
 显示“可用的类型库”列表中当前选定的类型库的位置。  
  
 **接口**  
 显示定义包含在“可用的类型库”框中当前选定的类型库中的接口。  
  
|传输按钮|说明|  
|----------|--------|  
|**\>**|将“接口”列表中当前选定的接口名称添加到“实现连接点”列表。|  
|**\>\>**|将“接口”列表中可用的所有接口名称添加到“实现连接点”列表。|  
|**\<**|移除“实现连接点”列表中当前选定的接口名称。|  
|**\<\<**|移除“实现连接点”列表中当前列出的所有接口名称。|  
  
 **实现连接点**  
 显示单击“完成”时实现连接点的接口名称。  
  
## 请参阅  
 [实现连接点](../ide/implementing-a-connection-point-visual-cpp.md)