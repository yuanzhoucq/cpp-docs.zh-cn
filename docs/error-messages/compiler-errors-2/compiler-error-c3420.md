---
title: "编译器错误 C3420 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3420"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3420"
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 编译器错误 C3420
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“finalizer”: 终结器不能为虚  
  
 终结器只能从其封闭类型进行非虚拟调用。 因此，声明虚拟终结器是错误的。  
  
 有关更多信息，请参见[Visual C\+\+ 中的析构函数和终结器](../../misc/destructors-and-finalizers-in-visual-cpp.md)。  
  
## 示例  
 下面的示例生成 C3420。  
  
```  
// C3420.cpp // compile with: /clr /c ref class R { virtual !R() {}   // C3420 };  
```