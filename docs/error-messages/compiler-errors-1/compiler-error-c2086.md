---
title: "编译器错误 C2086 | Microsoft Docs"
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
  - "C2086"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2086"
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2086
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 重定义  
  
 多次定义了该标识符，或者后面的声明与前一个不同。  
  
 C2086 也可能是增量编译引用的 C\# 程序集的结果。  重新生成该 C\# 程序集以解决此错误。  
  
 下面的示例生成 C2086：  
  
```  
// C2086.cpp  
main() {  
  int a;  
  int a;   // C2086 not an error in ANSI C  
}  
```