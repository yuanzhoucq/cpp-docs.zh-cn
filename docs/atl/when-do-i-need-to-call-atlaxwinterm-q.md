---
title: "When Do I Need to Call AtlAxWinTerm? | Microsoft Docs"
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
  - "AtlAxWinTerm"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AtlAxWinTerm method"
ms.assetid: 0088d494-2d8d-45b4-b582-2af726bd6cbd
caps.latest.revision: 12
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# When Do I Need to Call AtlAxWinTerm?
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[AtlAxWinTerm](../Topic/AtlAxWinTerm.md) 取消 **"AtlAxWin80"** 窗口选件类。  您应调用此函数\(如果不再需要创建宿主窗口\)，在销毁后所有现有宿主窗口。  如果不调用此函数，窗口选件类将自动中注销，在进程停止。  
  
## 请参阅  
 [When Do I Need to Call AtlAxWinInit?](../atl/when-do-i-need-to-call-atlaxwininit-q.md)   
 [控件包含常见问题](../atl/atl-control-containment-faq.md)