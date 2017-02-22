---
title: "bad_cast 异常 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "bad_cast"
  - "bad_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_cast 关键字 [C++]"
  - "异常, bad_cast"
ms.assetid: 31eae1e7-d8d5-40a0-9fef-64a6a4fc9021
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# bad_cast 异常
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由于强制转换为引用类型失败，`dynamic_cast` 运算符引发 `bad_cast` 异常。  
  
## 语法  
  
```  
catch (bad_cast)  
   statement  
```  
  
## 备注  
 `bad_cast` 的接口为：  
  
```  
class bad_cast : public exception {  
public:  
   bad_cast(const char * _Message = "bad cast");  
   bad_cast(const bad_cast &);  
   virtual ~bad_cast();  
};  
```  
  
 以下代码包含失败的 `dynamic_cast` 引发 `bad_cast` 异常的示例。  
  
```  
// expre_bad_cast_Exception.cpp  
// compile with: /EHsc /GR  
#include <typeinfo.h>  
#include <iostream>  
  
class Shape {  
public:  
   virtual void virtualfunc() const {}  
};  
  
class Circle: public Shape {  
public:  
   virtual void virtualfunc() const {}  
};  
  
using namespace std;  
int main() {  
   Shape shape_instance;  
   Shape& ref_shape = shape_instance;  
   try {  
      Circle& ref_circle = dynamic_cast<Circle&>(ref_shape);   
   }  
   catch (bad_cast b) {  
      cout << "Caught: " << b.what();  
   }  
}  
```  
  
 由于强制转换的对象 \(Shape\) 不是派生自指定的强制转换类型 \(Circle\)，因此引发异常。  若要避免此异常，请将下列声明添加到 `main`：  
  
```  
Circle circle_instance;  
Circle& ref_circle = circle_instance;  
```  
  
 然后在 `try` 块中反转强制转换的意义，如下所示：  
  
```  
Shape& ref_shape = dynamic_cast<Shape&>(ref_circle);  
```  
  
## 请参阅  
 [dynamic\_cast 运算符](../cpp/dynamic-cast-operator.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)   
 [C\+\+ 异常处理](../cpp/cpp-exception-handling.md)