---
title: "编译器错误 C3185 | Microsoft Docs"
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
  - "C3185"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3185"
ms.assetid: 5bf96279-043c-4981-9d02-b4550071b192
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3185
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在托管或 WinRT 类型“type”上使用了“typeid”，请改用“operator”  
  
 无法将 [typeid](../../cpp/typeid-operator.md) 运算符应用于托管或 WinRT 类型；请改用 [typeid](../../windows/typeid-cpp-component-extensions.md)。  
  
 下面的示例生成 C3185，并演示如何修复此错误：  
  
```  
// C3185a.cpp  
// compile with: /clr  
ref class Base {};  
ref class Derived : public Base {};  
  
int main() {  
   Derived ^ pd = gcnew Derived;  
   Base ^pb = pd;  
   const type_info & t1 = typeid(pb);   // C3185  
   System::Type ^ MyType = Base::typeid;   // OK  
};  
```  
  
 **C\+\+ 托管扩展**  
  
 无法将 [typeid](../../cpp/typeid-operator.md) 应用于托管类型；请改用 [\_\_typeof](../../misc/typeof.md)。  
  
 下面的示例生成 C3185：  
  
```  
// C3185b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
__gc class Base {};  
__gc class Derived : public Base {};  
  
int main() {  
   Derived *pd = new Derived;  
   Base *pb = pd;  
   const type_info & t1 = typeid(*pb);   // C3185  
  
   // OK  
   Type * t = __typeof(Base);  
   Type * t1 = __typeof(Derived);  
};  
```