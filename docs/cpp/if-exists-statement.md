---
title: "__if_exists 语句 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__if_exists_cpp"
  - "__if_exists"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__if_exists 关键字 [C++]"
  - "标识符, 测试是否存在"
  - "symbols, 测试是否存在"
ms.assetid: d3eb34b6-f3a9-4063-a286-b62a28c0c7fa
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# __if_exists 语句
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`__if_exists` 语句测试指定的标识符是否存在。  如果该标识符存在，则执行指定的语句块。  
  
## 语法  
  
```  
__if_exists ( identifier ) {   
statements  
};  
```  
  
#### 参数  
  
|参数|说明|  
|--------|--------|  
|`identifier`|要测试其存在性的标识符。|  
|`statements`|`identifier` 存在时要执行的一个或多个语句。|  
  
## 备注  
  
> [!CAUTION]
>  若要实现最可靠的结果，请在以下约束条件下使用 `__if_exists` 语句。  
  
-   只将 `__if_exists` 语句应用于简单类型，而不是模板。  
  
-   将 `__if_exists` 语句应用于类的内部或外部的标识符。  请勿将 `__if_exists` 语句应用于局部变量。  
  
-   请仅在函数的主体中使用该 `__if_exists` 语句。  在函数主体外部，`__if_exists` 语句仅能测试完全定义的类型。  
  
-   在测试重载函数时，不能测试特定形式的重载。  
  
 `__if_exists` 语句的补集是 [\_\_if\_not\_exists](../cpp/if-not-exists-statement.md) 语句。  
  
## 示例  
 请注意，此示例使用了模板，不建议这样做。  
  
```  
// the__if_exists_statement.cpp  
// compile with: /EHsc  
#include <iostream>  
  
template<typename T>  
class X : public T {  
public:  
   void Dump() {  
      std::cout << "In X<T>::Dump()" << std::endl;  
  
      __if_exists(T::Dump) {  
         T::Dump();  
      }  
  
      __if_not_exists(T::Dump) {  
         std::cout << "T::Dump does not exist" << std::endl;  
      }  
   }     
};  
  
class A {  
public:  
   void Dump() {  
      std::cout << "In A::Dump()" << std::endl;  
   }  
};  
  
class B {};  
  
bool g_bFlag = true;  
  
class C {  
public:  
   void f(int);  
   void f(double);  
};  
  
int main() {   
   X<A> x1;  
   X<B> x2;  
  
   x1.Dump();  
   x2.Dump();  
  
   __if_exists(::g_bFlag) {  
      std::cout << "g_bFlag = " << g_bFlag << std::endl;  
   }  
  
   __if_exists(C::f) {  
      std::cout << "C::f exists" << std::endl;  
   }  
  
   return 0;  
}  
```  
  
## Output  
  
```  
In X<T>::Dump()  
In A::Dump()  
In X<T>::Dump()  
T::Dump does not exist  
g_bFlag = 1  
C::f exists  
```  
  
## 请参阅  
 [选择语句](../cpp/selection-statements-cpp.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [\_\_if\_not\_exists 语句](../cpp/if-not-exists-statement.md)