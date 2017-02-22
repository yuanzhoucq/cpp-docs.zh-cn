---
title: "编译器错误 C3063 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3063"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3063"
ms.assetid: 0ecf6f1f-e4a7-487a-9fd5-79d8ac470001
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C3063
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

运算符“operator”: 所有操作数必须具有相同的枚举类型  
  
 对枚举数使用运算符时，两个操作数必须都是枚举类型。  有关更多信息，请参见[使用运算符和枚举](../../misc/operators-and-enumerations.md)。  
  
 下面的示例生成 C3063：  
  
```  
// C3063.cpp  
// compile with: /clr  
enum class E { a, b } e, mask;  
int main() {  
   if ( ( e & mask ) != 0 ) ;   // C3063 no operator!= (E, int)  
  
   if ( ( e & mask ) != E() )   // OK  
      ;  
}  
```