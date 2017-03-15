---
title: "编译器错误 C3076 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3076"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3076"
ms.assetid: 8a87b3e4-2c17-4b87-9622-ef0962d6a34e
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器错误 C3076
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“instance”: 无法将引用类型的实例“type”嵌入本机类型中  
  
 本机类型不能包含 CLR 类型的实例。  
  
 有关详细信息，请参阅[参考类型的 C\+\+ 堆栈语义](../../dotnet/cpp-stack-semantics-for-reference-types.md)。  
  
## 示例  
 下面的示例生成 C3076。  
  
```  
// C3076.cpp  
// compile with: /clr /c  
ref struct U {};  
  
struct V {  
   U y;   // C3076  
};  
  
ref struct W {  
   U y;   // OK  
};  
```