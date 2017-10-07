---
title: "is_pod 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::is_pod
dev_langs:
- C++
helpviewer_keywords:
- is_pod class
- is_pod
ms.assetid: d73ebdee-746b-4082-9fa4-2db71432eb0e
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: efe54ef10c8ab8102e17efdbf8e38f217ec2e0df
ms.contentlocale: zh-cn
ms.lasthandoff: 10/03/2017

---
# <a name="ispod-class"></a>is_pod 类
测试类型是否为 POD。  
  
## <a name="syntax"></a>语法  
  
```
template <class T>
struct is_pod;
```  
  
#### <a name="parameters"></a>参数  
*T*  
要查询的类型。  
  
## <a name="remarks"></a>备注  
如果类型 *T* 为纯旧数据 (POD)，则 `is_pod<T>::value` 为 `true`。 否则为 `false`。  
  
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
  
## <a name="example"></a>示例  
  
```cpp  
// std__type_traits__is_pod.cpp   
// compile with: /EHsc   
#include <type_traits>   
#include <iostream>   
  
struct trivial {   
    int val;   
};   
  
struct throws {   
    throws() {}  // User-declared ctor, so not POD
  
    int val;   
};   
  
int main() {   
    std::cout << "is_pod<trivial> == " << std::boolalpha   
        << std::is_pod<trivial>::value << std::endl;   
    std::cout << "is_pod<int> == " << std::boolalpha   
        << std::is_pod<int>::value << std::endl;   
    std::cout << "is_pod<throws> == " << std::boolalpha   
        << std::is_pod<throws>::value << std::endl;   
  
    return (0);   
}  
```  
  
```Output  
is_pod<trivial> == true  
is_pod<int> == true  
is_pod<throws> == false  
```  
  
## <a name="requirements"></a>要求  
**标头：**\<type_traits>  
  
**命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
[<type_traits>](../standard-library/type-traits.md)




