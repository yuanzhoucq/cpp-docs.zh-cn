---
title: "编译器错误 C3468 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3468"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3468"
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3468
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”: 只能将类型转发到程序集:  
  
 “`file`”不是程序集  
  
 只能转发程序集中的类型。  
  
 有关详细信息，请参阅[类型转发 \(C\+\+\/CLI\)](../../windows/type-forwarding-cpp-cli.md)。  
  
## 示例  
 下面的示例创建一个模块。  
  
```  
// C3468.cpp // compile with: /LN /clr public ref class R {};  
```  
  
## 示例  
 下面的示例生成 C3468。  
  
```  
// C3468_b.cpp // compile with: /clr /c #using "C3468.netmodule" [ assembly:TypeForwardedTo(R::typeid) ];   // C3468  
```