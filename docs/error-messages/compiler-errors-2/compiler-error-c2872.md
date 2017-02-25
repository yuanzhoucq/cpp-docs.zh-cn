---
title: "编译器错误 C2872 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2872"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2872"
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C2872
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”: 不明确的符号  
  
 编译器无法确定要引用哪个符号。  
  
 如果头文件包含 [using 指令](../../misc/using-directive-cpp.md)，并且后续的头文件已使用 `#include` 并包含一个也位于 `using` 指令中指定的命名空间中的类型，则会出现 C2872 错误。  仅在使用 `#include` 指定所有头文件后，才能指定 `using` 指令。  
  
 有关 C2872的更多信息， 查看[http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;316317](http://support.microsoft.com/default.aspx?scid=kb;en-us;316317)。  
  
 下面的示例生成 C2872：  
  
```  
// C2872.cpp  
namespace A {  
   int i;  
}  
  
using namespace A;  
int i;  
int main() {  
   ::i++;   // ok  
   A::i++;   // ok  
   i++;   // C2872 ::i or A::i?  
}  
```