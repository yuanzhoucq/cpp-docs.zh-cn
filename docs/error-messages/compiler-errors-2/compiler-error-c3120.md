---
title: "编译器错误 C3120 | Microsoft Docs"
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
  - "C3120"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3120"
ms.assetid: 9b6b210f-9948-4517-a4cc-b4aaadebde68
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3120
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“method\_name”: 接口方法不能采用变量参数列表  
  
 接口方法不能采用变量参数列表。  例如，下面的接口定义生成 C3120：  
  
```  
// C3120.cpp  
__interface A {  
int X(int i, ...);    // C3120  
};  
  
int main(void) { return(0); }  
```