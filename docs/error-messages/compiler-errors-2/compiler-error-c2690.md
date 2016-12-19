---
title: "编译器错误 C2690 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2690"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2690"
ms.assetid: f165a806-14bd-4942-99b7-8a9fc7dea227
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2690
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”：不能对托管或 WinRT 数组执行指针算术  
  
 不允许对托管或 WinRT 数组执行指针算术。  使用数组索引表示法来遍历该数组。  
  
 **C\+\+ 托管扩展**  
  
 不允许对 [\_\_gc](../../misc/gc.md) 数组执行指针算术。  使用数组索引表示法来遍历该数组。  
  
 下面的示例生成 C2690：  
  
```  
// C2690b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
int main() {  
   String* x[] = new String*[10];  
   x[0] = "test";  
   Console::WriteLine(x[0]);  
   x++;   // C2690  
}  
```