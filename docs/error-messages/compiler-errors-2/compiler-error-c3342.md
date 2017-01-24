---
title: "编译器错误 C3342 | Microsoft Docs"
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
  - "C3342"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3342"
ms.assetid: 5c6d784f-bebe-4f7e-8615-44ca6f78bfba
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3342
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“attribute”：不明确的特性  
  
 编译器发现特性的多个定义。  
  
 多次定义了特性。  
  
 有关详细信息，请参阅[用户定义的特性](../../windows/user-defined-attributes-cpp-component-extensions.md)。  
  
## 示例  
 以下示例生成 C3342。  
  
```  
// C3342.cpp // compile with: /clr /c using namespace System; using namespace System::Reflection; [AttributeUsage(AttributeTargets::All)] public ref class XAttribute : public  Attribute {}; [AttributeUsage(AttributeTargets::All)] public ref class X : public Attribute {}; [X]   // C3342 could refer to X or XAttribute // try the following line instead // [XAttribute] public ref class Class4 {};  
```