---
title: "编译器错误 C2120 | Microsoft Docs"
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
  - "C2120"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2120"
ms.assetid: b0f3f66c-6cd2-4f48-9ea3-c270b53c2b8c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2120
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

对于所有类型“void”非法  
  
 `void` 类型用于对其他类型的声明中。  
  
 下面的示例生成 C2120：  
  
```  
// C2120.cpp  
int main() {  
   void int i;   // C2120  
   int j;   // OK  
}  
```