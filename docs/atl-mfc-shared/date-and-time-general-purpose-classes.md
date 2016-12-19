---
title: "Date and Time: General-Purpose Classes | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "date and time classes"
  - "time classes"
ms.assetid: b8115d7f-428a-4c41-9970-18502f2caca2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Date and Time: General-Purpose Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文介绍如何利用选件类库的常规服务迄今相关的和时间线。  中介绍的过程包括:  
  
-   [获取当前时间](../atl-mfc-shared/current-time-general-purpose-classes.md)  
  
-   [计算经过的时间](../atl-mfc-shared/elapsed-time-general-purpose-classes.md)  
  
-   [设置一个日期\/时间的字符串表示形式](../atl-mfc-shared/formatting-time-values-general-purpose-classes.md)  
  
 `CTime` 选件类提供了一种轻松表示日期和时间信息。  `CTimeSpan` 选件类表示时间，例如两 `CTime` 对象之间的差异。  
  
> [!NOTE]
>  CTime对象可用来表示在1970年一月1日到2038年一月18日之间的日期。  `CTime` 对象具有解析1秒。  `CTime` 基于 `time_t` 数据类型，定义" *运行库参考*。  
  
## 请参阅  
 [Date and Time](../atl-mfc-shared/date-and-time.md)