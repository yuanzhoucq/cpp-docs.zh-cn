---
title: "runtime_error 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.runtime_error"
  - "runtime_error"
  - "stdexcept/std::runtime_error"
  - "std::runtime_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "runtime_error 类"
ms.assetid: 4d0227bf-847b-45a2-a320-2351ebf98368
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# runtime_error 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此类用作引发报告仅在执行程序时大概可检测的错误的所有异常的基类。  
  
## 语法  
  
```  
class runtime_error : public exception {  
public:  
    explicit runtime_error(const string& message);  
    explicit runtime_error(const char *message);  
};  
```  
  
## 备注  
 返回的值 [exception 类](../standard-library/exception-class1.md) 是一份 **消息**`.`[数据](../Topic/basic_string::data.md)。  
  
## 示例  
  
```  
// runtime_error.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
// runtime_error  
   try   
   {  
      locale loc( "test" );  
   }  
   catch ( exception &e )   
   {  
      cerr << "Caught " << e.what( ) << endl;  
      cerr << "Type " << typeid( e ).name( ) << endl;  
   };  
}  
```  
  
 **捕获错误的区域设置名称类型类 std::runtime\_error**   
## 要求  
 **标头︰** \< stdexcept \>  
  
 **命名空间:** std  
  
## 请参阅  
 [exception 类](../standard-library/exception-class1.md)   
 [C\+\+ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)