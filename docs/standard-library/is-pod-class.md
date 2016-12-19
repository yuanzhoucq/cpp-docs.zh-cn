---
title: "is_pod 类 | Microsoft Docs"
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
  - "std.tr1.is_pod"
  - "is_pod"
  - "std::tr1::is_pod"
  - "std.is_pod"
  - "std::is_pod"
  - "type_traits/std::is_pod"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "is_pod 类 [TR1]"
  - "is_pod"
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
caps.latest.revision: 20
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# is_pod 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

测试类型是否为 POD。  
  
## 语法  
  
```  
template<class Ty>  
    struct is_pod;  
```  
  
#### 参数  
 `Ty`  
 要查询的类型。  
  
## 备注  
 如果类型 `Ty` 为纯旧数据 \(POD\)，则 `is_pod<Ty>::value` 为 `true`。  否则为 `false`。  
  
 算术类型、枚举类型、指针类型和指向成员类型的指针是 POD。  
  
 POD 类型的 cv 限定版本本身就是 POD 类型。  
  
 POD 数组本身就是 POD。  
  
 所有非静态数据成员都是 POD 的结构或联本身就是 POD，前提是它：  
  
-   没有用户声明的构造函数。  
  
-   没有私有或受保护的非静态数据成员。  
  
-   没有基类。  
  
-   没有虚函数。  
  
-   没有引用类型的非静态数据成员。  
  
-   没有用户定义的复制赋值运算符。  
  
-   没有用户定义的析构函数。  
  
 因此，你可以以递归方式生成 POD 结构和包含 POD 结构和数组的数组。  
  
## 示例  
  
```  
// std_tr1__type_traits__is_pod.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial   
    {   
    int val;   
    };   
  
struct throws   
    {   
    throws() throw(int)   
        {   
        }   
  
    throws(const throws&) throw(int)   
        {   
        }   
  
    throws& operator=(const throws&) throw(int)   
        {   
        }   
  
    int val;   
    };   
  
int main()   
    {   
    std::cout << "is_pod<trivial> == " << std::boolalpha   
        << std::is_pod<trivial>::value << std::endl;   
    std::cout << "is_pod<int> == " << std::boolalpha   
        << std::is_pod<int>::value << std::endl;   
    std::cout << "is_pod<throws> == " << std::boolalpha   
        << std::is_pod<throws>::value << std::endl;   
  
    return (0);   
    }  
  
```  
  
  **is\_pod\<trivial\> \=\= true**  
**is\_pod\<int\> \=\= true**  
**is\_pod\<throws\> \=\= false**   
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)