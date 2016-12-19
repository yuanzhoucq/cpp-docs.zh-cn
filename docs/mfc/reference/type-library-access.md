---
title: "类型库访问 | Microsoft Docs"
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
  - "vc.mfc.macros"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类型库, 访问"
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
caps.latest.revision: 14
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 类型库访问
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

类型库公开一个 OLE 控件的接口与其他与识别应用程序。  如果一个或多个接口将公开，每 OLE 控件必须具有类型库。  
  
 以下宏允许一个 OLE 控件提供对其自己的类型库：  
  
### 类型库访问  
  
|||  
|-|-|  
|[DECLARE\_OLETYPELIB](../Topic/DECLARE_OLETYPELIB.md)|声明一个 OLE 控件的 `GetTypeLib` 成员函数 \(必须在类中声明\)。|  
|[IMPLEMENT\_OLETYPELIB](../Topic/IMPLEMENT_OLETYPELIB.md)|实现 OLE 控件的 `GetTypeLib` 成员函数 \(必须在类中实现。\)|  
  
## 请参阅  
 [MFC 宏和全局函数](../../mfc/reference/mfc-macros-and-globals.md)