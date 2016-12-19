---
title: "编译器错误 C2133 | Microsoft Docs"
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
  - "C2133"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2133"
ms.assetid: 8942f9e8-9818-468f-97db-09dbd124fcae
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2133
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 未知的大小  
  
 未确定大小的数组被声明为类、结构、联合或枚举的成员。  \/Za \(ANSI C\) 选项不允许使用未确定大小的成员数组。  
  
 下面的示例生成 C2133：  
  
```  
// C2133.cpp  
// compile with: /Za  
struct X {  
   int a[0];   // C2133 unsized array  
};  
```  
  
 可能的解决方案：  
  
```  
// C2133b.cpp  
// compile with: /c  
struct X {  
   int a[0];   // no /Za  
};  
```