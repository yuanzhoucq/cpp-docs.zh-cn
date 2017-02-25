---
title: "编译器错误 C3464 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3464"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3464"
ms.assetid: 0ede05dc-4486-4921-8e8c-78ab5a2e09c5
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3464
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”嵌套类型不能被转发  
  
 嵌套类型上不能进行类型转发。  
  
 有关详细信息，请参阅[类型转发 \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md)。  
  
## 示例  
 下面的示例创建一个组件。  
  
```  
// C3464.cpp // compile with: /LD /clr public ref class R { public: ref class N {}; };  
```  
  
## 示例  
 下面的示例生成 C3464。  
  
```  
// C3464_b.cpp // compile with: /clr /c #using "C3464.dll" [assembly:TypeForwardedTo(R::N::typeid)];   // C3464 [assembly:TypeForwardedTo(R::typeid)];   // OK  
```