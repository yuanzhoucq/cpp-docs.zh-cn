---
title: "编译器错误 C3077 | Microsoft Docs"
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
  - "C3077"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3077"
ms.assetid: d9f3c619-d1e2-4656-81a5-a35a9586a7d4
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3077
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“finalizer”：终结器只能是引用类型的成员  
  
 不能在本机类型或值类型中声明终结器。  
  
 有关更多信息，请参见[Visual C\+\+ 中的析构函数和终结器](../../misc/destructors-and-finalizers-in-visual-cpp.md)。  
  
## 示例  
 下面的示例生成 C3077。  
  
```  
// C3077.cpp // compile with: /clr /c value struct vs { !vs(){}   // C3077 }; ref struct rs { protected: !rs(){}   // OK };  
```