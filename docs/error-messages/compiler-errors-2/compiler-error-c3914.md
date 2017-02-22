---
title: "编译器错误 C3914 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3914"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3914"
ms.assetid: 8f3190e6-ee50-4916-9ecc-3b8748b2e1e7
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器错误 C3914
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

默认属性不能是静态属性  
  
 错误地声明了默认属性。有关详细信息，请参阅[如何：使用索引属性](../../misc/how-to-use-indexed-properties.md)。  
  
## 示例  
 下面的示例生成 C3914。  
  
```  
// C3914.cpp  
// compile with: /clr /c  
ref struct X {  
   static property int default[int] {   // C3914  
   // try the following line instead  
   // property int default[int] {  
      int get(int) { return 0; }  
      void set(int, int) {}  
   }  
};  
```