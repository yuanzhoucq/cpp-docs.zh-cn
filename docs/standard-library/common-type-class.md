---
title: "common_type 类 | Microsoft Docs"
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
  - "std.tr1.common_type"
  - "common_type"
  - "std::tr1::common_type"
  - "std.common_type"
  - "std::common_type"
  - "type_traits/std::common_type"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "common_type 类 [TR1]"
  - "common_type"
ms.assetid: 02bc4e7b-c63d-49de-9f8a-511d3a5c1e7f
caps.latest.revision: 22
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# common_type 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

确定一个或多个类型的通用类型。  
  
## 语法  
  
```  
  
template <class... T>  
   struct common_type;  
  
template <class T>  
   struct common_type<T> {  
      typedef typename decay<T>::type type;  
};  
  
template <class T, class U>  
   struct common_type<T, U> {  
      typedef typename decay<decltype(true ?  declval<T>() :  
         declval<U>())>::type type;  
};  
  
template <class T, class U, class... V>  
   struct common_type<T, U, V...> {  
      typedef typename common_type<typename common_type<T, U>::type, V...>::type type;  
};  
```  
  
#### 参数  
 状态为[已完成类型](../c-language/incomplete-types.md)或无效的类型列表。  
  
## 备注  
 `type` 成员是参数列表中所有类型都可以转换为的通用类型。  
  
## 示例  
 下面的程序演示一些正确使用方案并测试结果。  
  
```cpp  
// Compile using cl.exe /EHsc  
// common_type sample  
#include <iostream>  
#include <type_traits>  
  
struct Base {};  
struct Derived : Base {};  
  
int main()   
{  
    typedef std::common_type<unsigned char, short, int>::type NumericType;  
    typedef std::common_type<float, double>::type FloatType;  
    typedef std::common_type<const int, volatile int>::type ModifiedIntType;  
    typedef std::common_type<Base, Derived>::type ClassType;  
  
    std::cout << std::boolalpha;  
    std::cout << "Test for typedefs of common_type int" << std::endl;  
    std::cout << "NumericType: "     << std::is_same<int, NumericType>::value << std::endl;  
    std::cout << "FloatType: "       << std::is_same<int, FloatType>::value << std::endl;  
    std::cout << "ModifiedIntType: " << std::is_same<int, ModifiedIntType>::value << std::endl;  
    std::cout << "ClassType: "       << std::is_same<int, ClassType>::value << std::endl;  
    std::cout << "---------------------------" << std::endl;  
    std::cout << "Test for typedefs of common_type double" << std::endl;  
    std::cout << "NumericType: "     << std::is_same<double, NumericType>::value << std::endl;  
    std::cout << "FloatType: "       << std::is_same<double, FloatType>::value << std::endl;  
    std::cout << "ModifiedIntType: " << std::is_same<double, ModifiedIntType>::value << std::endl;  
    std::cout << "ClassType: "       << std::is_same<double, ClassType>::value << std::endl;  
    std::cout << "---------------------------" << std::endl;  
    std::cout << "Test for typedefs of common_type Base" << std::endl;  
    std::cout << "NumericType: "     << std::is_same<Base, NumericType>::value << std::endl;  
    std::cout << "FloatType: "       << std::is_same<Base, FloatType>::value << std::endl;  
    std::cout << "ModifiedIntType: " << std::is_same<Base, ModifiedIntType>::value << std::endl;  
    std::cout << "ClassType: "       << std::is_same<Base, ClassType>::value << std::endl;  
  
    return 0;  
}  
```  
  
## 输出  
  
```  
Test for typedefs of common_type int  
NumericType: true  
FloatType: false  
ModifiedIntType: true  
ClassType: false  
---------------------------  
Test for typedefs of common_type double  
NumericType: false  
FloatType: true  
ModifiedIntType: false  
ClassType: false  
---------------------------  
Test for typedefs of common_type Base  
NumericType: false  
FloatType: false  
ModifiedIntType: false  
ClassType: true  
  
```  
  
## 要求  
 **标头：**\<type\_traits\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)