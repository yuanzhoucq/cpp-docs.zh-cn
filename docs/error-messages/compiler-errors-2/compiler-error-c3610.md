---
title: "编译器错误 C3610 | Microsoft Docs"
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
  - "C3610"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3610"
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3610
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“valuetype”: 必须将值类型“装箱”，才能调用方法“method”  
  
 默认情况下，值类型不在托管堆上。  需要先将值类型移到托管堆上，然后才能从 .NET 运行时类（如 `Object`）调用方法。  
  
 只有使用 **\/clr:oldSyntax** 才能访问 C3610。  
  
 下面的示例生成 C3610：  
  
```  
// C3610.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__value class A {};  
  
int main() {  
   A a;  
   a.GetType(); // C3610  
  
   // OK  
   __box A* ovar = __box(a);  
   ovar->GetType();  
}  
```