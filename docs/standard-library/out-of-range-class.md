---
title: "out_of_range 类 | Microsoft Docs"
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
  - "out_of_range"
  - "stdexcept/std::out_of_range"
  - "std.out_of_range"
  - "std::out_of_range"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "out_of_range 类"
ms.assetid: d0e14dc0-065e-4666-9ac9-51e52223c503
caps.latest.revision: 25
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# out_of_range 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此类用作引发报告无效自变量的所有异常的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class out_of_range : public logic_error {  
public:  
    explicit out_of_range(const string& message);

    explicit out_of_range(const char *message);

};  
```  
  
## <a name="remarks"></a>备注  
 返回的值 [什么](../standard-library/exception-class1.md) 是一份 **消息**`.`[数据](../standard-library/basic-string-class.md#basic_string__data)。  
  
## <a name="example"></a>示例  
  
```  
// out_of_range.cpp  
// compile with: /EHsc  
#include <string>  
#include <iostream>  
  
using namespace std;  
  
int main() {  
// out_of_range  
   try {  
      string str( "Micro" );  
      string rstr( "soft" );  
      str.append( rstr, 5, 3 );  
      cout << str << endl;  
   }  
   catch ( exception &e ) {  
      cerr << "Caught: " << e.what( ) << endl;  
   };  
}  
```  
  
## <a name="output"></a>输出  
  
```  
Caught: invalid string position  
```  
  
## <a name="requirements"></a>要求  
 **标头︰** \< stdexcept>  
  
 **Namespace:** std  
  
## <a name="see-also"></a>请参阅  
 [logic_error 类](../standard-library/logic-error-class.md)   
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

