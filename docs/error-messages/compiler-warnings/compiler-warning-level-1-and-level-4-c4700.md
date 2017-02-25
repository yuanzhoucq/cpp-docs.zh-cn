---
title: "编译器警告（等级 1 和等级 4）C4700 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4700"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4700"
ms.assetid: 2da0deb4-77dd-4b05-98d3-b78d74ac4ca7
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器警告（等级 1 和等级 4）C4700
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用未初始化的局部变量“name”  
  
 您使用了事先未被分配值的局部变量 *name*，这将导致不可预知的结果。  
  
 下面的示例生成 C4700：  
  
```  
// C4700.cpp  
// compile with: /W1  
int main() {  
   int i;  
   return i;   // C4700  
}  
```  
  
 在 [\/clr:safe](../../build/reference/clr-common-language-runtime-compilation.md) 下，这是一个等级 4 的警告。下面的示例生成 C4700：  
  
```  
// C4700b.cpp  
// compile with: /W4 /clr:safe /c  
using namespace System;  
int main() {  
   Int32^ bi;  
   return *bi;   // C4700  
}  
```