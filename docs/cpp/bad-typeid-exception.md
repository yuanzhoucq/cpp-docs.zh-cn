---
title: "bad_typeid 异常 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "bad_typeid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_typeid 异常"
  - "异常, bad_typeid"
ms.assetid: 5963ed58-4ede-4597-957d-f7bbd06299c2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# bad_typeid 异常
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当 `typeid` 的操作数是 Null 指针时，[typeid 运算符](../cpp/typeid-operator.md)将引发 `bad_typeid` 异常。  
  
## 语法  
  
```  
  
      catch (bad_typeid)  
   statement  
```  
  
## 备注  
 `bad_typeid` 的接口为：  
  
```  
class bad_typeid : public exception  
{  
public:  
   bad_typeid(const char * _Message = "bad typeid");  
   bad_typeid(const bad_typeid &);  
   virtual ~bad_typeid();  
};  
```  
  
 以下示例演示引发 `bad_typeid` 异常的 `typeid` 运算符。  
  
```  
// expre_bad_typeid.cpp  
// compile with: /EHsc /GR  
#include <typeinfo.h>  
#include <iostream>  
  
class A{  
public:  
   // object for class needs vtable  
   // for RTTI  
   virtual ~A();  
};  
  
using namespace std;  
int main() {  
A* a = NULL;  
  
try {  
   cout << typeid(*a).name() << endl;  // Error condition  
   }  
catch (bad_typeid){  
   cout << "Object is NULL" << endl;  
   }  
}  
```  
  
## 输出  
  
```  
Object is NULL  
```  
  
## 请参阅  
 [运行时类型信息](../cpp/run-time-type-information.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)