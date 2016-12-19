---
title: "编译器警告（等级 1）C4162 | Microsoft Docs"
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
  - "C4162"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4162"
ms.assetid: 21ae3c92-501d-4689-ad7d-13753cb65eff
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 1）C4162
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“identifier”: 没有找到具有 C 链接的函数  
  
 声明了带有 C 链接的函数，但无法找到该函数。  
  
 若要消除此警告，请在 .c 文件中编译（调用 C 编译器）。如果必须调用 C\+\+ 编译器，请在声明函数之前放置外部“C”。  
  
 下面的示例生成 C4162  
  
```  
// C4162.cpp  
// compile with: /c /W1  
unsigned char _bittest(long* a, long b);  
#pragma intrinsic (_bittest)   // C4162  
  
int main() {  
   bool bit;  
   long num = 78002;  
   bit = _bittest(&num, 5);  
}  
```  
  
 可能的解决方案：  
  
```  
// C4162b.cpp  
// compile with: /c  
extern "C"  
unsigned char _bittest(long* a, long b);  
#pragma intrinsic (_bittest)  
  
int main() {  
   bool bit;  
   long num = 78002;  
   bit = _bittest(&num, 5);  
}  
```