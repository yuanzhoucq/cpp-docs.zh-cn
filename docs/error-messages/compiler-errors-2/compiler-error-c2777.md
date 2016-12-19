---
title: "编译器错误 C2777 | Microsoft Docs"
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
  - "C2777"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2777"
ms.assetid: 5fe158c0-2a65-488a-aca2-61d4a8b32d43
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2777
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

每个属性只能指定一个“put”方法  
  
 [属性](../../cpp/property-cpp.md) declspec 修饰符有多个 `put` 属性。  
  
 下面的示例生成 C2777：  
  
```  
// C2777.cpp  
struct A {  
   __declspec(property(put=PutProp,put=PutPropToo))   // C2777  
   // try the following line instead  
   // __declspec(property(put=PutProp))  
      int prop;  
   int PutProp(void);  
   int PutPropToo(void);  
};  
```