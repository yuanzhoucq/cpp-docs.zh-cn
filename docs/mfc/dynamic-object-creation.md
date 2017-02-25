---
title: "动态对象创建 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObject 类, 动态对象创建"
  - "动态对象创建"
  - "对象创建, 在运行时动态地"
  - "对象 [C++], 在运行时动态地创建"
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 动态对象创建
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文说明如何动态在运行时创建对象。  过程使用运行时类信息，如 [访问运行时信息类](../mfc/accessing-run-time-class-information.md)文章所述。  
  
#### 动态创建给定的对象的运行时类  
  
1.  使用 `CRuntimeClass`的 `CreateObject` 函数，该函数使用下面代码动态创建对象。  请注意上失败， `CreateObject` 将返回 **NULL** 而不会引发异常：  
  
     [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/CPP/dynamic-object-creation_1.cpp)]  
  
## 请参阅  
 [使用 CObject](../mfc/using-cobject.md)