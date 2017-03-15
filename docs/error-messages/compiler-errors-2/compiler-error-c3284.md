---
title: "编译器错误 C3284 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3824"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3284"
ms.assetid: e582f316-e9db-4d27-9c70-fdfa737a9d5f
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3284
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

函数“function”的泛型参数“parameter”的约束必须与函数“function”的泛型参数“paramete”的约束匹配  
  
 虚拟泛型函数所用的约束必须与基类中具有相同名称和参数集的虚拟函数的约束相同。  
  
 以下示例生成 C3284：  
  
```  
// C3284.cpp // compile with: /clr /c // C3284 expected public interface class IGettable { int Get(); }; public interface class B { generic<typename T> where T : IGettable virtual int mf(T t); }; public ref class D : public B { public: generic<typename T> // Uncomment the following line to resolve. // where T : IGettable virtual int mf(T t) { return 4; } };  
```