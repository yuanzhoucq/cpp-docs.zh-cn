---
title: "编译器错误 C2318 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2318"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2318"
ms.assetid: 169e30b9-df78-46cb-90bf-576ad3c32fd4
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2318
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

没有与该 catch 处理程序关联的 Try 块  
  
 定义一个 `catch` 处理程序，但其前面没有 `try` 块。  
  
 以下示例生成 C2318：  
  
```  
// C2318.cpp // compile with: /EHsc #include <eh.h> int main() { // no try block catch( int ) {}   // C2318 }  
```  
  
 可能的解决方法：  
  
```  
// C2318b.cpp // compile with: /EHsc #include <eh.h> int main() { try{} catch( int ) {} }  
```