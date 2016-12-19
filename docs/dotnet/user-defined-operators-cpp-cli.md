---
title: "用户定义的运算符 (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "在 /clr 下用户定义的运算符"
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
caps.latest.revision: 16
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 用户定义的运算符 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

托管类型的用户定义运算符允许用作静态成员或实例成员，或者位于全局范围内。  但是，只有静态运算符通过使用除 Visual C\+\+ 外语言编写的到客户端的元数据实现访问。  
  
 在引用类型，一个静态的用户定义的运算符的参数必须为这些类型中的一个：  
  
-   一个句柄 \(`type` ^\) 到封闭类型的实例。  
  
-   间接引用类型 \(`type`^& 或 type^% \) 到封闭类型的实例句柄。  
  
 在值类型，一个静态的用户定义的运算符的参数必须为这些类型中的一个：  
  
-   与封闭值类型的类型相同。  
  
-   指针类型间接 \(`type` ^\) 指向封闭类型。  
  
-   引用类型间接 \(`type` % 或 `type`& ）到封闭类型。  
  
-   引用类型间接 \(`type`^% 或 `type`^&\) 到句柄。  
  
 可以定义以下运算符：  
  
|运算符|一元\/二进制格式?|  
|---------|----------------|  
|\!|一元|  
|\!\=|二进制|  
|%|二进制|  
|&|一元和二进制|  
|&&|二进制|  
|\*|一元和二进制|  
|\+|一元和二进制|  
|\+\+|一元|  
|,|二进制|  
|\-|一元和二进制|  
|\-\-|一元|  
|\-\>|一元|  
|\/|二进制|  
|\<|二进制|  
|\<\<|二进制|  
|\<\=|二进制|  
|\=|二进制|  
|\=\=|二进制|  
|\>|二进制|  
|\>\=|二进制|  
|\>\>|二进制|  
|^|二进制|  
|false|一元|  
|true|一元|  
|&#124;|二进制|  
|&#124;&#124;|二进制|  
|~|一元|  
  
## 示例  
  
```  
// mcppv2_user-defined_operators.cpp  
// compile with: /clr  
using namespace System;  
public ref struct X {  
   X(int i) : m_i(i) {}  
   X() {}  
  
   int m_i;  
  
   // static, binary, user-defined operator  
   static X ^ operator + (X^ me, int i) {  
      return (gcnew X(me -> m_i + i));  
   }  
  
   // instance, binary, user-defined operator  
   X^ operator -( int i ) {  
      return gcnew X(this->m_i - i);  
   }  
  
   // instance, unary, user-defined pre-increment operator  
   X^ operator ++() {  
      return gcnew X(this->m_i++);  
   }  
  
   // instance, unary, user-defined post-increment operator  
   X^ operator ++(int i) {  
      return gcnew X(this->m_i++);  
   }  
  
   // static, unary user-defined pre- and post-increment operator  
   static X^ operator-- (X^ me) {  
      return (gcnew X(me -> m_i - 1));  
   }  
};  
  
int main() {  
   X ^hX = gcnew X(-5);  
   System::Console::WriteLine(hX -> m_i);  
  
   hX = hX + 1;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX = hX - (-1);  
   System::Console::WriteLine(hX -> m_i);  
  
   ++hX;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX++;  
   System::Console::WriteLine(hX -> m_i);  
  
   hX--;  
   System::Console::WriteLine(hX -> m_i);  
  
   --hX;  
   System::Console::WriteLine(hX -> m_i);  
}  
```  
  
  **\-5**  
**\-4**  
**\-3**  
**\-2**  
**\-1**  
**\-2**  
**\-3**   
## 示例  
 下面的示例演示复合运算符，只有使用 **\/clr** 编译时才可用。  复合运算符创建二元运算符的赋值形式，如果一个赋值运算符的左边具有 CLR 类型的操作数没有定义。  
  
```  
// mcppv2_user-defined_operators_2.cpp  
// compile with: /clr  
ref struct A {  
   A(int n) : m_n(n) {};  
   static A^ operator + (A^ r1, A^ r2) {  
      return gcnew A( r1->m_n + r2->m_n);  
   };  
   int m_n;  
};  
  
int main() {  
   A^ a1 = gcnew A(10);  
   A^ a2 = gcnew A(20);  
  
   a1 += a2;   // a1 = a1 + a2   += not defined in source  
   System::Console::WriteLine(a1->m_n);  
}  
```  
  
  **30**   
## 请参阅  
 [类和结构 \(托管\)](../windows/classes-and-structs-cpp-component-extensions.md)