---
title: "编译器错误 C2657 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2657"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2657"
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 编译器错误 C2657
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在语句的开始处找到“class::\*”\(是否忘记指定类型?\)  
  
 该行以指向成员的指针的标识符开始。  
  
 此错误可能是由于在指向成员的指针的声明中缺少类型说明符所致。  
  
 下面的示例生成 C2657：  
  
```  
// C2657.cpp  
class C {};  
int main() {  
   C::* pmc1;        // C2657  
   int C::* pmc2;   // OK  
}  
```