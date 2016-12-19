---
title: "编译器错误 C2071 | Microsoft Docs"
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
  - "C2071"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2071"
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2071
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“标识符”：非法存储类  
  
 已使用无效的[存储类](../../c-language/c-storage-classes.md)声明 `identifier`。  为标识符指定多个存储类时或定义与存储类声明不兼容时，会导致此错误。  
  
 若要解决此问题，请了解标识符的预期存储类（例如，`static` 或  `extern`），并更正要匹配的声明。  
  
## 示例  
 以下示例生成 C2071。  
  
```  
// C2071.cpp  
// compile with: /c  
struct C {  
   extern int i;   // C2071  
};  
struct D {  
   int i;   // OK, no extern on an automatic  
};  
```  
  
## 示例  
 以下示例生成 C2071。  
  
```  
// C2071_b.cpp  
// compile with: /c  
typedef int x(int i) { return i; }   // C2071  
typedef int (x)(int);   // OK, no local definition in typedef  
```