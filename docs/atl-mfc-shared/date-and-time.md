---
title: "Date and Time | Microsoft Docs"
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
  - "日期, MFC"
  - "MFC, 日期和时间"
  - "时间"
  - "时间, MFC 编程"
ms.assetid: ecf56dc5-d418-4603-ad3e-af7e205a6403
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Date and Time
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC支持几种不同的方式处理日期和时间一起使用。  这些元素包括：  
  
-   泛型时选件类。  [CTime](../atl-mfc-shared/reference/ctime-class.md) 和 [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md) 选件类封装大多数功能与ANSI标准时间库，在TIME.H.声明。  
  
-   为系统时钟支持。  MFC 3.0版中，支持添加到Win32 `SYSTEMTIME` 和 `FILETIME` 数据类型的 `CTime`。  
  
-   用于自动化 [日期数据类型](../atl-mfc-shared/date-type.md)支持。  **DATE** 支持日期、时间和日期\/时间值。  [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) 和 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md) 选件类封装此功能。  它们与 [COleVariant](../mfc/reference/colevariant-class.md) 选件类使用自动化支持。  
  
## 您想进一步了解什么？  
  
-   [日期和时间:泛型选件类](../atl-mfc-shared/date-and-time-general-purpose-classes.md)  
  
-   [日期和时间:SYSTEMTIME支持](../atl-mfc-shared/date-and-time-systemtime-support.md)  
  
-   [日期和时间:自动化支持](../atl-mfc-shared/date-and-time-automation-support.md)  
  
-   [日期和时间:数据库支持](../atl-mfc-shared/date-and-time-database-support.md)  
  
## 请参阅  
 [概念](../mfc/mfc-concepts.md)   
 [常规 MFC 主题](../mfc/general-mfc-topics.md)