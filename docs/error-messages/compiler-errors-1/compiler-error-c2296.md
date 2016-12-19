---
title: "编译器错误 C2296 | Microsoft Docs"
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
  - "C2296"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2296"
ms.assetid: 47d270f4-13ce-4c16-81e2-7d67c6c4a540
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2296
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”: 左操作数错误  
  
 与 `operator` 一起使用的左操作数无效。  
  
 例如，编译器可能发现在应该出现函数调用的位置出现声明。  
  
 下面的示例生成 C2296：  
  
```  
// C2296.cpp  
struct MyStruct {  
   struct Help {  
      Help(float f) : m_f(f) {}  
      float m_f;  
   };  
  
   MyStruct(const Help &h) : m_f(h.m_f) {}  
   MyStruct(float f) : m_f(f) {}  
   MyStruct operator*(const MyStruct &f1) const {   
      return MyStruct(m_f * f1.m_f);  
   }  
  
private:  
   float m_f;  
};  
  
int main() {  
   float f1 = 1.0f;  
  
   MyStruct m_MyStruct1 ( MyStruct::Help( f1 ) );  
   // try the following line instead  
   // MyStruct m_MyStruct1 = MyStruct::Help( f1 );  
  
   MyStruct m_MyStruct2 ( MyStruct::Help( f1 ) );  
   // try the following line instead  
   // MyStruct m_MyStruct2 = MyStruct::Help( f1 );  
  
   MyStruct m_MyStruct3 = m_MyStruct1 * m_MyStruct2;   // C2296  
}  
```