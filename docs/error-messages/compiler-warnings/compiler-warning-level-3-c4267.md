---
title: "编译器警告（等级 3）C4267 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4267"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4267"
ms.assetid: 2fa2f13f-fa4f-47bb-ad8f-6cb19cfc91e6
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# 编译器警告（等级 3）C4267
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“var”：从“size\_t”转换到“type”，可能丢失数据  
  
 编译器检测到从 `size_t` 到更小类型的转换。  
  
 若要解决此警告，请使用 `size_t` 而不是 `type`。  或者，使用至少与 `size_t` 一样大的整型类型。  
  
## 示例  
 下面的示例生成 C4267。  
  
```  
// C4267.cpp  
// compile by using: cl /W4 C4267.cpp  
void Func1(short) {}  
void Func2(int) {}  
void Func3(long) {}  
void Func4(size_t) {}  
  
int main() {  
   size_t bufferSize = 10;  
   Func1(bufferSize);   // C4267 for all platforms  
   Func2(bufferSize);   // C4267 only for 64-bit platforms  
   Func3(bufferSize);   // C4267 only for 64-bit platforms  
   Func4(bufferSize);   // OK for all platforms  
}  
```