---
title: "编译器警告（等级 2）C4356 | Microsoft Docs"
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
  - "C4356"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4356"
ms.assetid: 3af3defe-de33-43b6-bd6c-2c2e09e34f3f
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 2）C4356
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“成员”: 静态数据成员无法通过派生类初始化  
  
 静态数据成员的初始化的格式错误。  编译器已接受该初始化。  
  
 这是 Visual C\+\+ .NET 2003 编译器中的重大更改。  
  
 为使代码在 Visual C\+\+ 的所有版本中以相同方式工作，通过基类初始化成员。  
  
 使用 [警告](../../preprocessor/warning.md) 杂注可取消此警告。  
  
 下面的示例生成 C4356：  
  
```  
// C4356.cpp  
// compile with: /W2 /EHsc  
#include <iostream>  
  
template <class T>  
class C {  
   static int n;  
};  
  
class D : C<int> {};  
  
int D::n = 0; // C4356  
// try the following line instead  
// int C<int>::n = 0;  
  
class A {  
public:  
   static int n;  
};  
  
class B : public A {};  
  
int B::n = 10;   // C4356  
// try the following line instead  
// int A::n = 99;  
  
int main() {  
   using namespace std;  
   cout << B::n << endl;  
}  
```