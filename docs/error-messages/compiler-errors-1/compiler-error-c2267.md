---
title: "编译器错误 C2267 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2267"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2267"
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2267
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”: 具有块范围的静态函数非法  
  
 本地函数被声明为 `static`。  静态函数必须具有全局范围。  
  
 下面的示例生成 C2267：  
  
```  
// C2267.cpp  
static int func2();   // OK  
int main() {  
    static int func1();   // C2267  
}  
```