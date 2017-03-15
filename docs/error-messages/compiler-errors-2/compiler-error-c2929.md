---
title: "编译器错误 C2929 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2929"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2929"
ms.assetid: 11134027-6adc-4733-b6bd-b94486bd1933
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2929
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”：显式实例化；无法显式强制和取消模板类成员的实例化  
  
 不能在防止标识符实例化的同时对其进行显式实例化。  
  
 下面的示例生成 C2929：  
  
```  
// C2929.cpp // compile with: /c template<typename T> class A { public: A() {} }; template A<int>::A(); extern template A<int>::A();   // C2929  
```