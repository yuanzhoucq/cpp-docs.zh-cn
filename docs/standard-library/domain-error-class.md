---
title: "domain_error 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "domain_error"
  - "std::domain_error"
  - "std.domain_error"
  - "stdexcept/std::domain_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "domain_error 类"
ms.assetid: a1d8245d-61c2-4d1e-973f-073bd5dd5fa3
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# domain_error 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此类用作引发报告域错误的所有异常的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class domain_error : public logic_error {  
public:  
    explicit domain_error(const string& message);

    explicit domain_error(const char *message);

};  
```  
  
## <a name="remarks"></a>备注  
 返回的值 [什么](../standard-library/exception-class1.md) 是一份 **消息**`.`[数据](../standard-library/basic-string-class.md#basic_string__data)。  
  
## <a name="example"></a>示例  
  
```  
// domain_error.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   try   
   {  
      throw domain_error( "Your domain is in error!" );  
   }  
   catch (exception &e)   
   {  
      cerr << "Caught: " << e.what( ) << endl;  
      cerr << "Type: " << typeid(e).name( ) << endl;  
   };  
}  
\* Output:   
Caught: Your domain is in error!  
Type: class std::domain_error  
*\  
```  
  
## <a name="requirements"></a>要求  
 **标头︰** \< stdexcept>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>请参阅  
 [logic_error 类](../standard-library/logic-error-class.md)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

