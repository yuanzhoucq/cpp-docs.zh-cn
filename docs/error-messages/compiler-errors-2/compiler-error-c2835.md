---
title: "编译器错误 C2835 | Microsoft Docs"
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
  - "C2835"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2835"
ms.assetid: 41c70630-983f-4da2-8342-513cf48b0519
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2835
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用户定义的转换“type”不采用任何形参  
  
 用户定义的类型转换不能采用形参。  
  
 下面的示例生成 C2835：  
  
```  
// C2835.cpp  
class A {  
public:  
   char v_char;  
  
   A() {   
      v_char = 'A';   
   };  
   operator char(char a) {   // C2835  
   // try the following line instead  
   // operator char() {     
      return v_char + 1;   
   };  
};  
  
int main() {  
   A a;  
}  
```