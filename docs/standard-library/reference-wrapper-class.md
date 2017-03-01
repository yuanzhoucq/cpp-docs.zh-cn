---
title: "reference_wrapper 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- reference_wrapper
- std::reference_wrapper
- functional/std::reference_wrapper
- type_traits/std::reference_wrapper
- xrefwrap/std::reference_wrapper
- type_traits/std::reference_wrapper::get
- type_traits/std::reference_wrapper::operator()
dev_langs:
- C++
helpviewer_keywords:
- reference_wrapper class
- reference_wrapper
ms.assetid: 90b8ed62-e6f1-44ed-acc7-9619bd58865a
caps.latest.revision: 21
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
ms.sourcegitcommit: f0e7b22e4fbd6f54d390adfe70f7bfb99e4bc5df
ms.openlocfilehash: 1b6968f2300e5214575cc5385c136d6f27bab10a
ms.lasthandoff: 02/24/2017

---
# <a name="referencewrapper-class"></a>reference_wrapper 类
包装引用。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Ty>  
class reference_wrapper  
{  
public:  
    typedef Ty type;  
 
    reference_wrapper(Ty&) noexcept;
    operator Ty&() const noexcept;
    Ty& get() const noexcept;

    template <class... Types> 
    auto operator()(Types&&... args) const ->
        decltype(std::invoke(get(), std::forward<Types>(args)...));
 
private:  
    Ty *ptr; // exposition only  
};  
```  
  
## <a name="remarks"></a>备注  
`reference_wrapper<Ty>` 是可构造副本和可指定副本的包装器，它包装对某个 `Ty` 类型对象或函数的引用，并具有指向该类型对象的指针。 `reference_wrapper` 可用于将引用存储在标准容器内，并根据对 `std::bind` 的引用传递对象。  
  
类型 `Ty` 必须是一种对象类型或函数类型，或会在编译时失败的静态断言。  
  
帮助程序函数 [std::ref](functional-functions.md#ref_function) 和 [std::cref](functional-functions.md#cref_function) 可以用于创建 `reference_wrapper` 对象。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[reference_wrapper::reference_wrapper](#reference_wrapper)|构造一个 `reference_wrapper`。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[reference_wrapper::result_type](#result_type)|已包装引用的弱结果类型。|  
|[reference_wrapper::type](#type)|已包装引用的类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[reference_wrapper::get](#get)|获取已包装的引用。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[reference_wrapper::operator Ty&amp;](#operator_ty_amp_)|获取指向已包装引用的指针。|  
|[reference_wrapper::operator()](#operator_call)|调用已包装的引用。|  
## <a name="requirements"></a>要求  
 **标头：**\<functional>  
  
 **命名空间：** std  
  
##  <a name="a-namegeta--referencewrapperget"></a><a name="get"></a>  reference_wrapper::get  
 获取已包装的引用。  
  
```  
Ty& get() const noexcept;
```  
  
### <a name="remarks"></a>备注  
成员函数返回已包装的引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__reference_wrapper_get.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int main() {   
    int i = 1;   
    std::reference_wrapper<int> rwi(i);   
  
    std::cout << "i = " << i << std::endl;   
    std::cout << "rwi = " << rwi << std::endl;   
    rwi.get() = -1;   
    std::cout << "i = " << i << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
i = 1  
rwi = 1  
i = -1  
```  
  
##  <a name="a-nameoperatortyampa--referencewrapperoperator-tyamp"></a><a name="operator_ty_amp_"></a>reference_wrapper::operator Ty&amp;  
 获取已包装的引用。  
  
```  
operator Ty&() const noexcept;
```  
  
### <a name="remarks"></a>备注  
 该成员运算符将返回 `*ptr`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__reference_wrapper_operator_cast.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int main() {   
    int i = 1;   
    std::reference_wrapper<int> rwi(i);   
  
    std::cout << "i = " << i << std::endl;   
    std::cout << "(int)rwi = " << (int)rwi << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
i = 1  
(int)rwi = 1  
```  
  
##  <a name="a-nameoperatorcalla--referencewrapperoperator"></a><a name="operator_call"></a>reference_wrapper::operator()  
 调用已包装的引用。  
  
```  
template <class... Types>  
auto operator()(Types&&... args);
```  
  
### <a name="parameters"></a>参数  
 `Types`  
 参数列表类型。  
  
 `args`  
 参数列表。  
  
### <a name="remarks"></a>备注  
 模板成员 `operator()` 返回 `std::invoke(get(), std::forward<Types>(args)...)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__reference_wrapper_operator_call.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val) {   
    return (-val);   
}   
  
int main() {   
    std::reference_wrapper<int (int)> rwi(neg);   
  
    std::cout << "rwi(3) = " << rwi(3) << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
rwi(3) = -3  
```  
  
##  <a name="a-namereferencewrappera--referencewrapperreferencewrapper"></a><a name="reference_wrapper"></a>  reference_wrapper::reference_wrapper  
 构造一个 `reference_wrapper`。  
  
```  
reference_wrapper(Ty& val) noexcept;
```  
  
### <a name="parameters"></a>参数  
 `Ty`  
 要包装的类型。  
  
 `val`  
 要包装的值。  
  
### <a name="remarks"></a>备注  
 该构造函数将存储的值 `ptr` 设置为 `&val`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__reference_wrapper_reference_wrapper.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val) {   
    return (-val);   
}   
  
int main() {   
    int i = 1;   
    std::reference_wrapper<int> rwi(i);   
  
    std::cout << "i = " << i << std::endl;   
    std::cout << "rwi = " << rwi << std::endl;   
    rwi.get() = -1;   
    std::cout << "i = " << i << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
i = 1  
rwi = 1  
i = -1  
```  
  
##  <a name="a-nameresulttypea--referencewrapperresulttype"></a><a name="result_type"></a>  reference_wrapper::result_type  
 已包装引用的弱结果类型。  
  
```  
typedef R result_type;  
```  
  
### <a name="remarks"></a>备注  
 `result_type` typedef 是已包装函数的弱结果类型的同义词。 typedef 仅对函数类型有意义。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__reference_wrapper_result_type.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val) {   
    return (-val);   
}   
  
int main() {   
    typedef std::reference_wrapper<int (int)> Mywrapper;   
    Mywrapper rwi(neg);   
    Mywrapper::result_type val = rwi(3);   
  
    std::cout << "val = " << val << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
val = -3  
```  
  
##  <a name="a-nametypea--referencewrappertype"></a><a name="type"></a>  reference_wrapper::type  
 已包装引用的类型。  
  
```  
typedef Ty type;  
```  
  
### <a name="remarks"></a>备注  
 Typedef 是模板参数 `Ty`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__functional__reference_wrapper_type.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
int neg(int val) {   
    return (-val);   
}   
  
int main() {   
    int i = 1;   
    typedef std::reference_wrapper<int> Mywrapper;   
    Mywrapper rwi(i);   
    Mywrapper::type val = rwi.get();   
  
    std::cout << "i = " << i << std::endl;   
    std::cout << "rwi = " << val << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
i = 1  
rwi = 1  
```  
  
## <a name="see-also"></a>另请参阅  
 [cref 函数](../standard-library/functional-functions.md#cref_function)   
 [ref 函数](../standard-library/functional-functions.md#ref_function)


