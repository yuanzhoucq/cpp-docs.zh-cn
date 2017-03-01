---
title: "&lt;memory&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::operator!=
- memory/std::operator>
- memory/std::operator>=
- memory/std::operator<
- memory/std::operator<=
- memory/std::operator<<
- memory/std::operator==
ms.assetid: 257e3ba9-c4c2-4ae8-9b11-b156ba9c28de
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 28baed4badda4f2c1d7e5b20235fe8d40c2a7195
ms.openlocfilehash: 50cfd9e09a7534ea7c615ebf6b0c781806013965
ms.lasthandoff: 02/24/2017

---
# <a name="ltmemorygt-operators"></a>&lt;memory&gt; 运算符
||||  
|-|-|-|  
|[operator!=](#operator_neq)|[operator&gt;](#operator_gt_)|[operator&gt;=](#operator_gt__eq)|  
|[operator&lt;](#operator_lt_)|[operator&lt;&lt;](#operator_lt__lt_)|[operator&lt;=](#operator_lt__eq)|  
|[operator==](#operator_eq_eq)|  
  
##  <a name="a-nameoperatorneqa--operator"></a><a name="operator_neq"></a>operator!=  
 测试各对象之间是否不相等。  
  
```  
template <class Type, class Other>  
bool operator!=(
    const allocator<Type>& left,  
    const allocator<Other>& right) throw();

template <class T, class Del1, class U, class Del2>  
bool operator!=(
    const unique_ptr<T, Del1>& left,  
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>  
bool operator!=(
    const shared_ptr<Ty1>& left,  
    const shared_ptr<Ty2>& right);
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 要测试不相等的对象之一。  
  
 ` right`  
 要测试不相等的对象之一。  
  
 `Ty1`  
 由左侧共享指针控制的类型。  
  
 `Ty2`  
 由右侧共享指针控制的类型。  
  
### <a name="return-value"></a>返回值  
 如果对象不相等，则为 **true**；如果对象相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 第一个模板运算符返回 false。 （所有默认分配器都相等。）  
  
 第二个和第三个模板运算符返回 `!(`` left` `==` ` right``)`。  
  
### <a name="example"></a>示例  
  
```cpp  
// memory_op_me.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main( )   
{  
   allocator<double> Alloc;  
   vector <char>:: allocator_type v1Alloc;  
  
   if ( Alloc != v1Alloc )  
      cout << "The allocator objects Alloc & v1Alloc not are equal."  
           << endl;  
   else  
      cout << "The allocator objects Alloc & v1Alloc are equal."  
           << endl;  
}  
```  
  
```Output  
The allocator objects Alloc & v1Alloc are equal.  
```  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__operator_ne.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()   
    {   
    std::shared_ptr<int> sp0(new int(0));   
    std::shared_ptr<int> sp1(new int(0));   
  
    std::cout << "sp0 != sp0 == " << std::boolalpha   
        << (sp0 != sp0) << std::endl;   
    std::cout << "sp0 != sp1 == " << std::boolalpha   
        << (sp0 != sp1) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
sp0 != sp0 == false  
sp0 != sp1 == true  
```  
  
##  <a name="a-nameoperatoreqeqa--operator"></a><a name="operator_eq_eq"></a>operator==  
 测试两个对象是否相等。  
  
```  
template <class Type, class Other>  
bool operator==(
    const allocator<Type>& left,  
    const allocator<Other>& right) throw();

template <class Ty1, class Del1, class Ty2, class Del2>  
bool operator==(
    const unique_ptr<Ty1, Del1>& left,  
    const unique_ptr<Ty2, Del2>& right);

template <class Ty1, class Ty2>  
bool operator==(
    const shared_ptr<Ty1>& left;,  
    const shared_ptr<Ty2>& right);
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 要测试是否相等的其中一个对象。  
  
 ` right`  
 要测试是否相等的其中一个对象。  
  
 `Ty1`  
 由左侧共享指针控制的类型。  
  
 `Ty2`  
 由右侧共享指针控制的类型。  
  
### <a name="return-value"></a>返回值  
 如果对象相等，则为 `true`，如果对象不相等，则为 `false`。  
  
### <a name="remarks"></a>备注  
 第一个模板运算符返回 true。 （所有默认分配器都相等。）  
  
 第二个和第三个模板运算符返回 ` left.get() ==  right.get()`。  
  
### <a name="example"></a>示例  
  
```cpp  
// memory_op_eq.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
int main( )   
{  
   allocator<char> Alloc;  
   vector <int>:: allocator_type v1Alloc;  
  
   allocator<char> cAlloc(Alloc);   
   allocator<int> cv1Alloc(v1Alloc);  
  
   if ( cv1Alloc == v1Alloc )  
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."  
           << endl;  
   else  
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."  
           << endl;  
  
   if ( cAlloc == Alloc )  
      cout << "The allocator objects cAlloc & Alloc are equal."  
           << endl;  
   else  
      cout << "The allocator objects cAlloc & Alloc are not equal."  
           << endl;  
}  
```  
  
```Output  
The allocator objects cv1Alloc & v1Alloc are equal.  
The allocator objects cAlloc & Alloc are equal.  
```  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__operator_eq.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()   
    {   
    std::shared_ptr<int> sp0(new int(0));   
    std::shared_ptr<int> sp1(new int(0));   
  
    std::cout << "sp0 == sp0 == " << std::boolalpha   
        << (sp0 == sp0) << std::endl;   
    std::cout << "sp0 == sp1 == " << std::boolalpha   
        << (sp0 == sp1) << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
sp0 == sp0 == true  
sp0 == sp1 == false  
```  
  
##  <a name="a-nameoperatorgteqa--operatorgt"></a><a name="operator_gt__eq"></a>operator&gt;=  
 测试一个对象是否大于或等于另一个对象。  
  
```  
template <class T, class Del1, class U, class Del2>  
bool operator>=(
    const unique_ptr<T, Del1>& left,  
    const unique_ptr<U, Del2>& right);

template <class Ty1, class Ty2>  
bool operator>=(
    const shared_ptr<Ty1>& left,  
    const shared_ptr<Ty2>& right);
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 要比较的对象之一。  
  
 ` right`  
 要比较的对象之一。  
  
 `Ty1`  
 由左侧共享指针控制的类型。  
  
 `Ty2`  
 由右侧共享指针控制的类型。  
  
### <a name="remarks"></a>备注  
 模板运算符返回 ` left``.get() >=` ` right``.get()`。  
  
##  <a name="a-nameoperatorlta--operatorlt"></a><a name="operator_lt_"></a>operator&lt;  
 测试某一对象是否小于另一对象。  
  
```  
template <class T, class Del1, class U, class Del2>  
bool operator<(
    const unique_ptr<T, Del1>& left,  
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>  
bool operator<(
    const shared_ptr<Ty1>& left,  
    const shared_ptr<Ty2>& right);
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 要比较的对象之一。  
  
 ` right`  
 要比较的对象之一。  
  
 `Ty1`  
 由左侧指针控制的类型。  
  
 `Ty2`  
 由右侧指针控制的类型。  
  
##  <a name="a-nameoperatorlteqa--operatorlt"></a><a name="operator_lt__eq"></a>operator&lt;=  
 测试某一对象是否小于或等于另一个对象。  
  
```  
template <class T, class Del1, class U, class Del2>  
bool operator<=(
    const unique_ptr<T, Del1>& left,  
    const unique_ptr<U&, Del2>& right);

template <class Ty1, class Ty2>  
bool operator<=(
    const shared_ptr<Ty1>& left,  
    const shared_ptr<Ty2>& right);
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 要比较的对象之一。  
  
 ` right`  
 要比较的对象之一。  
  
 `Ty1`  
 由左侧共享指针控制的类型。  
  
 `Ty2`  
 由右侧共享指针控制的类型。  
  
### <a name="remarks"></a>备注  
 模板运算符返回 ` left``.get() <=` ` right``.get()`  
  
##  <a name="a-nameoperatorgta--operatorgt"></a><a name="operator_gt_"></a>operator&gt;  
 测试一个对象是否大于或等于第二个对象。  
  
```  
template <class Ty1, class Del1, class Ty2, class Del2>  
bool operator>(
    const unique_ptr<Ty1, Del1>& left,  
    const unique_ptr<Ty2&, Del2gt;& right);

template <class Ty1, class Ty2>  
bool operator>(
    const shared_ptr<Ty1>& left,  
    const shared_ptr<Ty2>& right);
```  
  
### <a name="parameters"></a>参数  
 ` left`  
 要比较的对象之一。  
  
 ` right`  
 要比较的对象之一。  
  
 `Ty1`  
 由左侧共享指针控制的类型。  
  
 `Ty2`  
 由右侧共享指针控制的类型。  
  
##  <a name="a-nameoperatorltlta--operatorltlt"></a><a name="operator_lt__lt_"></a>operator&lt;&lt;  
将共享指针写入该流。  
  
```  
template <class Elem, class Tr, class Ty>  
std::basic_ostream<Elem, Tr>& operator<<(std::basic_ostream<Elem, Tr>& out,  
    shared_ptr<Ty>& sp);
```  
  
### <a name="parameters"></a>参数  
 `Elem`  
 流元素的类型。  
  
 `Tr`  
 流元素特征的类型。  
  
 `Ty`  
 由共享指针控制的类型。  
  
 `out`  
 输出流。  
  
 `sp`  
 共享的指针。  
  
### <a name="remarks"></a>备注  
 此模板函数返回 `out << sp.get()`。  
  
### <a name="example"></a>示例  
  
```cpp  
// std__memory__operator_sl.cpp   
// compile with: /EHsc   
#include <memory>   
#include <iostream>   
  
int main()   
    {   
    std::shared_ptr<int> sp0(new int(5));   
  
    std::cout << "sp0 == " << sp0 << " (varies)" << std::endl;   
  
    return (0);   
    }  
  
```  
  
```Output  
sp0 == 3f3040 (varies)  
```  
  
## <a name="see-also"></a>另请参阅  
 [\<memory>](../standard-library/memory.md)


