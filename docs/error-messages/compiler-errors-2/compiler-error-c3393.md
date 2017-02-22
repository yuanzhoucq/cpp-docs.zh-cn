---
title: "编译器错误 C3393 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3393"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3393"
ms.assetid: d57f7c69-0a02-4fe3-9e45-bc62644fd77c
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3393
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

constraint 子句有语法错误：“identifier”不是一个类型  
  
 传递给约束的标识符必须是一种类型，但该标识符不是一种类型。  有关详细信息，请参阅[约束](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 示例  
 以下示例生成 C3393：  
  
```  
// C3393.cpp // compile with: /clr /c void MyInterface() {} interface class MyInterface2 {}; generic<typename T> where T : MyInterface   // C3393 // try the following line instead // where T : MyInterface2 ref class R {};  
```