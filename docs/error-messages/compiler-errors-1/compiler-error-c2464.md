---
title: "编译器错误 C2464 | Microsoft Docs"
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
  - "C2464"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2464"
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2464
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 不能使用“new”分配引用  
  
 使用 `new` 运算符分配了引用标识符。  引用不是内存对象，所以 `new` 无法返回指向它们的指针。  请使用标准变量声明语法声明引用。  
  
 下面的示例生成 C2464：  
  
```  
// C2464.cpp  
int main() {  
   new ( int& ir );   // C2464  
}  
```