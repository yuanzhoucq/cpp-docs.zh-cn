---
title: "编译器错误 C2726 | Microsoft Docs"
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
  - "C2726"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2726"
ms.assetid: f0191bb7-c175-450b-bf09-a3213db96d09
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2726
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“gcnew”只能用于创建具有托管或 WinRT 类型的对象  
  
 不能在垃圾回收堆上创建本机类型的实例。  
  
 下面的示例生成 C2726，并演示如何修复此错误：  
  
```  
// C2726.cpp  
// compile with: /clr  
using namespace System;  
class U {};  
ref class V {};  
value class W {};  
  
int main() {  
   U* pU = gcnew U;    // C2726  
   U* pU2 = new U;   // OK  
   V^ p2 = gcnew V;   // OK  
   W p3;   // OK  
  
}  
```  
  
 下面的示例生成 C2726，并演示如何修复此错误：  
  
```  
// C2726b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
class U {};  
__gc class V {};  
  
int main() {  
   U* pU = __gc new U;    // C2726  
   U* pU2 = new U;    // OK  
   V* p2 = __gc new V;  
}  
```