---
title: "连接映射 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.maps"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "连接映射"
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# 连接映射
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE 控件可公开接口。其他应用程序。  这些接口只允许从容器的访问到该控件。  如果一个 OLE 控件中访问其他 OLE 对象外部界面，必须建立连接点。  此连接点允许控件外部到计划映射的传出访问，如事件映射或通知函数。  
  
 Microsoft 基础类 \(MFC\) 库提供支持连接点的编程模型。  在此模型中，连接“映射”使用指定接口或连接点 OLE 控件的。  连接映射每个连接点包含的宏。  有关连接映射的更多信息，请参见 [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md) 类。  
  
 通常，控件将支持两行：一个事件和一个属性通知的。  这些由 `COleControl` 基类实现并不会被控件编写需要额外的工作。  在类实现的任何其他连接点必须手动添加。  若要支持连接映射和点，MFC 提供下面的宏：  
  
### 声明连接映射和除法  
  
|||  
|-|-|  
|[BEGIN\_CONNECTION\_PART](../Topic/BEGIN_CONNECTION_PART.md)|声明其他实现的连接点的嵌入类 \(必须在类中声明\)。|  
|[END\_CONNECTION\_PART](../Topic/END_CONNECTION_PART.md)|结束连接点的声明 \(必须在类中声明\)。|  
|[CONNECTION\_IID](../Topic/CONNECTION_IID.md)|指定控件的连接点接口的 ID。|  
|[DECLARE\_CONNECTION\_MAP](../Topic/DECLARE_CONNECTION_MAP.md)|声明连接映射在类 \(必须在类中声明\)。|  
|[BEGIN\_CONNECTION\_MAP](../Topic/BEGIN_CONNECTION_MAP.md)|启动消息映射的定义 \(必须在类中实现。\)|  
|[END\_CONNECTION\_MAP](../Topic/END_CONNECTION_MAP.md)|启动消息映射的定义 \(必须在类中实现。\)|  
|[CONNECTION\_PART](../Topic/CONNECTION_PART.md)|控件中的连接映射指定连接点。|  
  
 使用连接点，以下函数会协助您生成程序和断开连接的一个接收器：  
  
### 连接点的初始化\/终止  
  
|||  
|-|-|  
|[AfxConnectionAdvise](../Topic/AfxConnectionAdvise.md)|生成接收器和源之间的连接。|  
|[AfxConnectionUnadvise](../Topic/AfxConnectionUnadvise.md)|中断接收器和源之间的连接。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)