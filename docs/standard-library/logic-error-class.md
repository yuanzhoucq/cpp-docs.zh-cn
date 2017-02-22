---
title: "logic_error 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "stdexcept/std::logic_error"
  - "std::logic_error"
  - "logic_error"
  - "std.logic_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "logic_error 类"
ms.assetid: b290d73d-94e1-4288-af86-2bb5d71f677a
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# logic_error 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此类用作引发报告执行程序前大概可检测的错误（例如，违反逻辑前提条件）的所有异常的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class logic_error : public exception {  
public:  
    explicit logic_error(const string& message);

    explicit logic_error(const char *message);

};  
```  
  
## <a name="remarks"></a>备注  
 返回的值 [什么](../standard-library/exception-class1.md) 是一份 **消息**`.`[数据](../standard-library/basic-string-class.md#basic_string__data)。  
  
## <a name="example"></a>示例  
  
```  
// logic_error.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
using namespace std;  
  
int main( )  
{  
   try   
   {  
      throw logic_error( "logic error" );  
   }  
   catch ( exception &e )   
   {  
      cerr << "Caught: " << e.what( ) << endl;  
      cerr << "Type: " << typeid( e ).name( ) << endl;  
   };  
}  
```  
  
 **输出**  
  
```  
Caught: logic error  
Type: class std::logic_error  
```  
  
## <a name="requirements"></a>要求  
 **标头︰** \< stdexcept>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>请参阅  
[exception 类](../standard-library/exception-class1.md)  
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

