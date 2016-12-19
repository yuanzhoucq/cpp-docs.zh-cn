---
title: "编译器错误 C2696 | Microsoft Docs"
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
  - "C2696"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2696"
ms.assetid: 6c6eb7df-1230-4346-9a73-abf14c20785d
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2696
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法创建托管类型“type”的临时对象  
  
 对非托管程序中 `const` 的引用导致编译器调用构造函数并在堆栈上创建临时对象。  但是，永远不能在堆栈上创建托管类。  
  
 只有使用 **\/clr:oldSyntax** 才能访问 C2696。  
  
 下面的示例生成 C2696：  
  
```  
// C2696b.cpp  
// compile with: /clr:oldSyntax  
  
__gc class G {  
public:  
   G( int i ) {}  
};  
  
void func( const G& g );  
  
int main() {  
   func( 1 );   // C2696  
   G *myG = new G( 1 );   // OK  
   func( *myG );  
}  
```