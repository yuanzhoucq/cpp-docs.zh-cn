---
title: "编译器错误 C2779 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2779"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2779"
ms.assetid: 4a00e492-855a-41f3-8a18-5f60ee20c2f2
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2779
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“declaration”: 属性方法只能与非静态数据成员关联  
  
 将 `property` 扩展特性错误地应用于静态数据成员。  
  
 下面的示例生成 C2779：  
  
```  
// C2779.cpp  
struct A {  
   static __declspec(property(put=PutProp))  
   // try the following line instead  
   __declspec(property(put=PutProp))  
      int prop;   // C2779  
   int PutProp(void);  
};  
```