---
title: "bad_alloc 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- new/std::bad_alloc
- bad_alloc
dev_langs:
- C++
helpviewer_keywords:
- bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
caps.latest.revision: 26
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
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 3d42ce374744f446185466f65df77a38ebcdbfd4
ms.lasthandoff: 02/24/2017

---
# <a name="badalloc-class"></a>bad_alloc 类
该类描述引发的异常以指示分配请求未成功。  
  
## <a name="syntax"></a>语法  
  
```  
class bad_alloc : public exception {  
    bad_alloc();
virtual ~bad_alloc();

};  
```  
  
## <a name="remarks"></a>备注  
 **what** 返回的值是实现定义的 C 字符串。 无成员函数引发任何异常。  
  
## <a name="requirements"></a>要求  
 **标头：**\<new>  
  
 **命名空间：** std  
  
## <a name="example"></a>示例  
  
```cpp  
// bad_alloc.cpp  
// compile with: /EHsc  
#include<new>  
#include<iostream>  
using namespace std;  
  
int main() {  
   char* ptr;  
   try {  
      ptr = new char[(~unsigned int((int)0)/2) - 1];  
      delete[] ptr;  
   }  
   catch( bad_alloc &ba) {  
      cout << ba.what( ) << endl;  
   }  
}  
```  
  
## <a name="sample-output"></a>示例输出  
  
```  
bad allocation  
```  
  
## <a name="requirements"></a>要求  
 **标头：**\<new>  
  
## <a name="see-also"></a>另请参阅
 [exception 类](../standard-library/exception-class.md)  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


