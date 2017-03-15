---
title: "编译器错误 C2498 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2498"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2498"
ms.assetid: 0839f12c-aaa4-4a02-bb33-7f072715dd14
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# 编译器错误 C2498
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”:“novtable”只能应用于类声明或定义  
  
 此错误可能是由使用具有函数的 `__declspec(novtable)` 引起的。  
  
## 示例  
 下面的示例生成 C2498：  
  
```  
// C2498.cpp  
// compile with: /c  
void __declspec(novtable) f() {}   // C2498  
class __declspec(novtable) A {};   // OK  
```