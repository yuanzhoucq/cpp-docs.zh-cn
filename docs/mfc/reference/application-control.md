---
title: "应用程序控件 | Microsoft Docs"
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
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "应用程序控件"
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
caps.latest.revision: 12
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 应用程序控件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE 需要对应用程序和其各自对象的严格的控制。  OLE 系统 DLL 必须能够启动，并且自动释放应用程序中，协调它们的生产和修改，等等。  本主题中的函数满足要求。  除了调用由 OLE 系统 DLL 外，必须由应用程序有时调用这些函数。  
  
### 应用程序控件  
  
|||  
|-|-|  
|[AfxOleCanExitApp](../Topic/AfxOleCanExitApp.md)|指示应用程序是否可以停止。|  
|[AfxOleGetMessageFilter](../Topic/AfxOleGetMessageFilter.md)|检索应用程序当前消息筛选器。|  
|[AfxOleGetUserCtrl](../Topic/AfxOleGetUserCtrl.md)|检索当前的控制标志。|  
|[AfxOleSetUserCtrl](../Topic/AfxOleSetUserCtrl.md)|集或明确控制标志。|  
|[AfxOleLockApp](../Topic/AfxOleLockApp.md)|添加活动的对象数的计数。框架的全局应用程序的。|  
|[AfxOleUnlockApp](../Topic/AfxOleUnlockApp.md)|递减活动对象个数的框架的计数。在应用程序中。|  
|[AfxOleRegisterServerClass](../Topic/AfxOleRegisterServerClass.md)|注册在 OLE 系统注册表的服务器。|  
|[AfxOleSetEditMenu](../Topic/AfxOleSetEditMenu.md)|命令对象实现 *类型* 的用户界面。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)