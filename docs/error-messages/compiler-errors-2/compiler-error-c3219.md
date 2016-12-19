---
title: "编译器错误 C3219 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3219"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3219"
ms.assetid: 9c9757b0-1256-4cdf-9d8c-a3a72f300ce5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3219
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“param”: 泛型参数不能由多个非接口“class”进行约束  
  
 由两个或更多托管类约束泛型参数是无效的。  
  
 下面的示例生成 C3219：  
  
```  
// C3219.cpp // compile with: /clr ref class A {}; ref class B {}; generic <class T> where T : A, B ref class E {};   // C3219  
```  
  
 以下示例演示了可能的解决方法：  
  
```  
// C3219b.cpp // compile with: /clr /c ref class A {}; interface struct C {}; generic <class T> where T : A ref class E {};  
```