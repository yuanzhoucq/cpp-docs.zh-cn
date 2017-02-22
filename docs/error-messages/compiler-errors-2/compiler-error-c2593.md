---
title: "编译器错误 C2593 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2593"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2593"
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2593
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator identifier”不明确  
  
 为重载运算符定义了多个可能的运算符。  
  
 如果对一个或多个实参使用显式强制转换，可能会修复此错误。  
  
 下面的示例生成 C2593：  
  
```  
// C2593.cpp  
struct A {};  
struct B : A {};  
struct X {};  
struct D : B, X {};  
void operator+( X, X );  
void operator+( A, B );  
D d;  
  
int main() {  
   d +  d;         // C2593, D has an A, B, and X   
   (X)d + (X)d;    // OK, uses operator+( X, X )  
}  
```  
  
 使用 `CArchive` 对象序列化浮点变量可导致此错误。  编译器将 `<<` 运算符标识为不明确的。  `CArchive` 可序列化的唯一的基元 C\+\+ 类型是固定大小的类型 `BYTE`、`WORD`、`DWORD` 和 `LONG`。  所有的 integer 类型必须强制转换为这些类型之一才能进行序列化。  必须使用 `CArchive::Write()` 成员函数将浮点类型存档。  
  
 下面的示例说明如何将浮点变量 \(`f`\) 存档到 `ar` 存档中：  
  
```  
ar.Write(&f, sizeof( float ));  
```