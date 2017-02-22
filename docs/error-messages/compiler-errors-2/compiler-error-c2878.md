---
title: "编译器错误 C2878 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2878"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2878"
ms.assetid: 83ee3de1-f554-49e8-a840-1f550cee7f69
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2878
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“name”: 此名称的命名空间或类不存在  
  
 引用了尚未定义的命名空间或类。  
  
 下面的示例生成 C2878：  
  
```  
// C2878.cpp  
// compile with: /c  
namespace A {}  
namespace B = C;   // C2878 namespace C doesn't exist  
namespace B = A;   
```