---
title: "&lt;memory&gt; 运算符 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- memory/std::operator!=
- memory/std::operator>
- memory/std::operator>=
- memory/std::operator<
- memory/std::operator<=
- memory/std::operator<<
- memory/std::operator==
dev_langs:
- C++
ms.assetid: 257e3ba9-c4c2-4ae8-9b11-b156ba9c28de
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dd02495ab42fd758cca28cfc5670ea1a1e7a2a83
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ltmemorygt-operators"></a>&lt;memory&gt; 运算符
||||  
|-|-|-|  
|[operator!=](#op_neq)|[operator&gt;](#op_gt)|[operator&gt;=](#op_gt_eq)|  
|[operator&lt;](#op_lt)|[operator&lt;&lt;](#op_lt_lt)|[operator&lt;=](#op_lt_eq)|  
|[operator==](#op_eq_eq)|  
  
##  <a name="op_neq"></a>operator!=  
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
 `left`  
 要测试不相等的对象之一。  
  
 `right`  
 要测试不相等的对象之一。  
  
 `Ty1`  
 由左侧共享指针控制的类型。  
  
 `Ty2`  
 由右侧共享指针控制的类型。  
  
### <a name="return-value"></a>返回值  
 如果对象不相等，则为 **true**；如果对象相等，则为 **false**。  
  
### <a name="remarks"></a>备注  
 第一个模板运算符返回 false。 （所有默认分配器都相等。）  
  
 第二个和第三个模板运算符返回 `!(left == right)`。  
  
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
  
##  <a name="op_eq_eq"></a>operator==  
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
 `left`  
 要测试是否相等的其中一个对象。  
  
 `right`  
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
  
##  <a name="op_gt_eq"></a>  operator&gt;=  
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
 `left`  
 要比较的对象之一。  
  
 `right`  
 要比较的对象之一。  
  
 `Ty1`  
 由左侧共享指针控制的类型。  
  
 `Ty2`  
 由右侧共享指针控制的类型。  
  
### <a name="remarks"></a>备注  
 模板运算符返回`left.get() >= right.get()`。  
  
##  <a name="op_lt"></a>operator&lt;  
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
 `left`  
 要比较的对象之一。  
  
 `right`  
 要比较的对象之一。  
  
 `Ty1`  
 由左侧指针控制的类型。  
  
 `Ty2`  
 由右侧指针控制的类型。  
  
##  <a name="op_lt_eq"></a>  operator&lt;=  
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
 `left`  
 要比较的对象之一。  
  
 `right`  
 要比较的对象之一。  
  
 `Ty1`  
 由左侧共享指针控制的类型。  
  
 `Ty2`  
 由右侧共享指针控制的类型。  
  
### <a name="remarks"></a>备注  
 模板运算符返回 `left.get() <= right.get()`  
  
##  <a name="op_gt"></a>operator&gt;  
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
 `left`  
 要比较的对象之一。  
  
 `right`  
 要比较的对象之一。  
  
 `Ty1`  
 由左侧共享指针控制的类型。  
  
 `Ty2`  
 由右侧共享指针控制的类型。  
  
##  <a name="op_lt_lt"></a>  operator&lt;&lt;  
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
  
## <a name="see-also"></a>请参阅  
 [\<memory>](../standard-library/memory.md)

