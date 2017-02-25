---
title: "编译器错误 C3215 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3215"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3215"
ms.assetid: d0d16007-8885-42e0-b086-2d3a61f348c5
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3215
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type1”: 泛型类型参数已由“type2”进行约束  
  
 已多次指定约束。  
  
 有关泛型的详细信息，请参阅[泛型](../../windows/generics-cpp-component-extensions.md)。  
  
 下面的示例生成 C3215：  
  
```  
// C3215.cpp // compile with: /clr interface struct A {}; generic <class T> where T : A,A ref class C {};   // C3215  
```  
  
 可能的解决方法：  
  
```  
// C3215b.cpp // compile with: /clr /c interface struct A {}; generic <class T> where T : A ref class C {};  
```