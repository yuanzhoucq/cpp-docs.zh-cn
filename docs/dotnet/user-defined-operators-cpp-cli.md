---
title: "用户定义的运算符 (C + + /cli CLI) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- user-defined operators under /clr
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b02d6806abedb407d1c53ec8022e92983ce21d28
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="user-defined-operators-ccli"></a>用户定义的运算符 (C++/CLI)
托管类型的用户定义运算符可用作静态成员或实例成员，或者在全局范围内使用。 但是，使用除 Visual C++ 之外的语言编写的客户端通过元数据仅可以访问静态运算符。  
  
 在引用类型中，静态的用户定义的运算符的参数之一必须是以下类型中的一个：  
  
-   封闭类型的实例的一个句柄 (`type` ^)。  
  
-   封闭类型实例的句柄的间接引用类型（`type`^& 或 type^%）。  
  
 在值类型中，静态的用户定义的运算符的参数之一必须是以下类型中的一个：  
  
-   与封闭值类型相同的类型。  
  
-   封闭类型的间接指针类型 (`type` ^)。  
  
-   封闭类型的间接引用类型（`type`% 或 `type`&）。  
  
-   句柄的间接引用类型（`type`^% 或 `type`^&）。  
  
 您可以定义以下运算符：  
  
|运算符|一元还是二元形式？|  
|--------------|--------------------------|  
|!|一元|  
|!=|二进制|  
|%|二进制|  
|&|一元和二进制|  
|&&|二进制|  
|*|一元和二进制|  
|+|一元和二进制|  
|++|一元|  
|,|二进制|  
|-|一元和二进制|  
|--|一元|  
|->|一元|  
|/|二进制|  
|<|二进制|  
|<<|二进制|  
|\<=|二进制|  
|=|二进制|  
|==|二进制|  
|>|二进制|  
|>=|二进制|  
|>>|二进制|  
|^|二进制|  
|False|一元|  
|true|一元|  
|&#124;|二进制|  
|&#124;&#124;|二进制|  
|~|一元|  
  
## <a name="example"></a>示例  
  
```cpp  
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
  
```Output  
-5  
-4  
-3  
-2  
-1  
-2  
-3  
```  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用时才可用的复合运算符**/clr**进行编译。 如果未定义二元运算符的赋值形式，则复合运算符会创建一个，其中赋值运算符的左侧具有一个 CLR 类型。  
  
```cpp  
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
  
```Output  
30  
```  
  
## <a name="see-also"></a>请参阅  
 [类和结构](../windows/classes-and-structs-cpp-component-extensions.md)