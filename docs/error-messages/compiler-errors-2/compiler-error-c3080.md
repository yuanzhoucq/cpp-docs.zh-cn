---
title: "编译器错误 C3080 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3080"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3080"
ms.assetid: ff62a3f7-9b3b-44bd-b8d9-f3a8e5354560
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3080
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“finalizer\_function”：终结器不能具有存储类说明符  
  
 有关详细信息，请参阅[Visual C\+\+ 中的析构函数和终结器](../../misc/destructors-and-finalizers-in-visual-cpp.md)。  
  
## 示例  
 下面的示例生成 C3080。  
  
```  
// C3080.cpp // compile with: /clr /c ref struct rs { protected: static !rs(){}   // C3080 !rs(){}   // OK };  
```