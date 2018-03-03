---
title: "编译器错误 C2797 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2797
dev_langs:
- C++
helpviewer_keywords:
- C2797
ms.assetid: 9fb26d35-eb5c-46fc-9ff5-756fba5bdaff
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c8fd31905eb92db8ad2e3af941772584f6f64ce
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2797"></a>编译器错误 C2797
（已过时）未实现成员初始值设定项列表或非静态数据成员初始值设定项内部的列表初始化。  
  
 此警告是 Visual Studio 2015 中已过时。 在 Visual Studio 2013 和早期版本中，Visual c + + 编译器未实现成员初始值设定项列表或非静态数据成员初始值设定项内部的列表初始化。 在 Visual Studio 2013 Update 3 之前，这已在无提示的情况下转换为函数调用，从而将导致代码生成错误。 Visual Studio 2013 Update 3 将其报告为错误。  
  
 此示例生成 C2797：  
  
```  
#include <vector>  
struct S {  
    S() : v1{1} {} // C2797, VS2013 RTM incorrectly calls 'vector(size_type)'  
  
    std::vector<int> v1;  
    std::vector<int> v2{1, 2}; // C2797, VS2013 RTM incorrectly calls 'vector(size_type, const int &)'  
};  
  
```  
  
 此示例也生成 C2797：  
  
```  
struct S1 {  
    int i;  
};  
  
struct S2 {  
    S2() : s1{0} {} // C2797, VS2013 RTM interprets as S2() : s1(0) {} causing C2664  
    S1 s1;  
    S1 s2{0}; // C2797, VS2013 RTM interprets as S1 s2 = S1(0); causing C2664  
};  
  
```  
  
 若要解决此问题，你可以使用内部列表的显式构造。 例如：  
  
```  
#include <vector>  
typedef std::vector<int> Vector;  
struct S {  
    S() : v1(Vector{1}) {}  
  
    Vector v1;  
    Vector v2 = Vector{1, 2};  
};  
  
```  
  
 如果无需初始化列表：  
  
```  
struct S {  
    S() : s1("") {}  
  
    std::string s1;  
    std::string s2 = std::string("");  
};  
  
```  
  
 （Visual Studio 2013 中的编译器会在 Visual Studio 2013 Update 3 之前隐式执行它。）