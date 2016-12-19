---
title: "编译器错误 C3771 | Microsoft Docs"
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
  - "C3771"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3771"
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3771
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“标识符”: 在最近的命名空间范围内无法找到友元声明  
  
 无法在当前命名空间中找到指定模板的类模板声明*标识符*。  
  
### 更正此错误  
  
-   确保在当前命名空间中定义了模板标识符的类模板声明，或模板标识符是完全限定的名称。  
  
## 示例  
 下列代码示例在 `NA` 命名空间中声明一个类模板和函数，但试图在 `NB` 命名空间中声明友元函数模板。  
  
```  
// C3771.cpp // compile with: /c namespace NA { template<class T> class A { void aFunction(T t) {}; }; } // using namespace NA; namespace NB { class X { template<class T> friend void A<T>::aFunction(T); // C3771 // try the following line instead //      template<class T> friend void NA::A<T>::aFunction(T); // or try "using namespace NA;" instead. }; }  
```  
  
## 请参阅  
 [模板规范](../Topic/Template%20Specifications.md)