---
title: "编译器错误 C3084 | Microsoft Docs"
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
  - "C3084"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3084"
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3084
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“函数”: 终结器\/析构函数不能是“关键字”  
  
 未正确声明终结器或析构函数。  
  
 例如，析构函数不应标记为密封。  派生类型无法访问析构函数。  有关详细信息，请参见[显式重写](../../windows/explicit-overrides-cpp-component-extensions.md)和 [Visual C\+\+ 中的析构函数和终结器](../../misc/destructors-and-finalizers-in-visual-cpp.md)。  
  
## 示例  
 以下示例生成 C3084。  
  
```  
// C3084.cpp // compile with: /clr /c ref struct R { protected: !R() sealed;   // C3084 !R() abstract;   // C3084 !R(); };  
```