---
title: "bad_alloc 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: new/std::bad_alloc
dev_langs: C++
helpviewer_keywords: bad_alloc class
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fc136f33d3653aef1e325a97f6e47ff3742b0182
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="requirements"></a>惠?  
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
  
## <a name="requirements"></a>惠?  
 **标头：**\<new>  
  
## <a name="see-also"></a>请参阅
 [exception 类](../standard-library/exception-class.md)  
 [C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

