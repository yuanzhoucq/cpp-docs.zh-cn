---
title: "编译器错误 C3530 | Microsoft Docs"
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
  - "C3530"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3530"
ms.assetid: 21be81ce-b699-4c74-81bc-80a0c34d2d5a
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3530
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“auto”不能与其他任何类型说明符一起使用  
  
 某个类型说明符与 `auto` 关键字一起使用。  
  
### 更正此错误  
  
1.  不要在使用 `auto` 关键字的变量声明中使用类型说明符。  
  
## 示例  
 下面的示例会产生 C3530，因为同时用 `auto` 关键字和 `int` 类型声明 `x` 变量，还因为该示例是用 **\/Zc:auto** 编译的。  
  
```  
// C3530.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto int x;   // C3530  
   return 0;  
}  
```  
  
## 请参阅  
 [auto 关键字](../../cpp/auto-keyword.md)