---
title: "编译器错误 C3223 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3223"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3223"
ms.assetid: 1f4380b4-0413-40db-a868-62f97babaf78
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C3223
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“property”：不能将“typeid”应用于属性  
  
 不能将 [typeid](../../windows/typeid-cpp-component-extensions.md) 应用于属性。  
  
## 示例  
 以下示例生成 C3223。  
  
```  
// C3223.cpp // compile with: /clr ref class R { public: property int myprop; }; int main() { System::Type^ type2 = R::myprop::typeid;   // C3223 }  
```