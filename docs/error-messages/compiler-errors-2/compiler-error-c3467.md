---
title: "编译器错误 C3467 | Microsoft Docs"
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
  - "C3467"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3467"
ms.assetid: e2b844d0-4920-412f-99fd-cd8051c4aa41
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3467
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”：此类型已被转发  
  
 编译器找到了同一类型的多个转发类型声明。 每个类型只允许具有一个声明。  
  
 有关详细信息，请参阅[类型转发 \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md)。  
  
## 示例  
 下面的示例创建一个组件。  
  
```  
// C3467.cpp // compile with: /LD /clr public ref class R {};  
```  
  
## 示例  
 下面的示例生成 C3467。  
  
```  
// C3467_b.cpp // compile with: /clr /c #using "C3467.dll" [ assembly:TypeForwardedTo(R::typeid) ]; [ assembly:TypeForwardedTo(R::typeid) ];   // C3467  
```