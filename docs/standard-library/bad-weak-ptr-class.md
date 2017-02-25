---
title: "bad_weak_ptr 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "memory/std::tr1::bad_weak_ptr"
  - "std::tr1::bad_weak_ptr"
  - "bad_weak_ptr"
  - "tr1::bad_weak_ptr"
  - "tr1.bad_weak_ptr"
  - "std.tr1.bad_weak_ptr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bad_weak_ptr 类"
  - "bad_weak_ptr 类 [TR1]"
ms.assetid: a09336d5-7237-4480-ab6b-3787e0e6025e
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# bad_weak_ptr 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

报告不良的 weak\_ptr 异常。  
  
## 语法  
  
```  
class bad_weak_ptr  
    : public std::exception {  
public:  
    bad_weak_ptr();  
    const char *what() throw();  
    };  
```  
  
## 备注  
 此类描述可从 [shared\_ptr 类](../standard-library/shared-ptr-class.md) 构造函数引发的异常，该构造函数采用 [weak\_ptr 类](../standard-library/weak-ptr-class.md) 类型的参数。  成员函数 `what` 返回 `"bad_weak_ptr"`。  
  
## 示例  
  
```  
// std_tr1__memory__bad_weak_ptr.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()   
    {   
    std::weak_ptr<int> wp;   
  
     {   
    std::shared_ptr<int> sp(new int);   
    wp = sp;   
     }   
  
    try   
        {   
        std::shared_ptr<int> sp1(wp); // weak_ptr has expired   
        }   
    catch (const std::bad_weak_ptr&)   
        {   
        std::cout << "bad weak pointer" << std::endl;   
        }   
    catch (...)   
        {   
        std::cout << "unknown exception" << std::endl;   
        }   
  
    return (0);   
    }  
  
```  
  
  **错误的弱指针**   
## 要求  
 **标头：**\<memory\>  
  
 **命名空间:** std  
  
## 请参阅  
 [weak\_ptr 类](../standard-library/weak-ptr-class.md)