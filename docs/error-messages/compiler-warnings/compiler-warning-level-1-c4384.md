---
title: "编译器警告（等级 1）C4384 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4384"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4384"
ms.assetid: fafa8eb2-cbfc-4edb-8b0f-511ff5d37ac0
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器警告（等级 1）C4384
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma“make\_public”只应用在全局范围上  
  
 没有正确应用 [make\_public](../../preprocessor/make-public.md) 杂注。  
  
## 示例  
 下面的示例生成 C4384。  
  
```  
// C4384.cpp  
// compile with: /c /W1  
namespace n {  
   #pragma make_public(N::C)   // C4384  
   namespace N {  
      class C {};  
   }  
}  
```