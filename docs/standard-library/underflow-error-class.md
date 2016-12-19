---
title: "underflow_error 类 | Microsoft Docs"
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
  - "stdexcept/std::underflow_error"
  - "underflow_error"
  - "std.underflow_error"
  - "std::underflow_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "underflow_error 类"
ms.assetid: d632f1f9-9c6c-4954-b96b-03041bfab22d
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# underflow_error 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此类用作引发报告算数下溢的所有异常的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class underflow_error : public runtime_error {  
public:  
    explicit underflow_error(const string& message);

    explicit underflow_error(const char *message);

};  
```  
  
## <a name="remarks"></a>备注  
 返回的值 [什么](../standard-library/exception-class1.md) 是一份 **消息**`.`[数据](../standard-library/basic-string-class.md#basic_string__data)。  
  
## <a name="example"></a>示例  
  
```  
// underflow_error.cpp  
// compile with: /EHsc /GR  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   try   
   {  
      throw underflow_error( "The number's a bit small, captain!" );  
   }  
   catch ( exception &e ) {  
      cerr << "Caught: " << e.what( ) << endl;  
      cerr << "Type: " << typeid( e ).name( ) << endl;  
   };  
}  
\* Output:   
Caught: The number's a bit small, captain!  
Type: class std::underflow_error  
*\  
```  
  
## <a name="requirements"></a>要求  
 **标头︰** \< stdexcept>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>请参阅  
 [\< stdexcept> 成员](http://msdn.microsoft.com/zh-cn/7b6b0a73-916e-44aa-9a3f-f5b6b3ce98e6)   
 [runtime_error 类](../standard-library/runtime-error-class.md)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

