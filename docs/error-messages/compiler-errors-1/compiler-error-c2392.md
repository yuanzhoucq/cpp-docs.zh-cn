---
title: "Compiler Error C2392 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2392"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2392"
ms.assetid: 98ced473-6383-46ed-b79c-21857d65dcb2
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# Compiler Error C2392
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“method1”：托管或 WinRT 类型中不支持协变返回类型，否则“method2”将被重写  
  
 对于 Windows 运行时成员函数或使用 [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)选项进行编译时，不允许协变返回类型。  
  
## 示例  
 下面的示例生成了 C2392，并演示了如何修复此错误。  
  
```  
// C2392.cpp  
// compile with: /clr  
public ref struct B {  
public:  
   int i;  
};  
  
public ref struct D: public B{};  
  
public ref struct B1 {  
public:  
   virtual B^ mf() {  
      B^ pB = gcnew B;  
      pB->i = 11;  
      return pB;  
   }  
};  
  
public ref struct D1: public B1 {  
public:  
   virtual D^ mf() override {  // C2392  
   // try the following line instead  
   // virtual B^ mf() override {  
   // return type D^ is covariant with B^, not allowed with CLR types  
      D^ pD = gcnew D;  
      pD->i = 12;  
      return pD;  
   }  
};  
  
int main() {  
   B1^ pB1 = gcnew D1;  
   B^ pB = pB1->mf();  
   D^ pD = dynamic_cast<D^>(pB);  
}  
```