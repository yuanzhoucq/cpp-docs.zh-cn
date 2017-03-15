---
title: "When Do I Need to Call AtlAxWinInit? | Microsoft Docs"
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
  - "AtlAxWinInit"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AtlAxWinInit method"
ms.assetid: 080b9cfe-d85a-4439-a9e9-ab3966ebaa8e
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# When Do I Need to Call AtlAxWinInit?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

必须进行调用[AtlAxWinInit](../Topic/AtlAxWinInit.md) 注册 **"AtlAxWin80"** 窗口选件类\(以及两个自定义windows消息\)此功能，在尝试创建宿主窗口之前。  但是，您始终不需要显式调用此函数，因为使用这些控件\)的承载API \(和选件类通常将调用此函数。  不在多次调用此函数的损害。  有关更多信息，请参见 [什么是控件承载API ATL?](../atl/what-is-the-atl-control-hosting-api-q.md)。  
  
## 请参阅  
 [When Do I Need to Call AtlAxWinTerm?](../atl/when-do-i-need-to-call-atlaxwinterm-q.md)   
 [控件包含常见问题](../atl/atl-control-containment-faq.md)