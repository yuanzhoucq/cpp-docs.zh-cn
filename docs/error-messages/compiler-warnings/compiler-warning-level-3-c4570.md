---
title: "编译器警告（等级 3）C4570 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4570"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4570"
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器警告（等级 3）C4570
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 没有显式声明为抽象的，但具有抽象函数  
  
 包含 [abstract](../../windows/abstract-cpp-component-extensions.md) 函数的类型本身应标记为抽象类型。  
  
## 示例  
 下面的示例生成 C4570。  
  
```  
// C4570.cpp  
// compile with: /clr /W3 /c  
ref struct X {   // C4570  
// try the following line instead  
// ref class X abstract {  
   virtual void f() abstract;  
};  
```