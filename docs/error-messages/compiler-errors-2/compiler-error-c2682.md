---
title: "编译器错误 C2682 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2682"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2682"
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 编译器错误 C2682
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无法使用 casting\_operator 从“type1”强制转换到“type2”  
  
 某转换运算符尝试在不兼容的类型之间进行转换。  例如，无法使用 [dynamic\_cast](../../cpp/dynamic-cast-operator.md) 运算符将指针转换为引用。  `dynamic_cast` 运算符不能用于转换掉限定符。  类型上的所有限定符必须匹配。  
  
 可以使用 `const_cast` 运算符移除 `const`、`volatile`、`__unaligned` 等特性。  
  
 下面的示例生成 C2682：  
  
```  
// C2682.cpp  
class A { virtual void f(); };  
class B: public A {};  
  
void g(A* pa) {  
    B& rb = dynamic_cast<B&>(pa); // C2682  
}  
```  
  
 下面的示例生成 C2682：  
  
```  
// C2682b.cpp  
// compile with: /clr  
ref struct R{};  
ref struct RR : public R{};  
ref struct H {  
   RR^ r ;  
   short s;  
   int i;  
};  
  
int main() {  
   H^ h = gcnew H();    
   interior_ptr<int>lr = &(h->i);  
   interior_ptr<short>ssr = safe_cast<interior_ptr<short> >(lr);   // C2682  
   interior_ptr<short>ssr = reinterpret_cast<interior_ptr<short> >(lr);   // OK  
}  
```