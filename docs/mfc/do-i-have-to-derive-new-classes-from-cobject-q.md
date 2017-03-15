---
title: "我是否必须从 CObject 中派生新类？ | Microsoft Docs"
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
  - "CObject 类, 何时使用"
  - "派生类, 从 CObject"
ms.assetid: 26021031-feaf-424c-80d1-9547c4409d6a
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 我是否必须从 CObject 中派生新类？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不，你不会。  
  
 当你需要它提供的功能时从 [CObject](../mfc/reference/cobject-class.md) 派生一个类，例如序列化或动态的再造性。  许多数据类需要序列化到文件，因此，通常最好从 `CObject`派生。  从 `CObject`派生的有类的示例，请参见 [SCRIBBLE 示例](../top/visual-cpp-samples.md)。  
  
## 请参阅  
 [CObject 类：常见问题](../mfc/cobject-class-frequently-asked-questions.md)