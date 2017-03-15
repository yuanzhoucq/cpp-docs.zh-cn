---
title: "编译器错误 C2286 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2286"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2286"
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2286
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指向“identifier”表示的成员的指针已设置为“inheritance”— 忽略声明  
  
 类存在两种不同的指向成员的指针的表示形式。  
  
 有关详细信息，请参阅[继承关键字](../../cpp/inheritance-keywords.md)。  
  
## 示例  
 下面的示例生成 C2286：  
  
```  
// C2286.cpp  
// compile with: /c  
class __single_inheritance X;  
class __multiple_inheritance X;   // C2286  
class  __multiple_inheritance Y;   // OK  
```