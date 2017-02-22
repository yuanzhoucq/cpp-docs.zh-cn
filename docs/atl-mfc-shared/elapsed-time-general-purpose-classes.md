---
title: "Elapsed Time: General-Purpose Classes | Microsoft Docs"
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
  - "calculating dates and times"
  - "计算, 日期和时间"
  - "日期, calculating intervals"
  - "运行时间"
  - "运行时间, 计算"
  - "intervals, 日期和时间"
  - "时间, elapsed"
ms.assetid: e5c5d3d2-ce1d-409e-875c-98848434e716
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Elapsed Time: General-Purpose Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的过程演示如何计算两个 `CTime` 对象并获取之间的差异 `CTimeSpan` 结果。  
  
#### 计算经过的时间  
  
1.  使用 `CTime` 和 `CTimeSpan` 对象计算经过的时间，如下所示:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#174](../atl-mfc-shared/codesnippet/CPP/elapsed-time-general-purpose-classes_1.cpp)]  
  
     一旦计算 `elapsedTime`，可以使用 `CTimeSpan` 的成员函数提取时间值的元素。  
  
## 请参阅  
 [Date and Time: General\-Purpose Classes](../atl-mfc-shared/date-and-time-general-purpose-classes.md)