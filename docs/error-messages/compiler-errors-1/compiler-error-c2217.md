---
title: "编译器错误 C2217 | Microsoft Docs"
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
  - "C2217"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2217"
ms.assetid: 1ce1e3f5-4171-4376-804d-967f7e612935
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2217
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“attribute1”需要“attribute2”  
  
 第一个函数特性需要第二个特性。  
  
### 通过检查以下可能的原因进行修复  
  
1.  中断函数 \(`__interrupt`\) 声明为 `near`。  中断函数必须为 `far`。  
  
2.  中断函数是用 `__stdcall` 或 `__fastcall` 声明的。  中断函数必须使用 C 调用约定。  
  
## 示例  
 如果您尝试将委托绑定到使用数目可变的参数的 CLR 函数，则也会发生 C2217。  如果该函数还有一个参数数组重载，请改用此重载。  下面的示例生成 C2217。  
  
```  
// C2217.cpp  
// compile with: /clr  
using namespace System;  
delegate void MyDel(String^, Object^, Object^, ...);   // C2217  
delegate void MyDel2(String ^, array<Object ^> ^);   // OK  
  
int main() {  
   MyDel2^ wl = gcnew MyDel2(Console::WriteLine);  
   array<Object ^ > ^ x = gcnew array<Object ^>(2);  
   x[0] = safe_cast<Object^>(0);  
   x[1] = safe_cast<Object^>(1);  
  
   // wl("{0}, {1}", 0, 1);  
   wl("{0}, {1}", x);  
}  
```