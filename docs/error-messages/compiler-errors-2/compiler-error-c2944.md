---
title: "编译器错误 C2944 | Microsoft Docs"
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
  - "C2944"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2944"
ms.assetid: f209e668-e72f-442a-a438-8c4ff43a404a
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2944
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“class”：type\-class\-id 重新定义为模板的类形参数  
  
 你不能使用泛型类或模板类来代替符号作为模板值参数。  
  
 以下示例生成 C2944：  
  
```  
// C2944.cpp // compile with: /c template<class T> class TC { }; template <int TC<int> > struct X1 { };   // C2944 template <class T > struct X2 {};  
```  
  
 使用泛型时，也可能出现 C2944：  
  
```  
// C2944b.cpp // compile with: /clr /c generic<class T> ref class GC {}; template <int GC<int> > struct X2 { };   // C2944 template <class T> struct X3 {};   // OK  
```