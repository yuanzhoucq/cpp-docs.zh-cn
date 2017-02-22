---
title: "编译器错误 C2005 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2005"
ms.assetid: 090530ed-e0ec-4358-833a-ca24260e7ffe
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 编译器错误 C2005
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#line 应跟一个行号，却找到“token”  
  
 `#line` 指令后面必须跟行号。  
  
 下面的示例生成 C2005：  
  
```  
// C2005.cpp  
int main() {  
   int i = 0;  
   #line i   // C2005  
}  
```  
  
 可能的解决方案：  
  
```  
// C2005b.cpp  
int main() {  
   int i = 0;  
   #line 0  
}  
```