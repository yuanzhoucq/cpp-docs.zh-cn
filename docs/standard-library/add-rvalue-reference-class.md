---
title: "add_rvalue_reference 类 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "type_traits/std::add_rvalue_reference"
  - "std::add_rvalue_reference"
  - "add_rvalue_reference"
  - "std.add_rvalue_reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "add_rvalue_reference 类"
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# add_rvalue_reference 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果它是对象或函数的类型，创建的模板参数，将右值引用类型。 否则，由于引用折叠的语义，类型为模板参数相同。  
  
## 语法  
  
```cpp  
template<class T>  
    struct add_rvalue_reference;  
  
template<class T>  
    using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;  
```  
  
#### 参数  
 T  
 要修改的类型。  
  
## 备注  
 `add_rvalue_reference` 类具有一个名为成员 `type`, ，这是与模板参数的右值引用的类型的别名 `T`。 对于非对象和非函数类型的引用折叠的语义表示， `T`, ，`T&&` 是 `T`。 例如，当 `T` 是左值引用类型，  `add_rvalue_reference<T>::type` 为左值引用类型，不为右值引用。  
  
 为方便起见，\< type\_traits \> 定义了一个帮助器模板， `add_rvalue_reference_t`, ，则该别名 `type` 的成员 `add_rvalue_reference`。  
  
## 示例  
 此代码示例使用 static\_assert 来显示如何通过使用创建的右值引用类型 `add_rvalue_reference` 和 `add_rvalue_reference_t`, ，以及如何对 `add_rvalue_reference` 上左值引用类型不是右值引用，但将折叠为左值引用类型。  
  
```cpp  
// ex_add_rvalue_reference.cpp  
// Build by using: cl /EHsc /W4 ex_add_rvalue_reference.cpp  
#include <type_traits>   
#include <iostream>   
#include <string>  
  
using namespace std;  
int main()  
{  
    static_assert(is_same<add_rvalue_reference<string>::type, string&&>::value,   
        "Expected add_rvalue_reference_t<string> to be string&&");  
    static_assert(is_same<add_rvalue_reference_t<string*>, string*&&>::value,   
        "Expected add_rvalue_reference_t<string*> to be string*&&");  
    static_assert(is_same<add_rvalue_reference<string&>::type, string&>::value,   
        "Expected add_rvalue_reference_t<string&> to be string&");  
    static_assert(is_same<add_rvalue_reference_t<string&&>, string&&>::value,   
        "Expected add_rvalue_reference_t<string&&> to be string&&");  
    cout << "All static_assert tests of add_rvalue_reference passed." << endl;  
    return 0;  
}  
  
/*Output:  
All static_assert tests of add_rvalue_reference passed.  
*/  
```  
  
## 要求  
 标头：\< type\_traits \> 命名空间：std  
  
## 请参阅  
 [\<type\_traits\>](../standard-library/type-traits.md)   
 [add\_lvalue\_reference 类](../standard-library/add-lvalue-reference-class.md)   
 [is\_rvalue\_reference 类](../standard-library/is-rvalue-reference-class.md)