---
title: "编译器错误 C2428 | Microsoft Docs"
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
  - "C2428"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2428"
ms.assetid: 74aa5714-e930-4f9e-9061-68ccce7f0d38
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2428
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operation”: 在“bool”类型的操作数上不允许  
  
 无法将减量运算符应用于 `bool` 类型的对象。  
  
 下面的示例生成 C2428：  
  
```  
// C2428.cpp  
void g(bool fFlag) {  
   --fFlag;   // C2428  
   fFlag--;   // C2428  
}  
```