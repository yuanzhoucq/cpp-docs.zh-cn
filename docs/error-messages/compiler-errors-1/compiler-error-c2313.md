---
title: "编译器错误 C2313 | Microsoft Docs"
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
  - "C2313"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2313"
ms.assetid: f70eb19b-c0a3-4fb2-ade1-3890a589928d
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2313
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type1”：由引用（“type2”）在行号上捕获  
  
 异常类型有两个处理程序。 第二个 catch 的类型是对第一个类型的引用。  
  
 以下示例生成 C2313：  
  
```  
// C2313.cpp // compile with: /EHsc #include <eh.h> class C {}; int main() { try { throw "ooops!"; } catch( C& ) {} catch( C ) {}   // C2313 }  
```