---
title: "编译器错误 C2691 | Microsoft Docs"
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
  - "C2691"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2691"
ms.assetid: 6925f8f3-ea60-4909-91e6-b781492c645d
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2691
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“数据类型”：托管数组或 WinRT 数组不能具有此元素类型  
  
 托管数组元素或 WinRT 数组元素的类型可以是值类型或引用类型。  
  
 以下示例生成 C2691：  
  
```  
// C2691a.cpp  
// compile with: /clr  
class A {};  
  
int main() {  
   array<A>^ a1 = gcnew array<A>(20);   // C2691  
   array<int>^ a2 = gcnew array<int>(20);   // value type OK  
}  
```  
  
 以下示例生成 C2691：  
  
```  
// C2691b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
int main() {  
   int * a1 __gc[];   // C2691  
   int * a1 = new int [20];   // OK  
}  
```  
  
 如果尝试使用适用于 C\+\+ 的托管扩展来定义交错数组，也可能出现 C2691。  当前语法支持交错数组，有关详细信息请参阅[数组](../../windows/arrays-cpp-component-extensions.md)。  
  
 以下示例生成 C2691：  
  
```  
// C2691c.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
int main() {  
   Int32 myJaggedArray[][] = new Int32 [50][];   // C2691  
}  
```