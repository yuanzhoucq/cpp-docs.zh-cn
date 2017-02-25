---
title: "编译器错误 C3366 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3366"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3366"
ms.assetid: efc55bcf-c16d-43c1-a36f-87a6165fa2a8
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C3366
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“variable”：托管或 WinRT 类型的静态数据成员必须在类定义中定义  
  
 尝试在 WinRT 或 .NET 类\/接口定义外部引用该类或接口的静态成员。  
  
 编译器需要知道类的完整定义（以在一次传递后发出元数据）并要求在类中初始化静态数据成员。  
  
 例如，下面的示例生成 C3366，并演示如何修复此错误：  
  
```  
// C3366.cpp  
// compile with: /clr /c  
ref class X {  
   public:  
   static int i;   // initialize i here to avoid C3366  
};  
  
int X::i = 5;      // C3366  
```  
  
 下面的示例生成 C3366，并演示如何修复此错误：  
  
```  
// C3366_b.cpp  
// compile with: /clr:oldSyntax /c  
__gc struct X {  
   static int i;   // initialize i here to avoid C3366  
};  
  
int X::i = 5;      // C3366  
```