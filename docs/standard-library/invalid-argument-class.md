---
title: "invalid_argument 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.invalid_argument"
  - "stdexcept/std::invalid_argument"
  - "invalid_argument"
  - "std::invalid_argument"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_argument 类"
ms.assetid: af6c227d-ad7c-4e63-9dee-67af81d83506
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# invalid_argument 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此类用作引发报告无效自变量的所有异常的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class invalid_argument : public logic_error {  
public:  
    explicit invalid_argument(const string& message);

    explicit invalid_argument(const char *message);

};  
```  
  
## <a name="remarks"></a>备注  
 返回的值 [什么](../standard-library/exception-class1.md) 是一份 **消息**`.`[数据](../standard-library/basic-string-class.md#basic_string__data)。  
  
## <a name="example"></a>示例  
  
```  
// invalid_arg.cpp  
// compile with: /EHsc /GR  
#include <bitset>  
#include <iostream>  
  
using namespace std;  
  
int main( )  
{  
   try   
   {  
      bitset< 32 > bitset( string( "11001010101100001b100101010110000") );  
   }  
   catch ( exception &e )   
   {  
      cerr << "Caught " << e.what( ) << endl;  
      cerr << "Type " << typeid( e ).name( ) << endl;  
   };  
}  
\* Output:   
Caught invalid bitset<N> char  
Type class std::invalid_argument  
*\  
```  
  
## <a name="requirements"></a>要求  
 **标头︰** \< stdexcept>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>请参阅  
 [logic_error 类](../standard-library/logic-error-class.md)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

