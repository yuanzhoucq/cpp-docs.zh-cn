---
title: "编译器错误 C2460 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2460"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2460"
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2460
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier1”: 使用正在定义的“identifier2”  
  
 将类或结构 \(`identifier2`\) 声明为其本身的成员 \(`identifier1`\)。  不允许类和结构的递归定义。  
  
 下面的示例生成 C2460：  
  
```  
// C2460.cpp  
class C {  
   C aC;    // C2460  
};  
```  
  
 请改为在类中使用指针引用。  
  
```  
// C2460.cpp  
class C {  
   C * aC;    // OK  
};  
```