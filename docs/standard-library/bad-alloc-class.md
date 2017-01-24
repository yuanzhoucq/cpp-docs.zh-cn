---
title: "bad_alloc 类 | Microsoft Docs"
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
  - "std::bad_alloc"
  - "new/std:bad_alloc"
  - "bad_alloc"
  - "std.bad_alloc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_alloc 类"
ms.assetid: 6429a8e6-5a49-4907-8d56-f4a4ec8131d0
caps.latest.revision: 26
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# bad_alloc 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

该类描述引发的异常以指示分配请求未成功。  
  
## <a name="syntax"></a>语法  
  
```  
class bad_alloc : public exception {  
    bad_alloc();
virtual ~bad_alloc();

};  
```  
  
## <a name="remarks"></a>备注  
 返回的值 **什么** 是实现定义的 C 字符串。 无成员函数引发任何异常。  
  
## <a name="requirements"></a>要求  
 **标头︰** \< 新>  
  
 **Namespace:** std  
  
## <a name="example"></a>示例  
  
```  
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
 **标头︰** \< 新>  
  
## <a name="see-also"></a>请参阅
 [exception 类](../standard-library/exception-class1.md)  
 [C + + 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

