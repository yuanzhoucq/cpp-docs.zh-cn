---
title: "编译器错误 C2728 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2728"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2728"
ms.assetid: 65635f91-1cd1-46e4-9ad7-14726d0546af
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# 编译器错误 C2728
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“type”：本机数组不能包含此类型  
  
 数组创建语法用于创建托管对象或 WinRT 对象的数组。  不能使用本机数组语法创建托管对象或 WinRT 对象的数组。  
  
 有关详细信息，请参阅[数组](../../windows/arrays-cpp-component-extensions.md)。  
  
 以下示例将生成 C2728，并演示如何修复此错误：  
  
```  
// C2728.cpp  
// compile with: /clr  
  
int main() {  
   int^ arr[5];   // C2728  
  
   // try the following line instead  
   array<int>^arr2;  
}  
```  
  
 [\_\_nogc](../../misc/nogc.md) 数组不能为 [\_\_gc](../../misc/gc.md) 类型。  
  
 以下示例将生成 C2728，并演示如何修复此错误：  
  
```  
// C2728_b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
int main() {  
   int __gc* arr __nogc[5];   // C2728  
  
   // try the following line instead  
   int arr2 __gc[];  
}  
```