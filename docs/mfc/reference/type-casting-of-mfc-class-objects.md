---
title: "MFC 类对象的类型强制转换 | Microsoft Docs"
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
  - "vc.mfc.macros.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "强制转换类型"
  - "宏, 强制转换指针"
  - "宏, 类型强制转换"
  - "指针, 类型强制转换"
  - "类型强制转换"
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
caps.latest.revision: 15
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 类对象的类型强制转换
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

类型强制宏的一种转换特定指针到指向特定类对象的指针，可带也可不检查转换是非法的。  
  
 下表列出了 MFC 类型强制宏。  
  
### 转换指向 MFC 类对象的宏  
  
|||  
|-|-|  
|[DYNAMIC\_DOWNCAST](../Topic/DYNAMIC_DOWNCAST.md)|转换指针到指向类对象，同时检查时转换是非法的。|  
|[STATIC\_DOWNCAST](../Topic/STATIC_DOWNCAST.md)|转换为指针从一类的对象向相关类型的指针。  在调试版本中，原因，如果 **ASSERT** 对象是一“目标类型。|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)