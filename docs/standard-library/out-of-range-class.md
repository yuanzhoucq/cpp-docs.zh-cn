---
title: "out_of_range 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- out_of_range
- stdexcept/std::out_of_range
dev_langs:
- C++
helpviewer_keywords:
- out_of_range class
ms.assetid: d0e14dc0-065e-4666-9ac9-51e52223c503
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 416f866ead1e3e4468136ebbdef1b5d7750691d4
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="outofrange-class"></a>out_of_range 类
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
 [what](../standard-library/exception-class.md) 返回的值是 **message**`.`[data](../standard-library/basic-string-class.md#data) 的副本。  
  
## <a name="example"></a>示例  
  
```cpp  
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
 **标头：**\<stdexcept>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [logic_error 类](../standard-library/logic-error-class.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


