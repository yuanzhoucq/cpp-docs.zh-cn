---
title: "编译器错误 C3923 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3923"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3923"
ms.assetid: db8838e9-6344-4cd6-83e0-a8abeb12c4c0
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C3923
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“member”：不允许在 WinRT 或托管类的成员函数中使用局部类、结构或联合定义  
  
## 示例  
 下列示例生成 C3923。  
  
```  
// C3923.cpp  
// compile with: /clr /c  
ref struct x {  
   void Test() {  
      struct a {};   // C3923  
      class b {};   // C3923  
      union c {};   // C3923  
   }  
};  
```