---
title: "编译器错误 C2693 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2693"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2693"
ms.assetid: b7364ca8-b6be-48c0-97d6-6029787fb171
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# 编译器错误 C2693
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“运算符”：比较托管数组或 WinRT 数组的引用是非法的  
  
 你不能测试托管数组或 WinRT 数组的任何不相等情况。  例如，你可以测试托管数组是否相等，但不能测试其中一个数组是大于还是小于另一个数组。  
  
 **C\+\+ 托管扩展**  
  
 你不能测试 [\_\_gc](../../misc/gc.md) 数组的任何不相等情况。  例如，你可以测试托管数组是否相等，但不能测试其中一个数组是大于还是小于另一个数组。  
  
 下面的示例生成 C2693：  
  
```  
// C2693b.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
int func3(int a __gc[], int b __gc[]) {  
   return a < b;    // C2693  
}  
int func1(int a __gc[], int b __gc[]) {  
   return a != b;   // OK  
}  
  
int func2(int a __gc[], int b __gc[]) {  
   return a == b;   // OK  
}  
```