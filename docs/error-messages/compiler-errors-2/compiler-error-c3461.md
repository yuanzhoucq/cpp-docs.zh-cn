---
title: "编译器错误 C3461 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3461"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3461"
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3461
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”：仅可转发托管类型  
  
 类型转发只会在 CLR 类型上发生。  有关更多信息，请参见[类和结构 \(托管\)](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 有关更多信息，请参见[类型转发 \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md)。  
  
## 示例  
 下面的示例创建一个组件。  
  
```  
// C3461.cpp // compile with: /clr /LD public ref class R {};  
```  
  
## 示例  
 下面的示例生成 C3461。  
  
```  
// C3461b.cpp // compile with: /clr /c #using "C3461.dll" class N {}; [assembly:TypeForwardedTo(N::typeid)];   // C3461 [assembly:TypeForwardedTo(R::typeid)];   // OK  
```