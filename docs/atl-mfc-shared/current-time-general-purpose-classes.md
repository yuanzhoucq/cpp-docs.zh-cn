---
title: "Current Time: General Purpose Classes | Microsoft Docs"
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
  - "当前时间, CTime object"
  - "初始化对象, with the current time"
  - "过程, getting current time"
  - "时间, getting current"
  - "时间, setting current"
ms.assetid: c39e6775-6a92-4b27-95a7-5c86ed371d8a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Current Time: General Purpose Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的过程演示如何创建 `CTime` 对象和初始化其与当前时间。  
  
#### 获取当前时间  
  
1.  分配一 `CTime` 对象，如下所示:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#171](../atl-mfc-shared/codesnippet/CPP/current-time-general-purpose-classes_1.cpp)]  
  
    > [!NOTE]
    >  未初始化的 `CTime` 对象未初始化为一个有效期。  
  
2.  调用 `CTime::GetCurrentTime` 函数获取从操作系统的当前时间。  此函数返回可用于设置 `CTime`的值 `CTime` 对象，例如:  
  
     [!code-cpp[NVC_ATLMFC_Utilities#172](../atl-mfc-shared/codesnippet/CPP/current-time-general-purpose-classes_2.cpp)]  
  
     因为 `GetCurrentTime` 是从 `CTime` 选件类的静态成员函数，必须限定其与选件类和范围解析运算符\(`::`\)，`CTime::GetCurrentTime()`的名称。  
  
 当然，以前的大纲显示两个步骤可以合并到一个程序语句如下所示:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#173](../atl-mfc-shared/codesnippet/CPP/current-time-general-purpose-classes_3.cpp)]  
  
## 请参阅  
 [Date and Time: General\-Purpose Classes](../atl-mfc-shared/date-and-time-general-purpose-classes.md)