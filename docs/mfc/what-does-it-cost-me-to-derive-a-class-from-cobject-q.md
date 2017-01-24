---
title: "从 CObject 派生类所带来的开销 | Microsoft Docs"
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
  - "CObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObject 类, 派生类的系统开销"
ms.assetid: 9b92c98b-b3dd-48a7-9d24-c3b8554edf90
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 从 CObject 派生类所带来的开销
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在派生类从 [CObject](../mfc/reference/cobject-class.md) 的开销非常小。  派生类继承四个虚函数和一个对象。[CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)  
  
## 请参阅  
 [CObject 类：常见问题](../mfc/cobject-class-frequently-asked-questions.md)