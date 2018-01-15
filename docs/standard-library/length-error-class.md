---
title: "length_error 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: stdexcept/std::length_error
dev_langs: C++
helpviewer_keywords: length_error class
ms.assetid: d53c46c5-4626-400d-bd76-bf3e1e0f64ae
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d33195d1c2215c28122d7a9a536942afc1dc512f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="lengtherror-class"></a>length_error 类
此类用作引发报告尝试生成对象太长而难以指定的所有异常的基类。  
  
## <a name="syntax"></a>语法  
  
```  
class length_error : public logic_error {  
public:  
    explicit length_error(const string& message);

    explicit length_error(const char *message);

};  
```  
  
## <a name="remarks"></a>备注  
 [what](../standard-library/exception-class.md) 返回的值是 **message**`.`[data](../standard-library/basic-string-class.md#data) 的副本。  
  
## <a name="example"></a>示例  
  
```cpp  
// length_error.cpp  
// compile with: /EHsc /GR /MDd  
#include <vector>  
#include <iostream>  
  
using namespace std;  
  
template<class  T>  
class stingyallocator : public allocator< T>  
{  
public:  
   template <class U>  
      struct rebind { typedef stingyallocator<U> other; };  
   _SIZT max_size( ) const  
   {  
         return 10;  
   };  
  
};  
  
int main( )  
{  
   try  
   {  
      vector<int, stingyallocator< int > > myv;  
      for ( int i = 0; i < 11; i++ ) myv.push_back( i );  
   }  
   catch ( exception &e )  
   {  
      cerr << "Caught " << e.what( ) << endl;  
      cerr << "Type " << typeid( e ).name( ) << endl;  
   };  
}  
\* Output:   
Caught vector<T> too long  
Type class std::length_error  
*\  
```  
  
## <a name="requirements"></a>惠?  
 **标头：**\<stdexcept>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [logic_error 类](../standard-library/logic-error-class.md)   
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

