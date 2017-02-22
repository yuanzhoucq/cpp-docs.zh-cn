---
title: "Elapsed Time: Automation Classes | Microsoft Docs"
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
  - "adding dates"
  - "Automation classes, 运行时间"
  - "calculating dates and times"
  - "计算, 日期和时间"
  - "日期, calculating intervals"
  - "运行时间, calculating in Automation"
  - "intervals, 日期和时间"
  - "时间, elapsed"
ms.assetid: 26b34b37-c10e-4b91-82c3-1dc5ffb5361f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Elapsed Time: Automation Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此过程演示如何计算两个 `CTime` 对象并获取之间的差异 `CTimeSpan` 结果。  
  
#### 计算经过的时间  
  
1.  创建两 `COleDateTime` 对象。  
  
2.  设置之一为当前时间的 `COleDateTime` 对象。  
  
3.  执行某些耗时任务。  
  
4.  设置为当前时间的另一 `COleDateTime` 对象。  
  
5.  拍摄区别在于这两个时间之间。  
  
     [!code-cpp[NVC_ATLMFC_Utilities#178](../atl-mfc-shared/codesnippet/CPP/elapsed-time-automation-classes_1.cpp)]  
  
## 请参阅  
 [Date and Time: Automation Support](../atl-mfc-shared/date-and-time-automation-support.md)