---
title: "add_rvalue_reference 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::add_rvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- add_rvalue_reference Class
ms.assetid: 76b0cb7c-1031-45d0-b409-f03ab0297580
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: ba7959b602a18ab4072dfb84238e95077337be3d
ms.contentlocale: zh-cn
ms.lasthandoff: 09/27/2017

---
# <a name="addrvaluereference-class"></a>add_rvalue_reference 类
如果模板参数是对象或函数类型，则创建模板参数的右值引用类型。 否则，由于引用折叠的语义，类型与模板参数相同。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template <class T>
struct add_rvalue_reference;

template <class T>
using add_rvalue_reference_t = typename add_rvalue_reference<T>::type;
```  
  
#### <a name="parameters"></a>参数  
 T  
 要修改的类型。  
  
## <a name="remarks"></a>备注  
 `add_rvalue_reference` 类具有名为 `type` 的成员，它是模板参数 `T` 的右值引用类型的别名。 对于非对象和非函数类型 `T`，引用折叠的语义意味着 `T&&` 是 `T`。 例如，当 `T` 是一个左值引用类型时，`add_rvalue_reference<T>::type` 是左值引用类型，而不是右值引用。  
  
 为了方便起见，<type_traits> 定义了一个帮助程序模板 `add_rvalue_reference_t`，用于为 `add_rvalue_reference` 的 `type` 成员命名别名。  
  
## <a name="example"></a>示例  
 此代码示例使用 static_assert 来显示如何使用 `add_rvalue_reference` 和 `add_rvalue_reference_t` 创建右值引用类型，以及 `add_rvalue_reference` 针对左值引用类型的结果如何不是右值引用，而是到左值引用类型的折叠。  
  
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
  
## <a name="requirements"></a>要求  
 标头：< type_traits > 命名空间：std  
  
## <a name="see-also"></a>另请参阅  
 [<type_traits>](../standard-library/type-traits.md)   
 [add_lvalue_reference 类](../standard-library/add-lvalue-reference-class.md)   
 [is_rvalue_reference 类](../standard-library/is-rvalue-reference-class.md)

