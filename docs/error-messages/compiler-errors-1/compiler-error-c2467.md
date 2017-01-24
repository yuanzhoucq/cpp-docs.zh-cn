---
title: "编译器错误 C2467 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2467"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2467"
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2467
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非法的匿名“user\-defined\-type”声明  
  
 声明了嵌套的用户定义类型。  如果在启用 ANSI 兼容选项 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 的情况下编译 C 源代码，则这是一个错误。  
  
 下面的示例生成 C2467：  
  
```  
//C2467.c  
// compile with: /Za   
int main() {  
   struct X {  
      union { int i; };   // C2467, nested declaration  
   };  
}  
```