---
title: "编译器警告（等级 1）C4678 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4678"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4678"
ms.assetid: 0c588f34-595d-4e5c-9470-8723fca2cc06
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器警告（等级 1）C4678
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

基类“base\_type”的可访问性比“derived\_type”低  
  
 某个公共类型是从私有类型派生的。 如果在引用的程序集中实例化该公共类型，将无法访问私有基类型的成员。  
  
 只有使用 **\/clr:oldSyntax** 才可能出现 C4678 错误。 通过使用 **\/clr** 来获得可访问性比其派生类差的基类是错误的。  
  
 下面的示例生成 C4678：  
  
```  
// C4678.cpp // compile with: /clr:oldSyntax /LD /W1 #using <mscorlib.dll> private __gc struct privateG { // try the following line instead // public __gc struct privateG { public: int i; }; public __gc struct V: public privateG {   // C4678 public: int j; };  
```