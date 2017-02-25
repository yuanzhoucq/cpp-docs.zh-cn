---
title: "Current Time: Automation Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Automation classes, 当前时间"
  - "当前时间, COleDateTime object"
  - "过程, getting current time"
  - "时间, getting current"
  - "时间, setting current"
ms.assetid: cc967f17-1189-4cf3-85f9-1969462d5f72
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Current Time: Automation Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的过程演示如何创建 `COleDateTime` 对象和初始化其与当前时间。  
  
#### 获取当前时间  
  
1.  创建 `COleDateTime` 对象。  
  
2.  调用 `GetCurrentTime`。  
  
     [!code-cpp[NVC_ATLMFC_Utilities#177](../atl-mfc-shared/codesnippet/CPP/current-time-automation-classes_1.cpp)]  
  
## 请参阅  
 [Date and Time: Automation Support](../atl-mfc-shared/date-and-time-automation-support.md)