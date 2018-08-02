---
title: 矢量 (STL/CLR) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::vector
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::vector::assign
- cliext::vector::at
- cliext::vector::back
- cliext::vector::back_item
- cliext::vector::begin
- cliext::vector::capacity
- cliext::vector::clear
- cliext::vector::const_iterator
- cliext::vector::const_reference
- cliext::vector::const_reverse_iterator
- cliext::vector::difference_type
- cliext::vector::empty
- cliext::vector::end
- cliext::vector::erase
- cliext::vector::front
- cliext::vector::front_item
- cliext::vector::generic_container
- cliext::vector::generic_iterator
- cliext::vector::generic_reverse_iterator
- cliext::vector::generic_value
- cliext::vector::insert
- cliext::vector::iterator
- cliext::vector::operator=
- cliext::vector::operator
- cliext::vector::pop_back
- cliext::vector::push_back
- cliext::vector::rbegin
- cliext::vector::reference
- cliext::vector::rend
- cliext::vector::reserve
- cliext::vector::resize
- cliext::vector::reverse_iterator
- cliext::vector::size
- cliext::vector::size_type
- cliext::vector::swap
- cliext::vector::to_array
- cliext::vector::value_type
- cliext::vector::vector
dev_langs:
- C++
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> (vector) member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- capacity member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- pop_back member [STL/CLR]
- push_back member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reserve member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- vector member [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 426fbb9b63065218158a199a32e5addca70eba9c
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376178"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)
此模板类描述一个对象，用于控制不同长度序列元素的随机访问。 使用容器`vector`来管理一系列元素作为一个连续的存储块。 块作为一个数组，其中根据需要增长。  
  
 在下面的说明`GValue`等同于*值*后者是 ref 类型，除非在此情况下是`Value^`。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template<typename Value>  
    ref class vector  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IVector<GValue>  
    { ..... };  
```  
  
### <a name="parameters"></a>参数  
 *值*  
 受控序列中的元素的类型。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/向量 >  
  
 **Namespace:** cliext  

## <a name="declarations"></a>声明  
  
|类型定义|描述|  
|---------------------|-----------------|  
|[vector::const_iterator (STL/CLR)](#const_iterator)|受控序列的常量迭代器的类型。|  
|[vector::const_reference (STL/CLR)](#const_reference)|元素的常量引用的类型。|  
|[vector::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|受控序列的常量反向迭代器的类型。|  
|[vector::difference_type (STL/CLR)](#difference_type)|两个元素间的带符号距离的类型。|  
|[vector::generic_container (STL/CLR)](#generic_container)|泛型接口的容器的类型。|  
|[vector::generic_iterator (STL/CLR)](#generic_iterator)|泛型接口的容器的迭代器的类型。|  
|[vector::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型接口的反向迭代器的类型。|  
|[vector::generic_value (STL/CLR)](#generic_value)|容器的泛型接口的元素的类型。|  
|[vector::iterator (STL/CLR)](#iterator)|受控序列的迭代器的类型。|  
|[vector::reference (STL/CLR)](#reference)|元素的引用的类型。|  
|[vector::reverse_iterator (STL/CLR)](#reverse_iterator)|受控序列的反向迭代器的类型。|  
|[vector::size_type (STL/CLR)](#size_type)|两个元素间的带符号距离的类型。|  
|[vector::value_type (STL/CLR)](#value_type)|元素的类型。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[vector::assign (STL/CLR)](#assign)|替换所有元素。|  
|[vector::at (STL/CLR)](#at)|访问指定位置处的元素。|  
|[vector::back (STL/CLR)](#back)|访问最后一个元素。|  
|[vector::begin (STL/CLR)](#begin)|指定受控序列的开头。|  
|[vector::capacity (STL/CLR)](#capacity)|报告已分配的存储容器的大小。|  
|[vector::clear (STL/CLR)](#clear)|删除所有元素。|  
|[vector::empty (STL/CLR)](#empty)|测试元素是否存在。|  
|[vector::end (STL/CLR)](#end)|指定受控序列的末尾。|  
|[vector::erase (STL/CLR)](#erase)|移除指定位置处的元素。|  
|[vector::front (STL/CLR)](#front)|访问第一个元素。|  
|[vector::insert (STL/CLR)](#insert)|将元素添加的指定位置。|  
|[vector::pop_back (STL/CLR)](#pop_back)|删除最后一个元素。|  
|[vector::push_back (STL/CLR)](#push_back)|添加一个新的最后一个元素。|  
|[vector::rbegin (STL/CLR)](#rbegin)|指定反向受控序列的开头。|  
|[vector::rend (STL/CLR)](#rend)|指定反向受控序列的末尾。|  
|[vector::reserve (STL/CLR)](#reserve)|可确保容器的最小增长容量。|  
|[vector::resize (STL/CLR)](#resize)|更改元素的数。|  
|[vector::size (STL/CLR)](#size)|对元素数进行计数。|  
|[vector::swap (STL/CLR)](#swap)|交换两个容器的内容。|  
|[vector::to_array (STL/CLR)](#to_array)|将受控的序列复制到新数组。|  
|[vector::vector (STL/CLR)](#vector)|构造容器对象。|  
  
|属性|描述|  
|--------------|-----------------|  
|[vector::back_item (STL/CLR)](#back_item)|访问最后一个元素。|  
|[vector::front_item (STL/CLR)](#front_item)|访问第一个元素。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[vector::operator= (STL/CLR)](#op_as)|替换受控序列。|  
|[vector::operator(STL/CLR)](#op)|访问指定位置处的元素。|  
|[operator!= (vector) (STL/CLR)](#op_neq)|确定是否`vector`对象不等于另一个`vector`对象。|  
|[operator< (vector) (STL/CLR)](#op_lt)|确定是否`vector`对象是否小于另一个`vector`对象。|  
|[operator<= (vector) (STL/CLR)](#op_lteq)|确定是否`vector`对象是否小于或等于另一个`vector`对象。|  
|[operator== (vector) (STL/CLR)](#op_eq)|确定是否`vector`对象是否等于另一个`vector`对象。|  
|[operator> (vector) (STL/CLR)](#op_gt)|确定是否`vector`对象是否大于另一个`vector`对象。|  
|[operator>= (vector) (STL/CLR)](#op_gteq)|确定是否`vector`对象是否大于或等于另一个`vector`对象。|  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重复的对象。|  
|<xref:System.Collections.IEnumerable>|通过元素的序列。|  
|<xref:System.Collections.ICollection>|维护组元素。|  
|<xref:System.Collections.Generic.IEnumerable%601>|通过类型化的元素进行排序。|  
|<xref:System.Collections.Generic.ICollection%601>|维护的组类型化的元素。|  
|<xref:System.Collections.Generic.IList%601>|维护类型化元素的有序的的组。|  
|IVector < 值\>|维护泛型容器。|  
  
## <a name="remarks"></a>备注  
 该对象分配并释放存储的存储阵列通过其控制的序列*值*元素，根据需要增长。 将新元素追加的成本是分期常量时间内的方式增长。 换而言之，在末尾添加元素的成本不会增加，一般情况下，按受控的序列获取较大的长度。 因此，一个向量是模板类的基础容器的良好候选项[堆栈 (STL/CLR)](../dotnet/stack-stl-clr.md)。  
  
 一个`vector`支持随机访问迭代器，这意味着您可以引用元素直接给定其数字位置，范围为从第一个 （正面） 元素的零到`size() - 1`的最后一个 （返回） 元素。 这还意味着向量是模板类的基础容器的良好候选项[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)。  
  
 向量迭代器，用于存储其关联的向量对象，以及它将指定的元素的偏移的句柄。 迭代器只能用于其关联的容器对象。 矢量元素的偏移是它的位置相同。  
  
 插入或清除元素可以更改存储在给定的位置，因此还可以更改由迭代器指定的值的元素值。 （该容器可能需要将元素复制向上或向下创建之前插入一个孔或擦除后填充一个三角形孔。）不过，向量迭代器保持有效，只要其偏置的范围是`[0, size()]`。 此外，有效的迭代器保持现在-可以使用它来访问或更改，只要其偏差不等于此元素的值指定- `size()`。  
  
 擦除或删除元素调用析构函数为其存储的值。 销毁容器清除所有元素。 因此，其元素类型是 ref 类的容器可确保任何元素的生存期长于容器。 但请注意，容器的句柄不会销毁它的元素。  
  
## <a name="members"></a>成员

## <a name="assign"></a> vector:: assign (STL/CLR)
替换所有元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void assign(size_type count, value_type val);  
template<typename InIt>  
    void assign(InIt first, InIt last);  
void assign(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>参数  
 *count*  
 要插入的元素数。  
  
 *first*  
 要插入范围的起始处。  
  
 *最后一个*  
 要插入的范围的下限。  
  
 *right*  
 要插入的枚举。  
  
 *val*  
 要插入的元素的值。  
  
### <a name="remarks"></a>备注  
 第一个成员函数替换受控的序列的重复*计数*值的元素*val*。 您使用它来填充容器元素与所有具有相同的值。  
  
 如果`InIt`是整数类型，第二个成员函数的行为相同`assign((size_type)first, (value_type)last)`。 否则，它与序列替换受控的序列 [`first`， `last`)。 您使用它来进行受控的序列副本另一个序列。  
  
 第三个成员函数使用指定的枚举器的序列替换受控的序列*右*。 您可以使用它来使受控的序列的枚举器所述的序列副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_assign.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::vector<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    c2.assign(c1.begin(), c1.end() - 1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an enumeration   
    c2.assign(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }   
```  
  
```Output  
x x x x x x  
a b  
a b c  
```  

## <a name="at"></a> vector:: at (STL/CLR)
访问指定位置处的元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
reference at(size_type pos);  
```  
  
#### <a name="parameters"></a>参数  
 *pos*  
 要访问的元素的位置。  
  
### <a name="remarks"></a>备注  
 此成员函数返回对受控序列位置处的元素的引用*pos*。使用它来读取或写入其位置的元素您知道。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_at.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using at   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1.at(1) = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a x c  
```  

## <a name="back"></a> vector:: back (STL/CLR)
访问最后一个元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
reference back();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回对受控序列，必须为非空的最后一个元素的引用。 用于访问的最后一个元素，当您知道它存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back() = {0}", c1.back());   
  
// alter last item and reinspect   
    c1.back() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
back() = c  
 a b x  
```  

## <a name="back_item"></a> vector::back_item (STL/CLR)
访问最后一个元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
property value_type back_item;  
```  
  
### <a name="remarks"></a>备注  
 属性访问，必须为非空的受控序列的最后一个元素。 您可以使用它来读取或写入的最后一个元素，当您知道它存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_back_item.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last item   
    System::Console::WriteLine("back_item = {0}", c1.back_item);   
  
// alter last item and reinspect   
    c1.back_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
back_item = c  
 a b x  
```  

## <a name="begin"></a> vector:: begin (STL/CLR)
指定受控序列的开头。  
  
### <a name="syntax"></a>语法  
  
```cpp  
iterator begin();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回指定第一个元素的受控序列，或刚超出空序列末尾的随机访问迭代器。 用于获取迭代器，指定`current`如果受控序列的长度发生更改，可以更改受控制的序列，但其状态的开头。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_begin.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
 x y c  
```  

## <a name="capacity"></a> vector:: capacity (STL/CLR)
报告已分配的存储容器的大小。  
  
### <a name="syntax"></a>语法  
  
```cpp  
size_type capacity();  
```  
  
### <a name="remarks"></a>备注  
 此成员函数返回当前分配的用于存放受控的序列的值至少为一样大的存储[vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`。 用于确定多少容器可以增长之前它必须重新分配受控序列的存储。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_capacity.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
capacity() = 4, ok = True  
capacity() = 9, ok = True  
```  

## <a name="clear"></a> vector:: clear (STL/CLR)
删除所有元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void clear();  
```  
  
### <a name="remarks"></a>备注  
 成员函数有效地调用[vector:: erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md) `(` [vector:: begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md) `(),` [vector:: end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `())`. 用于确保受控的序列为空。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_clear.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
size() = 0  
 a b  
size() = 0  
```  

## <a name="const_iterator"></a> vector:: const_iterator (STL/CLR)
受控序列的常量迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T2`可充当受控序列的常量随机访问迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_const_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a> vector:: const_reference (STL/CLR)
元素的常量引用的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述的元素的常量引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_const_reference.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        cliext::vector<wchar_t>::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a> vector:: const_reverse_iterator (STL/CLR)
受控序列的常量反向迭代器的类型...  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T4`可充当受控序列的常量反向迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::vector<wchar_t>::const_reverse_iterator crit = c1.rbegin();   
    cliext::vector<wchar_t>::const_reverse_iterator crend = c1.rend();   
    for (; crit != crend; ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="difference_type"></a> vector:: difference_type (STL/CLR)
两个元素之间的带符号距离的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述已签名的元素计数。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_difference_type.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::vector<wchar_t>::difference_type diff = 0;   
    for (cliext::vector<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it) ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (cliext::vector<wchar_t>::iterator it = c1.end();   
        it != c1.begin(); --it) --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
end()-begin() = 3  
begin()-end() = -3  
```  

## <a name="empty"></a> vector:: empty (STL/CLR)
测试元素是否存在。  
  
### <a name="syntax"></a>语法  
  
```cpp  
bool empty();  
```  
  
### <a name="remarks"></a>备注  
 对于空受控序列，该成员函数返回 true。 它等效于[vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`() == 0`。 用于测试是否向量为空。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_empty.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    System::Console::WriteLine("empty() = {0}", c1.empty());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  

## <a name="end"></a> vector:: end (STL/CLR)
指定受控序列的末尾。  
  
### <a name="syntax"></a>语法  
  
```cpp  
iterator end();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回一个随机访问迭代器，它指向刚超出受控序列的末尾。 用于获取迭代器，指定`current`如果受控序列的长度发生更改，可以更改结束的受控的序列，但其状态。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_end.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    cliext::vector<wchar_t>::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
  
// alter first two items and reinspect   
    *--it = L'x';   
    *++it = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
 a x y  
```  

## <a name="erase"></a> vector:: erase (STL/CLR)
移除指定位置处的元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>参数  
 *first*  
 要清除范围的起始处。  
  
 *最后一个*  
 要清除范围的末尾。  
  
 *where*  
 要清除的元素。  
  
### <a name="remarks"></a>备注  
 第一个成员函数删除由指向受控序列的元素*其中*。 用于删除单个元素。  
  
 第二个成员函数将移除范围 [`first`、`last`) 中的受控序列的元素。 用于删除零个或多个连续的元素。  
  
 这两个成员函数返回一个迭代器，指定已删除的任何元素之外保留的第一个元素或[vector:: end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `()`如果此类元素不存在。  
  
 如果清除元素，元素副本数呈线性之间的清除结束和邻近序列末尾的元素数目。 （时清除序列的任意一端的一个或多个元素，没有元素副本发生。）  
  
### <a name="example"></a>示例  
  
```cpp 
// cliext_vector_erase.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.push_back(L'd');   
    c1.push_back(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    cliext::vector<wchar_t>::iterator it = c1.end();   
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",   
        *c1.erase(c1.begin(), --it));   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }    
```  
  
```Output  
 a b c  
erase(begin()) = b  
 b c d e  
erase(begin(), end()-1) = e  
size() = 1  
```  

## <a name="front"></a> vector:: front (STL/CLR)
访问第一个元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
reference front();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回对受控序列，必须为非空的第一个元素的引用。 您可以使用它来读取或写入的第一个元素，当您知道它存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_front.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front() = {0}", c1.front());   
  
// alter first item and reinspect   
    c1.front() = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
front() = a  
 x b c  
```  

# <a name="front_item"></a> vector::front_item (STL/CLR)
访问第一个元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
property value_type front_item;  
```  
  
### <a name="remarks"></a>备注  
 属性访问，必须为非空的受控序列的第一个元素。 您可以使用它来读取或写入的第一个元素，当您知道它存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_front_item.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first item   
    System::Console::WriteLine("front_item = {0}", c1.front_item);   
  
// alter first item and reinspect   
    c1.front_item = L'x';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
front_item = a  
 x b c  
```  

# <a name="generic_container"></a> vector::generic_container (STL/CLR)
泛型接口的容器的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef Microsoft::VisualC::StlClr::  
    IVector<generic_value>  
    generic_container;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述该类模板容器的泛型接口。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_generic_container.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(gc1->end(), L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.push_back(L'e');   
  
    System::Collections::IEnumerator^ enum1 =   
        gc1->GetEnumerator();   
    while (enum1->MoveNext())   
        System::Console::Write(" {0}", enum1->Current);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a b c d  
a b c d e  
```  

## <a name="generic_iterator"></a> vector::generic_iterator (STL/CLR)
用于容器的泛型接口具有的迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerRandomAccessIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述可用于泛型接口为该类模板容器的泛型迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::vector<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a a c  
```  

# <a name="generic_reverse_iterator"></a> vector::generic_reverse_iterator (STL/CLR)
一个反向迭代器用于与容器的泛型接口的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述可用于泛型接口为该类模板容器的泛型反向迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::vector<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();   
    cliext::vector<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a c c  
```  

## <a name="generic_value"></a> vector::generic_value (STL/CLR)
用于容器的泛型接口具有的元素的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述类型的对象`GValue`描述使用的存储的元素值与此模板容器类的泛型接口。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_generic_value.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::vector<wchar_t>::generic_value gcval = *gcit;   
    *++gcit = gcval;   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a a c  
```  

## <a name="insert"></a> vector:: insert (STL/CLR)
将元素添加的指定位置。  
  
### <a name="syntax"></a>语法  
  
```cpp  
iterator insert(iterator where, value_type val);  
void insert(iterator where, size_type count, value_type val);  
template<typename InIt>  
    void insert(iterator where, InIt first, InIt last);  
void insert(iterator where,  
    System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>参数  
 *count*  
 要插入的元素数。  
  
 *first*  
 要插入范围的起始处。  
  
 *最后一个*  
 要插入的范围的下限。  
  
 *right*  
 要插入的枚举。  
  
 *val*  
 要插入的元素的值。  
  
 *where*  
 若要在其前插入的容器中的位置。  
  
### <a name="remarks"></a>备注  
 每个成员函数插入指向的元素之前的元素*其中*序列由剩余操作数指定受控序列中。  
  
 第一个成员函数将具有值的元素插入*val* ，并返回一个迭代器，指定新插入的元素。 用于插入迭代器指定的位置之前的单一元素。  
  
 第二个成员函数插入的重复*计数*值的元素*val*。 用于插入零个或多个连续元素的相同值的所有副本。  
  
 如果 `InIt` 是整数类型，则第三个成员函数的行为与 `insert(where, (size_type)first, (value_type)last)` 相同。 否则，它插入序列 [`first`， `last`)。 用于插入另一个序列中复制的零个或多个连续元素。  
  
 第四个成员函数将指定的序列插入*右*。 用于插入序列描述将枚举器。  
  
 在插入单个元素时，元素副本数呈线性之间插入点和最近序列末尾的元素数目。 （在一个或多个元素插入序列的任意一端时，任何元素副本会不发生。）如果`InIt`是一个输入迭代器，第三个成员函数有效地执行序列中的每个元素的单个插入。 否则为如果插入`N`元素，元素副本数目上呈线性`N`以及之间插入点和最近序列末尾的元素数目。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_insert.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::vector<wchar_t> c2;   
    c2.insert(c2.begin(), 2, L'y');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    it = c1.end();   
    c2.insert(c2.end(), c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    c2.insert(c2.begin(),   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
insert(begin()+1, L'x') = x  
 a x b c  
 y y  
 y y a x b  
 a x b c y y a x b  
```  
  
## <a name="iterator"></a> vector:: iterator (STL/CLR)
受控序列的迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T1`可充当受控序列的随机访问迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    it = c1.begin();   
    *it = L'x';   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
x b c  
```  

## <a name="op_as"></a> vector:: operator = (STL/CLR)
替换受控序列。  
  
### <a name="syntax"></a>语法  
  
```cpp  
vector<Value>% operator=(vector<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *right*  
 用于复制的容器。  
  
### <a name="remarks"></a>备注  
 成员运算符副本*右*对象，然后返回`*this`。 用于替换受控的序列中的受控序列的副本*右*。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_operator_as.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2 = c1;   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="op"></a> vector::operator(STL/CLR)
访问指定位置处的元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
reference operator[](size_type pos);  
```  
  
#### <a name="parameters"></a>参数  
 *pos*  
 要访问的元素的位置。  
  
### <a name="remarks"></a>备注  
 成员运算符返回位置处的元素 referene *pos*。您可以使用它来访问你知道其位置的元素。  
  
### <a name="example"></a>示例  
  
```cpp 
// cliext_vector_operator_sub.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using subscripting   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
  
// change an entry and redisplay   
    c1[1] = L'x';   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1[i]);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a x c  
```  

## <a name="pop_back"></a> vector:: pop_back (STL/CLR)
删除最后一个元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void pop_back();  
```  
  
### <a name="remarks"></a>备注  
 成员函数删除必须为非空的受控序列的最后一个元素。 您可以使用它来缩短在后一个元素的向量。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_pop_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_back();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b  
```  

## <a name="push_back"></a> vector:: push_back (STL/CLR)
添加一个新的最后一个元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void push_back(value_type val);  
```  
  
### <a name="remarks"></a>备注  
 成员函数将具有值的元素插入`val`受控序列的末尾。 用于将另一个元素追加到矢量。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_push_back.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  
  
## <a name="rbegin"></a> vector:: rbegin (STL/CLR)
指定反向受控序列的开头。  
  
### <a name="syntax"></a>语法  
  
```cpp  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回一个反向迭代器，指定受控序列，或刚超出空序列的开头的最后一个元素。 因此，它指定`beginning`反向序列。 用于获取迭代器，指定`current`如果受控序列的长度发生更改，可以更改的相反顺序的受控的序列，但其状态开始。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_rbegin.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
 a y x  
```  

## <a name="reference"></a> vector:: reference (STL/CLR)
元素的引用的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述的元素的引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_reference.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::vector<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::vector<wchar_t>::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
  
// modify contents " a b c"   
    for (it = c1.begin(); it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::vector<wchar_t>::reference ref = *it;   
  
        ref += (wchar_t)(L'A' - L'a');   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
A B C  
```  

## <a name="rend"></a> vector:: rend (STL/CLR)
指定反向受控序列的末尾。  
  
### <a name="syntax"></a>语法  
  
```cpp  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回一个反向迭代器指向刚超出开头的受控序列。 因此，它指定`end`反向序列。 用于获取迭代器，指定`current`如果受控序列的长度发生更改，可以更改的相反顺序的受控的序列，但其状态结束。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_rend.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
  
// alter first two items and reinspect   
    *--rit = L'x';   
    *++rit = L'y';   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
 y x c  
```  

## <a name="reserve"></a> vector:: reserve (STL/CLR)
可确保容器的最小增长容量。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void reserve(size_type count);  
```  
  
#### <a name="parameters"></a>参数  
 *count*  
 新的容器的最小容量。  
  
### <a name="remarks"></a>备注  
 成员函数确保`capacity()`此后返回至少*计数*。 用于确保容器不需要受控序列的存储，直到它已发展为指定的大小。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_reserve.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for (int i = 0; i < c1.size(); ++i)   
        System::Console::Write(" {0}", c1.at(i));   
    System::Console::WriteLine();   
  
// increase capacity   
    cliext::vector<wchar_t>::size_type cap = c1.capacity();   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        cap, c1.size() <= cap);   
    c1.reserve(cap + 5);   
    System::Console::WriteLine("capacity() = {0}, ok = {1}",   
        c1.capacity(), cap + 5 <= c1.capacity());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
capacity() = 4, ok = True  
capacity() = 9, ok = True  
```  

## <a name="resize"></a> vector:: resize (STL/CLR)
更改元素的数。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void resize(size_type new_size);  
void resize(size_type new_size, value_type val);  
```  
  
#### <a name="parameters"></a>参数  
 *new_size*  
 受控序列的新大小。  
  
 *val*  
 填充元素的值。  
  
### <a name="remarks"></a>备注  
 这两个成员函数，请确保[vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `()`此后返回*new_size*。 如果它必须使受控的序列更长，第一个成员函数追加具有值的元素`value_type()`，而第二个成员函数追加具有值的元素*val*。 若要使受控的序列更短，这两个成员函数有效地清除的最后一个元素[vector:: size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `() -` `new_size`时间。 用于确保受控的序列的大小*new_size*、 修整或填充当前的受控的序列。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_resize.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
    c1.resize(4);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// resize to empty   
    c1.resize(0);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// resize and pad   
    c1.resize(5, L'x');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
size() = 0  
 0 0 0 0  
size() = 0  
 x x x x x  
```  

## <a name="reverse_iterator"></a> vector:: reverse_iterator (STL/CLR)
受控序列的反向迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述了可充当受控序列的反向迭代器的未指定类型 `T3` 的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
  
// alter first element and redisplay   
    rit = c1.rbegin();   
    *rit = L'x';   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
x b a  
```  

## <a name="size"></a> vector:: size (STL/CLR)
对元素数进行计数。  
  
### <a name="syntax"></a>语法  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回受控序列的长度。 用于确定受控序列中当前元素的数目。 如果您关心的只是该序列是否具有非零大小，请参阅[vector:: empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)`()`。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_size.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
size() = 3 starting with 3  
size() = 0 after clearing  
size() = 2 after adding 2  
```  

## <a name="size_type"></a> vector:: size_type (STL/CLR)
两个元素间的带符号距离的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述非负元素计数。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_size_type.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::vector<wchar_t>::size_type diff = c1.end() - c1.begin();   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```  
  
## <a name="swap"></a> vector:: swap (STL/CLR)
交换两个容器的内容。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void swap(vector<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *right*  
 要与其交换内容的容器。  
  
### <a name="remarks"></a>备注  
 成员函数交换之间的受控的序列`*this`并*右*。 它是在常量时间内，则会引发任何异常。 您将其用作一种来交换两个容器的内容的快速方法。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_swap.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::vector<wchar_t> c2(5, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
x x x x x  
x x x x x  
a b c  
```  

## <a name="to_array"></a> vector::to_array (STL/CLR)
将受控的序列复制到新数组。  
  
### <a name="syntax"></a>语法  
  
```cpp  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回一个数组，包含对受控的序列。 用于获取数组形式的受控序列的副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_to_array.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.push_back(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (wchar_t elem in a1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c d  
a b c  
```  

## <a name="value_type"></a> vector:: value_type (STL/CLR)
元素的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数的同义词*值*。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_value_type.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using value_type   
    for (cliext::vector<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        cliext::vector<wchar_t>::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="vector"></a> vector:: vector (STL/CLR)
构造容器对象。  
  
### <a name="syntax"></a>语法  
  
```cpp  
vector();  
vector(vector<Value>% right);  
vector(vector<Value>^ right);  
explicit vector(size_type count);  
vector(size_type count, value_type val);  
template<typename InIt>  
    vector(InIt first, InIt last);  
vector(System::Collections::Generic::IEnumerable<Value>^ right);  
```  
  
#### <a name="parameters"></a>参数  
 *count*  
 要插入的元素数。  
  
 *first*  
 要插入范围的起始处。  
  
 *最后一个*  
 要插入的范围的下限。  
  
 *right*  
 要插入的对象或范围。  
  
 *val*  
 要插入的元素的值。  
  
### <a name="remarks"></a>备注  
 构造函数：  
  
 `vector();`  
  
 初始化受控的序列不包含任何元素。 用于指定空的初始受控的序列。  
  
 构造函数：  
  
 `vector(vector<Value>% right);`  
  
 初始化受控的序列与序列 [`right.begin()`， `right.end()`)。 用于指定是矢量对象控制的序列的副本的初始受控的序列*右*。  
  
 构造函数：  
  
 `vector(vector<Value>^ right);`  
  
 初始化受控的序列与序列 [`right->begin()`， `right->end()`)。 用于指定是由其句柄的向量对象控制的序列的副本的初始受控的序列*右*。  
  
 构造函数：  
  
 `explicit vector(size_type count);`  
  
 初始化具有的受控的序列*计数*每个值元素`value_type()`。 您使用它来填充容器元素与所有具有默认值。  
  
 构造函数：  
  
 `vector(size_type count, value_type val);`  
  
 初始化具有的受控的序列*计数*每个值元素*val*。 您使用它来填充容器元素与所有具有相同的值。  
  
 构造函数：  
  
 `template<typename InIt>`  
  
 `vector(InIt first, InIt last);`  
  
 初始化受控的序列与序列 [`first`， `last`)。 您可以使用它来使受控的序列的另一个序列副本。  
  
 构造函数：  
  
 `vector(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 初始化具有指定枚举器的序列的受控的序列*右*。 您可以使用它来使受控的序列描述将枚举器的另一个序列的副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_construct.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
// construct an empty container   
    cliext::vector<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::vector<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::vector<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::vector<wchar_t>::iterator it = c3.end();   
    cliext::vector<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::vector<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::vector<wchar_t> c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    return (0);   
    }  
```  
  
```Output  
size() = 0  
 0 0 0  
 x x x x x x  
 x x x x x  
 x x x x x x  
 x x x x x x  
 x x x x x x  
```  

## <a name="op_neq"></a> 运算符 ！ = （矢量） (STL/CLR)
Vector 不相等比较。  
  
### <a name="syntax"></a>语法  
  
```cpp  
template<typename Value>  
    bool operator!=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *left*  
 要比较的左容器。  
  
 *right*  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`!(left == right)`。 使用它来测试是否*左*未排序相同*右*时两个向量是比较的元素的方式。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_operator_ne.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] != [a b c] is {0}",   
        c1 != c1);   
    System::Console::WriteLine("[a b c] != [a b d] is {0}",   
        c1 != c2);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
 a b d  
[a b c] != [a b c] is False  
[a b c] != [a b d] is True  
```  

## <a name="op_lt"></a> 运算符&lt;（矢量） (STL/CLR)
向量小于比较。  
  
### <a name="syntax"></a>语法  
  
```cpp  
template<typename Value>  
    bool operator<(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *left*  
 要比较的左容器。  
  
 *right*  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数返回 true 当对于最低的位置`i`为其`!(right[i] < left[i])`它是还 true 的`left[i] < right[i]`。 否则，它将返回`left->size() < right->size()`使用它来测试是否*左*进行排序之前*右*时两个向量是比较的元素的方式。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_operator_lt.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] < [a b c] is {0}",   
        c1 < c1);   
    System::Console::WriteLine("[a b c] < [a b d] is {0}",   
        c1 < c2);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
 a b d  
[a b c] < [a b c] is False  
[a b c] < [a b d] is True  
```  

## <a name="op_lteq"></a> 运算符&lt;= （矢量） (STL/CLR)
Vector 小于或等于比较。  
  
### <a name="syntax"></a>语法  
  
```cpp  
template<typename Value>  
    bool operator<=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *left*  
 要比较的左容器。  
  
 *right*  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`!(right < left)`。 使用它来测试是否*左*未排序后*右*时两个向量是比较的元素的方式。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_operator_le.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] <= [a b c] is {0}",   
        c1 <= c1);   
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",   
        c2 <= c1);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
 a b d  
[a b c] <= [a b c] is True  
[a b d] <= [a b c] is False  
```  

## <a name="op_eq"></a> 运算符 = = （矢量） (STL/CLR)
向量相等比较。  
  
### <a name="syntax"></a>语法  
  
```cpp  
template<typename Value>  
    bool operator==(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *left*  
 要比较的左容器。  
  
 *right*  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数才返回 true，序列由控制*左*并*右*具有相同的长度和每个位置`i`， `left[i] ==` `right[i]`。 使用它来测试是否*左*进行排序相同*右*时两个向量是比较的元素的方式。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_operator_eq.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] == [a b c] is {0}",   
        c1 == c1);   
    System::Console::WriteLine("[a b c] == [a b d] is {0}",   
        c1 == c2);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
 a b d  
[a b c] == [a b c] is True  
[a b c] == [a b d] is False  
```  

## <a name="op_gt"></a> 运算符&gt;（矢量） (STL/CLR)
大于比较的向量。  
  
### <a name="syntax"></a>语法  
  
```cpp  
template<typename Value>  
    bool operator>(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *left*  
 要比较的左容器。  
  
 *right*  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数将返回`right` `<` `left`。 使用它来测试是否*左*进行排序后*右*时两个向量是比较的元素的方式。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_operator_gt.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] > [a b c] is {0}",   
        c1 > c1);   
    System::Console::WriteLine("[a b d] > [a b c] is {0}",   
        c2 > c1);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
 a b d  
[a b c] > [a b c] is False  
[a b d] > [a b c] is True  
```  

## <a name="op_gteq"></a> 运算符&gt;= （矢量） (STL/CLR)
向量大于或等于比较。  
  
### <a name="syntax"></a>语法  
  
```cpp  
template<typename Value>  
    bool operator>=(vector<Value>% left,  
        vector<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *left*  
 要比较的左容器。  
  
 *right*  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`!(left < right)`。 使用它来测试是否*左*未排序之前*右*时两个向量是比较的元素的方式。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_vector_operator_ge.cpp   
// compile with: /clr   
#include <cliext/vector>   
  
int main()   
    {   
    cliext::vector<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::vector<wchar_t> c2;   
    c2.push_back(L'a');   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
  
// display contents " a b d"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("[a b c] >= [a b c] is {0}",   
        c1 >= c1);   
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",   
        c1 >= c2);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
 a b d  
[a b c] >= [a b c] is True  
[a b c] >= [a b d] is False  
```  