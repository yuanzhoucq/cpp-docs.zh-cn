---
title: 列表 (STL/CLR) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::list
- cliext::list::assign
- cliext::list::assign
- cliext::list::back
- cliext::list::back_item
- cliext::list::begin
- cliext::list::clear
- cliext::list::const_iterator
- cliext::list::const_reference
- cliext::list::const_reverse_iterator
- cliext::list::difference_type
- cliext::list::empty
- cliext::list::end
- cliext::list::erase
- cliext::list::front
- cliext::list::front_item
- cliext::list::generic_container
- cliext::list::generic_iterator
- cliext::list::generic_reverse_iterator
- cliext::list::generic_value
- cliext::list::insert
- cliext::list::iterator
- cliext::list::list
- cliext::list::merge
- cliext::list::operator=
- cliext::list::pop_back
- cliext::list::pop_front
- cliext::list::push_back
- cliext::list::push_front
- cliext::list::rbegin
- cliext::list::reference
- cliext::list::remove
- cliext::list::remove_if
- cliext::list::rend
- cliext::list::resize
- cliext::list::reverse
- cliext::list::reverse_iterator
- cliext::list::size
- cliext::list::size_type
- cliext::list::sort
- cliext::list::splice
- cliext::list::swap
- cliext::list::to_array
- cliext::list::unique
- cliext::list::value_type
- cliext::operator!=(list)
- cliext::operator<(list)
- cliext::operator<=(list)
- cliext::operator==(list)
- cliext::operator>(list)
- cliext::operator>=(list)
dev_langs:
- C++
helpviewer_keywords:
- <cliext/list> header [STL/CLR]
- list class [STL/CLR]
- <list> header [STL/CLR]
- assign member [STL/CLR]
- assign member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
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
- list member [STL/CLR]
- merge member [STL/CLR]
- operator= member [STL/CLR]
- pop_back member [STL/CLR]
- pop_front member [STL/CLR]
- push_back member [STL/CLR]
- push_front member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- remove member [STL/CLR]
- remove_if member [STL/CLR]
- rend member [STL/CLR]
- resize member [STL/CLR]
- reverse member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- sort member [STL/CLR]
- splice member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- unique member [STL/CLR]
- value_type member [STL/CLR]
- operator!=(list) member [STL/CLR]
- operator<(list) member [STL/CLR]
- operator<=(list) member [STL/CLR]
- operator==(list) member [STL/CLR]
- operator>(list) member [STL/CLR]
- operator>=(list) member [STL/CLR]
ms.assetid: a70c45c8-a257-4f6b-8434-b27ff6685bac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 8eb64c41db0e6062f2be636ddce7e8cefe0bb32b
ms.sourcegitcommit: bad2441d1930275ff506d44759d283d94cccd1c0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2018
ms.locfileid: "39376285"
---
# <a name="list-stlclr"></a>list (STL/CLR)
此模板类描述一个对象，用于控制不同长度序列元素的双向访问。 使用容器`list`来管理一系列元素为双向链接列表的节点，每个存储一个元素。  
  
 在下面的说明`GValue`等同于*值*后者是 ref 类型，除非在此情况下是`Value^`。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template<typename Value>  
    ref class list  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        Microsoft::VisualC::StlClr::IList<GValue>  
    { ..... };  
```  
  
### <a name="parameters"></a>参数  
 *值*  
 受控序列中的元素的类型。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/列表 >  
  
 **Namespace:** cliext 

## <a name="declarations"></a>声明  
  
|类型定义|描述|  
|---------------------|-----------------|  
|[list::const_iterator (STL/CLR)](#const_iterator)|受控序列的常量迭代器的类型。|  
|[list::const_reference (STL/CLR)](#const_reference)|元素的常量引用的类型。|  
|[list::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|受控序列的常量反向迭代器的类型。|  
|[list::difference_type (STL/CLR)](#difference_type)|两个元素间的带符号距离的类型。|  
|[list::generic_container (STL/CLR)](#generic_container)|泛型接口的容器的类型。|  
|[list::generic_iterator (STL/CLR)](#generic_iterator)|泛型接口的容器的迭代器的类型。|  
|[list::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型接口的反向迭代器的类型。|  
|[list::generic_value (STL/CLR)](#generic_value)|容器的泛型接口的元素的类型。|  
|[list::iterator (STL/CLR)](#iterator)|受控序列的迭代器的类型。|  
|[list::reference (STL/CLR)](#reference)|元素的引用的类型。|  
|[list::reverse_iterator (STL/CLR)](#reverse_iterator)|受控序列的反向迭代器的类型。|  
|[list::size_type (STL/CLR)](#size_type)|两个元素间的带符号距离的类型。|  
|[list::value_type (STL/CLR)](#value_type)|元素的类型。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[list::assign (STL/CLR)](#assign)|替换所有元素。|  
|[list::back (STL/CLR)](#back)|访问最后一个元素。|  
|[list::begin (STL/CLR)](#begin)|指定受控序列的开头。|  
|[list::clear (STL/CLR)](#clear)|删除所有元素。|  
|[list::empty (STL/CLR)](#empty)|测试元素是否存在。|  
|[list::end (STL/CLR)](#end)|指定受控序列的末尾。|  
|[list::erase (STL/CLR)](#erase)|移除指定位置处的元素。|  
|[list::front (STL/CLR)](#front)|访问第一个元素。|  
|[list::insert (STL/CLR)](#insert)|将元素添加的指定位置。|  
|[list::list (STL/CLR)](#list)|构造容器对象。|  
|[list::merge (STL/CLR)](#merge)|合并两个有序受控的序列。|  
|[list::pop_back (STL/CLR)](#pop_back)|删除最后一个元素。|  
|[list::pop_front (STL/CLR)](#pop_front)|删除第一个元素。|  
|[list::push_back (STL/CLR)](#push_back)|添加一个新的最后一个元素。|  
|[list::push_front (STL/CLR)](#push_front)|添加一个新的第一个元素。|  
|[list::rbegin (STL/CLR)](#rbegin)|指定反向受控序列的开头。|  
|[list::remove (STL/CLR)](#remove)|删除具有指定值的元素。|  
|[list::remove_if (STL/CLR)](#remove_if)|移除通过指定的测试的元素。|  
|[list::rend (STL/CLR)](#rend)|指定反向受控序列的末尾。|  
|[list::resize (STL/CLR)](#resize)|更改元素的数。|  
|[list::reverse (STL/CLR)](#reverse)|反转受控的序列。|  
|[list::size (STL/CLR)](#size)|对元素数进行计数。|  
|[list::sort (STL/CLR)](#sort)|受控的序列进行排序。|  
|[list::splice (STL/CLR)](#splice)|重新联结节点间的链接。|  
|[list::swap (STL/CLR)](#swap)|交换两个容器的内容。|  
|[list::to_array (STL/CLR)](#to_array)|将受控的序列复制到新数组。|  
|[list::unique (STL/CLR)](#unique)|删除通过了指定测试的相邻元素。|  
  
|属性|描述|  
|--------------|-----------------|  
|[list::back_item (STL/CLR)](#back_item)|访问最后一个元素。|  
|[list::front_item (STL/CLR)](#front_item)|访问第一个元素。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[list::operator= (STL/CLR)](#op_as)|替换受控序列。|  
|[operator!= (list) (STL/CLR)](#op_neq)|确定是否`list`对象不等于另一个`list`对象。|  
|[operator< (list) (STL/CLR)](#op_lt)|确定是否`list`对象是否小于另一个`list`对象。|  
|[operator<= (list) (STL/CLR)](#op_lteq)|确定是否`list`对象是否小于或等于另一个`list`对象。|  
|[operator== (list) (STL/CLR)](#op_eq)|确定是否`list`对象是否等于另一个`list`对象。|  
|[operator> (list) (STL/CLR)](#op_gt)|确定是否`list`对象是否大于另一个`list`对象。|  
|[operator>= (list) (STL/CLR)](#op_gteq)|确定是否`list`对象是否大于或等于另一个`list`对象。|  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|重复的对象。|  
|<xref:System.Collections.IEnumerable>|通过元素的序列。|  
|<xref:System.Collections.ICollection>|维护组元素。|  
|<xref:System.Collections.Generic.IEnumerable%601>|通过类型化的元素进行排序。|  
|<xref:System.Collections.Generic.ICollection%601>|维护的组类型化的元素。|  
|IList\<值 >|维护泛型容器。|  
  
## <a name="remarks"></a>备注  
 该对象分配并释放存储为双向链接列表中的单个节点其控制的序列。 它可以更改节点永远不会通过将一个节点的内容复制到另一个之间的链接，重新排列元素。 这意味着您可以插入和删除自由地不影响剩余元素的元素。 因此，列表是模板类的基础容器的良好候选项[队列 (STL/CLR)](../dotnet/queue-stl-clr.md)或模板类[堆栈 (STL/CLR)](../dotnet/stack-stl-clr.md)。  
  
 一个`list`对象支持双向迭代器，这意味着您可以单步到给定迭代器，指定受控序列中的元素的相邻元素。 特殊的头节点对应于返回的迭代器[list:: end (STL/CLR)](../dotnet/list-end-stl-clr.md)`()`。 如果存在，可以递减此迭代器，用于访问受控序列中的最后一个元素。 可递增访问头节点的列表迭代器，它将比较等于`end()`。 但不能取消引用返回的迭代器`end()`。  
  
 请注意，不能指直接给定其数字位置-需要随机访问迭代器的一个列表元素。 因此列表*不*作为基础容器模板类可用[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)。  
  
 列表迭代器，用于存储其关联的列表节点，后者又将存储的句柄关联的容器的句柄。 迭代器只能用于其关联的容器对象。 列表迭代器保持有效，只要其关联的列表节点是与某些列表相关联。 此外，有效的迭代器是现在--可以使用它来访问或更改，只要不等于此元素的值指定- `end()`。  
  
 擦除或删除元素调用析构函数为其存储的值。 销毁容器清除所有元素。 因此，其元素类型是 ref 类的容器可确保任何元素的生存期长于容器。 但请注意，容器的句柄 does*不*销毁它的元素。  
  
## <a name="members"></a>成员

## <a name="assign"></a> list:: assign (STL/CLR)
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
// cliext_list_assign.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// assign a repetition of values   
    cliext::list<wchar_t> c2;   
    c2.assign(6, L'x');   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign an iterator range   
    cliext::list<wchar_t>::iterator it = c1.end();   
    c2.assign(c1.begin(), --it);   
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
 
## <a name="back"></a> list:: back (STL/CLR)
访问最后一个元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
reference back();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回对受控序列，必须为非空的最后一个元素的引用。 用于访问的最后一个元素，当您知道它存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="back_item"></a> list::back_item (STL/CLR)
访问最后一个元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
property value_type back_item;  
```  
  
### <a name="remarks"></a>备注  
 属性访问，必须为非空的受控序列的最后一个元素。 您可以使用它来读取或写入的最后一个元素，当您知道它存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_back_item.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="begin"></a> list:: begin (STL/CLR)
指定受控序列的开头。  
  
### <a name="syntax"></a>语法  
  
```cpp  
iterator begin();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回指定第一个元素的受控序列，或刚超出空序列末尾的随机访问迭代器。 用于获取迭代器，指定`current`如果受控序列的长度发生更改，可以更改受控制的序列，但其状态的开头。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_begin.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::list<wchar_t>::iterator it = c1.begin();   
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

## <a name="clear"></a> list:: clear (STL/CLR)
删除所有元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void clear();  
```  
  
### <a name="remarks"></a>备注  
 成员函数有效地调用[list:: erase (STL/CLR)](../dotnet/list-erase-stl-clr.md) `(` [list:: begin (STL/CLR)](../dotnet/list-begin-stl-clr.md) `(),` [list:: end (STL/CLR)](../dotnet/list-end-stl-clr.md) `())`. 用于确保受控的序列为空。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_clear.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="const_iterator"></a> list:: const_iterator (STL/CLR)
受控序列的常量迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T2`可充当受控序列的常量随机访问迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_const_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::list<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a> list:: const_reference (STL/CLR)
元素的常量引用的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述的元素的常量引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_const_reference.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::list<wchar_t>::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        cliext::list<wchar_t>::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a> list:: const_reverse_iterator (STL/CLR)
受控序列的常量反向迭代器的类型...  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T4`可充当受控序列的常量反向迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::list<wchar_t>::const_reverse_iterator crit = c1.rbegin();   
    cliext::list<wchar_t>::const_reverse_iterator crend = c1.rend();   
    for (; crit != crend; ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="difference_type"></a> list:: difference_type (STL/CLR)
两个元素之间的带符号距离的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述已签名的元素计数。  
  
### <a name="example"></a>示例  
  
```cpp 
// cliext_list_difference_type.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::list<wchar_t>::difference_type diff = 0;   
    for (cliext::list<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it) ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (cliext::list<wchar_t>::iterator it = c1.end();   
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

## <a name="empty"></a> list:: empty (STL/CLR)
测试元素是否存在。  
  
### <a name="syntax"></a>语法  
  
```cpp  
bool empty();  
```  
  
### <a name="remarks"></a>备注  
 对于空受控序列，该成员函数返回 true。 它等效于[list:: size (STL/CLR)](../dotnet/list-size-stl-clr.md)`() == 0`。 用于测试是否列表为空。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_empty.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="end"></a> list:: end (STL/CLR)
指定受控序列的末尾。  
  
### <a name="syntax"></a>语法  
  
```cpp  
iterator end();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回一个随机访问迭代器，它指向刚超出受控序列的末尾。 用于获取指定受控序列; 的末尾的迭代器其状态不会更改如果受控序列的长度发生更改。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_end.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    cliext::list<wchar_t>::iterator it = c1.end();   
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

## <a name="erase"></a> list:: erase (STL/CLR)
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
  
 这两个成员函数返回一个迭代器，指定已删除的任何元素之外保留的第一个元素或[list:: end (STL/CLR)](../dotnet/list-end-stl-clr.md) `()`如果此类元素不存在。  
  
 如果清除元素，元素副本数呈线性之间的清除结束和邻近序列末尾的元素数目。 （时清除序列的任意一端的一个或多个元素，没有元素副本发生。）  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_erase.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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
    cliext::list<wchar_t>::iterator it = c1.end();   
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

## <a name="front"></a> list:: front (STL/CLR)
访问第一个元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
reference front();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回对受控序列，必须为非空的第一个元素的引用。 您可以使用它来读取或写入的第一个元素，当您知道它存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="front_item"></a> list::front_item (STL/CLR)
访问第一个元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
property value_type front_item;  
```  
  
### <a name="remarks"></a>备注  
 属性访问，必须为非空的受控序列的第一个元素。 您可以使用它来读取或写入的第一个元素，当您知道它存在。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_front_item.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="generic_container"></a> list::generic_container (STL/CLR)
泛型接口的容器的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef Microsoft::VisualC::StlClr::  
    IList<generic_value>  
    generic_container;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述该类模板容器的泛型接口。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_generic_container.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
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

## <a name="generic_iterator"></a> list::generic_iterator (STL/CLR)
用于容器的泛型接口具有的迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerBidirectionalIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述可用于泛型接口为该类模板容器的泛型迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::list<wchar_t>::generic_value gcval = *gcit;   
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

## <a name="generic_reverse_iterator"></a> list::generic_reverse_iterator (STL/CLR)
一个反向迭代器用于与容器的泛型接口的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseBidirectionalIterator<generic_value> generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述可用于泛型接口为该类模板容器的泛型反向迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::list<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();   
    cliext::list<wchar_t>::generic_value gcval = *gcit;   
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

## <a name="generic_value"></a> list::generic_value (STL/CLR)
用于容器的泛型接口具有的元素的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述类型的对象`GValue`描述使用的存储的元素值与此模板容器类的泛型接口。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_generic_value.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    cliext::list<wchar_t>::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    cliext::list<wchar_t>::generic_iterator gcit = gc1->begin();   
    cliext::list<wchar_t>::generic_value gcval = *gcit;   
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

## <a name="insert"></a> list:: insert (STL/CLR)
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
// cliext_list_insert.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value using iterator   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",   
        *c1.insert(++it, L'x'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a repetition of values   
    cliext::list<wchar_t> c2;   
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
  
// insert a single value using index   
    it = c2.begin();   
    ++it, ++it, ++it;   
    c2.insert(it, L'z');   
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

## <a name="iterator"></a> list:: iterator (STL/CLR)
受控序列的迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T1`可充当受控序列的随机访问迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    cliext::list<wchar_t>::iterator it = c1.begin();   
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

## <a name="list"></a> list:: list (STL/CLR)
构造容器对象。  
  
### <a name="syntax"></a>语法  
  
```cpp  
list();  
list(list<Value>% right);  
list(list<Value>^ right);  
explicit list(size_type count);  
list(size_type count, value_type val);  
template<typename InIt>  
    list(InIt first, InIt last);  
list(System::Collections::Generic::IEnumerable<Value>^ right);  
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
  
 `list();`  
  
 初始化受控的序列不包含任何元素。 用于指定空的初始受控的序列。  
  
 构造函数：  
  
 `list(list<Value>% right);`  
  
 初始化受控的序列与序列 [`right.begin()`， `right.end()`)。 用于指定初始受控的序列的列表对象控制的序列的副本*右*。  
  
 构造函数：  
  
 `list(list<Value>^ right);`  
  
 初始化受控的序列与序列 [`right->begin()`， `right->end()`)。 用于指定初始受控的序列的列表对象的句柄是控制的序列的副本*右*。  
  
 构造函数：  
  
 `explicit list(size_type count);`  
  
 初始化具有的受控的序列*计数*每个值元素`value_type()`。 您使用它来填充容器元素与所有具有默认值。  
  
 构造函数：  
  
 `list(size_type count, value_type val);`  
  
 初始化具有的受控的序列*计数*每个值元素*val*。 您使用它来填充容器元素与所有具有相同的值。  
  
 构造函数：  
  
 `template<typename InIt>`  
  
 `list(InIt first, InIt last);`  
  
 初始化受控的序列与序列 [`first`， `last`)。 您可以使用它来使受控的序列的另一个序列副本。  
  
 构造函数：  
  
 `list(System::Collections::Generic::IEnumerable<Value>^ right);`  
  
 初始化具有指定枚举器的序列的受控的序列*右*。 您可以使用它来使受控的序列描述将枚举器的另一个序列的副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_construct.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container   
    cliext::list<wchar_t> c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// construct with a repetition of default values   
    cliext::list<wchar_t> c2(3);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", (int)elem);   
    System::Console::WriteLine();   
  
// construct with a repetition of values   
    cliext::list<wchar_t> c3(6, L'x');   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    cliext::list<wchar_t>::iterator it = c3.end();   
    cliext::list<wchar_t> c4(c3.begin(), --it);   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    cliext::list<wchar_t> c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    cliext::list<wchar_t> c7(c3);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    cliext::list<wchar_t> c8(%c3);   
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

## <a name="merge"></a> list:: merge (STL/CLR)
合并两个有序受控的序列。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void merge(list<Value>% right);  
template<typename Pred2>  
    void merge(list<Value>% right, Pred2 pred);  
```  
  
#### <a name="parameters"></a>参数  
 *Pred*  
 元素对的比较器。  
  
 *right*  
 若要在合并的容器。  
  
### <a name="remarks"></a>备注  
 第一个成员函数从控制的序列中移除所有元素*右*并将它们插入到受控序列中。 这两个序列必须按以前排序`operator<`-前进任一序列时，元素必须不能减少在值中。 所产生的序列还按`operator<`。 使用此成员函数要合并两个值中增加到一个序列，其中也会增加值中的序列。  
  
 第二个成员函数行为与第一个相同，不同之处在于按序列进行排序`pred`  --  `pred(X, Y)`必须为 false 的任何元素`X`遵循元素`Y`序列中。 您可以使用它来合并两个序列排序通过谓词函数或您指定的委托。  
  
 同时函数执行稳定合并--生成的受控序列中反向没有对原始受控序列中的元素。 此外，如果对元素`X`和`Y`生成的受控序列中具有等效顺序- `!(X < Y) && !(X < Y)` -从原始受控序列的元素在元素之前出现控制的序列从*右*。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_merge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
typedef cliext::list<wchar_t> Mylist;   
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'c');   
    c1.push_back(L'e');   
  
// display initial contents " a c e"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    cliext::list<wchar_t> c2;   
    c2.push_back(L'b');   
    c2.push_back(L'd');   
    c2.push_back(L'f');   
  
// display initial contents " b d f"   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// merge and display   
    cliext::list<wchar_t> c3(c1);   
    c3.merge(c2);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
  
// sort descending, merge descending, and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    c3.merge(c1, cliext::greater<wchar_t>());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    return (0);   
    }  
```  
  
```Output  
 a c e  
 b d f  
 a b c d e f  
c2.size() = 0  
 e c a  
 f e d c b a  
 f e e d c c b a a  
c1.size() = 0  
```  

## <a name="op_as"></a> list::operator = (STL/CLR)
替换受控序列。  
  
### <a name="syntax"></a>语法  
  
```  
list<Value>% operator=(list<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *right*  
 用于复制的容器。  
  
### <a name="remarks"></a>备注  
 成员运算符副本*右*对象，然后返回`*this`。 用于替换受控的序列中的受控序列的副本*右*。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_operator_as.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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

## <a name="pop_back"></a> list:: pop_back (STL/CLR)
删除最后一个元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void pop_back();  
```  
  
### <a name="remarks"></a>备注  
 成员函数删除必须为非空的受控序列的最后一个元素。 您可以使用它来缩短在后一个元素的列表。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_pop_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="pop_front"></a> list:: pop_front (STL/CLR)
删除第一个元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void pop_front();  
```  
  
### <a name="remarks"></a>备注  
 成员函数删除必须为非空的受控序列的第一个元素。 用于缩短通过前面的一个元素的列表。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_pop_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// pop an element and redisplay   
    c1.pop_front();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
b c  
```  

## <a name="push_back"></a> list:: push_back (STL/CLR)
添加一个新的最后一个元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void push_back(value_type val);  
```  
  
### <a name="remarks"></a>备注  
 成员函数将具有值的元素插入`val`受控序列的末尾。 用于将另一个元素追加到列表。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_push_back.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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
  
## <a name="push_front"></a> list:: push_front (STL/CLR)
添加一个新的第一个元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void push_front(value_type val);  
```  
  
### <a name="remarks"></a>备注  
 成员函数将具有值的元素插入`val`受控序列开头位置。 使用在前面附加到列表的另一个元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_push_front.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_front(L'a');   
    c1.push_front(L'b');   
    c1.push_front(L'c');   
  
// display contents " c b a"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
c b a  
```  

## <a name="rbegin"></a> list:: rbegin (STL/CLR)
指定反向受控序列的开头。  
  
### <a name="syntax"></a>语法  
  
```cpp  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回一个反向迭代器，指定受控序列，或刚超出空序列的开头的最后一个元素。 因此，它指定`beginning`反向序列。 用于获取迭代器，指定`current`如果受控序列的长度发生更改，可以更改的相反顺序的受控的序列，但其状态开始。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_rbegin.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();   
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

## <a name="reference"></a> list:: reference (STL/CLR)
元素的引用的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述的元素的引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_reference.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    cliext::list<wchar_t>::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::list<wchar_t>::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
  
// modify contents " a b c"   
    for (it = c1.begin(); it != c1.end(); ++it)   
        {   // get a reference to an element   
        cliext::list<wchar_t>::reference ref = *it;   
  
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

## <a name="remove"></a> list:: remove (STL/CLR)
删除具有指定值的元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void remove(value_type val);  
```  
  
#### <a name="parameters"></a>参数  
 *val*  
 要移除的元素的值。  
  
### <a name="remarks"></a>备注  
 成员函数为其受控序列中移除一个元素`((System::Object^)val)->Equals((System::Object^)x)`（如果有） 也是如此。 使用要清除具有指定值的任意元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_remove.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// fail to remove and redisplay   
    c1.remove(L'A');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();  
  
// remove and redisplay   
    c1.remove(L'b');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
a b c  
a c  
```  

## <a name="remove_if"></a> list:: remove_if (STL/CLR)
移除通过指定的测试的元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
template<typename Pred1>  
    void remove_if(Pred1 pred);  
```  
  
#### <a name="parameters"></a>参数  
 *Pred*  
 要移除元素的测试。  
  
### <a name="remarks"></a>备注  
 成员函数从受控序列 （擦除） 中的每个元素`X`为其`pred(X)`为 true。 用于删除满足条件的函数或委托为指定的所有元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_remove_if.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'b');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b b b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// fail to remove and redisplay   
    c1.remove_if(cliext::binder2nd<cliext::equal_to<wchar_t> >(   
        cliext::equal_to<wchar_t>(), L'd'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// remove and redisplay   
    c1.remove_if(cliext::binder2nd<cliext::not_equal_to<wchar_t> >(   
        cliext::not_equal_to<wchar_t>(), L'b'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b b b c  
a b b b c  
b b b  
``` 

## <a name="rend"></a> list:: rend (STL/CLR)
指定反向受控序列的末尾。  
  
### <a name="syntax"></a>语法  
  
```cpp  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回一个反向迭代器指向刚超出开头的受控序列。 因此，它指定`end`反向序列。 用于获取迭代器，指定`current`如果受控序列的长度发生更改，可以更改的相反顺序的受控的序列，但其状态结束。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_rend.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rend();   
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

## <a name="resize"></a> list:: resize (STL/CLR)
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
 这两个成员函数，请确保[list:: size (STL/CLR)](../dotnet/list-size-stl-clr.md) `()`此后返回*new_size*。 如果它必须使受控的序列更长，第一个成员函数追加具有值的元素`value_type()`，而第二个成员函数追加具有值的元素*val*。 若要使受控的序列更短，这两个成员函数有效地清除的最后一个元素[list:: size (STL/CLR)](../dotnet/list-size-stl-clr.md) `() -` `new_size`时间。 用于确保受控的序列的大小*new_size*、 修整或填充当前的受控的序列。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_resize.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
// construct an empty container and pad with default values   
    cliext::list<wchar_t> c1;   
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

## <a name="reverse"></a> list:: reverse (STL/CLR)
反转受控的序列。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void reverse();  
```  
  
### <a name="remarks"></a>备注  
 成员函数反转受控序列中的所有元素的顺序。 您可以使用它以反映元素的列表。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_reverse.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// reverse and redisplay   
    c1.reverse();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
c b a  
```  

## <a name="reverse_iterator"></a> list:: reverse_iterator (STL/CLR)
受控序列的反向迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述了可充当受控序列的反向迭代器的未指定类型 `T3` 的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" reversed   
    cliext::list<wchar_t>::reverse_iterator rit = c1.rbegin();   
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
  
## <a name="size"></a> list:: size (STL/CLR)
对元素数进行计数。  
  
### <a name="syntax"></a>语法  
  
```cpp  
size_type size();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回受控序列的长度。 用于确定受控序列中当前元素的数目。 如果您关心的只是该序列是否具有非零大小，请参阅[list:: empty (STL/CLR)](../dotnet/list-empty-stl-clr.md)`()`。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_size.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="size_type"></a> list:: size_type (STL/CLR)
两个元素间的带符号距离的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef int size_type;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述非负元素计数。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_size_type.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    cliext::list<wchar_t>::size_type diff = 0;   
    for (cliext::list<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```

## <a name="sort"></a> list:: sort (STL/CLR)
受控的序列进行排序。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void sort();  
template<typename Pred2>  
    void sort(Pred2 pred);  
```  
  
#### <a name="parameters"></a>参数  
 *Pred*  
 元素对的比较器。  
  
### <a name="remarks"></a>备注  
 第一个成员函数重新排列受控序列中的元素，以便按排序`operator<`-值中不要递减元素，当正在进行的序列。 使用此成员函数进行排序以递增顺序序列。  
  
 第二个成员函数行为与第一个相同，不同之处在于该序列进行排序`pred`  --  `pred(X, Y)`为 false 的任何元素`X`遵循元素`Y`结果序列中。 用于对通过谓词函数或委托指定的顺序序列进行排序。  
  
 同时函数执行一个稳定排序--生成的受控序列中反向没有对原始受控序列中的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_sort.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort descending and redisplay   
    c1.sort(cliext::greater<wchar_t>());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// sort ascending and redisplay   
    c1.sort();   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
c b a  
a b c  
``` 

## <a name="splice"></a> list:: splice (STL/CLR)
Restitch 节点之间的链接。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void splice(iterator where, list<Value>% right);  
void splice(iterator where, list<Value>% right,  
    iterator first);  
void splice(iterator where, list<Value>% right,  
    iterator first, iterator last);  
```  
  
#### <a name="parameters"></a>参数  
 *first*  
 要拼接的范围的起始处。  
  
 *最后一个*  
 要拼接的范围的下限。  
  
 *right*  
 要从中进行拼接的容器。  
  
 *where*  
 要拼接之前的容器中的位置。  
  
### <a name="remarks"></a>备注  
 第一个成员函数插入控制的序列*右*指向受控序列中的元素之前*其中*。 它还会删除中的所有元素*右*。 (`%right`不能等于`this`。)使用要拼接到另一个列表的所有。  
  
 第二个成员函数删除由指向的元素*第一个*控制的序列中*右*并将其指向受控序列中的元素之前插入*其中*. (如果`where` `==` `first` `||` `where` `== ++first`，不会发生更改。)使用要拼接到另一个列表的单个元素。  
  
 第三个成员函数插入由指定的子范围 [`first`， `last`) 控制的序列从*右*指向的受控序列中的元素之前*其中*. 它还将删除原始子范围控制的序列*右*。 (如果`right` `==` `this`，在范围 [`first`， `last`) 不能包含元素由指向*其中*。)使用要拼接到另一个列表中的零个或多个元素的子序列。  
  
### <a name="example"></a>示例  
  
```cpp
// cliext_list_splice.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// splice to a new list   
    cliext::list<wchar_t> c2;   
    c2.splice(c2.begin(), c1);   
    System::Console::WriteLine("c1.size() = {0}", c1.size());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return one element   
    c1.splice(c1.end(), c2, c2.begin());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// return remaining elements   
    c1.splice(c1.begin(), c2, c2.begin(), c2.end());   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("c2.size() = {0}", c2.size());   
    return (0);   
    }  
```  
  
```Output  
 a b c  
c1.size() = 0  
 a b c  
 a  
 b c  
 b c a  
c2.size() = 0  
```    

## <a name="swap"></a> list:: swap (STL/CLR)
交换两个容器的内容。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void swap(list<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *right*  
 要与其交换内容的容器。  
  
### <a name="remarks"></a>备注  
 成员函数交换之间的受控的序列`*this`并*右*。 它是在常量时间内，则会引发任何异常。 您将其用作一种来交换两个容器的内容的快速方法。  
  
### <a name="example"></a>示例  
  
```cpp 
// cliext_list_swap.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    cliext::list<wchar_t> c2(5, L'x');   
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

## <a name="to_array"></a> list::to_array (STL/CLR)
将受控的序列复制到新数组。  
  
### <a name="syntax"></a>语法  
  
```cpp  
cli::array<Value>^ to_array();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回一个数组，包含对受控的序列。 用于获取数组形式的受控序列的副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_to_array.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
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

## <a name="unique"></a> list:: unique (STL/CLR)
删除通过了指定测试的相邻元素。  
  
### <a name="syntax"></a>语法  
  
```cpp  
void unique();  
template<typename Pred2>  
    void unique(Pred2 pred);  
```  
  
#### <a name="parameters"></a>参数  
 *Pred*  
 元素对的比较器。  
  
### <a name="remarks"></a>备注  
 第一个成员函数从受控序列 （擦除） 删除比较每个元素等于其前一个元素-如果元素`X`位于元素`Y`并`X == Y`，成员函数删除`Y`。 用于删除所有只保留一个副本的每个的相邻元素的子序列的相等。 请注意，如果受控的序列进行排序，例如通过调用[list:: sort (STL/CLR)](../dotnet/list-sort-stl-clr.md)`()`，成员函数具有唯一值将保留仅有的元素。 （由此而得名）。  
  
 第二个成员函数行为与第一个相同，不同之处在于它会删除每个元素`Y`遵循元素`X`为其`pred(X, Y)`。 用于删除的每个满足谓词函数或您指定的委托的相邻元素的子序列的所有只保留一个副本。 请注意，如果受控的序列进行排序，例如通过调用`sort(pred)`，成员函数将保留不具有等效顺序的所有其他元素的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_unique.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display initial contents " a a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique   
    cliext::list<wchar_t> c2(c1);   
    c2.unique();   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display contents after unique(not_equal_to)   
    c2 = c1;   
    c2.unique(cliext::not_equal_to<wchar_t>());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a a b c  
a b c  
a a  
```  

## <a name="value_type"></a> list:: value_type (STL/CLR)
元素的类型。  
  
### <a name="syntax"></a>语法  
  
```cpp  
typedef Value value_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数的同义词*值*。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_value_type.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c" using value_type   
    for (cliext::list<wchar_t>::iterator it = c1.begin();   
        it != c1.end(); ++it)   
        {   // store element in value_type object   
        cliext::list<wchar_t>::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
```  
  
```Output  
a b c  
``` 

## <a name="op_neq"></a> 运算符 ！ = （列表） (STL/CLR)
列出不等于比较。  
  
### <a name="syntax"></a>语法  
  
```cpp  
template<typename Value>  
    bool operator!=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *left*  
 要比较的左容器。  
  
 *right*  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`!(left == right)`。 使用它来测试是否*左*未排序相同*右*当两个列表都比较的元素的方式。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_operator_ne.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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

## <a name="op_lt"></a> 运算符&lt;（列表） (STL/CLR)
列表小于比较。  
  
### <a name="syntax"></a>语法  
  
```cpp  
template<typename Value>  
    bool operator<(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *left*  
 要比较的左容器。  
  
 *right*  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数返回 true 当对于最低的位置`i`为其`!(right[i] < left[i])`它是还 true 的`left[i] < right[i]`。 否则，它将返回`left->size() < right->size()`使用它来测试是否*左*进行排序之前*右*当两个列表都比较的元素的方式。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_operator_lt.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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

## <a name="op_lteq"></a> 运算符&lt;= （列表） (STL/CLR)
列表小于或等于比较。  
  
### <a name="syntax"></a>语法  
  
```cpp  
template<typename Value>  
    bool operator<=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *left*  
 要比较的左容器。  
  
 *right*  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数返回`!(right < left)`。 使用它来测试是否*左*未排序后*右*当两个列表都比较的元素的方式。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_operator_le.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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

## <a name="op_eq"></a> 运算符 = = （列表） (STL/CLR)
列表相等比较。  
  
### <a name="syntax"></a>语法  
  
```cpp 
template<typename Value>  
    bool operator==(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *left*  
 要比较的左容器。  
  
 *right*  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数才返回 true，序列由控制*左*并*右*具有相同的长度和每个位置`i`， `left[i] ==` `right[i]`。 使用它来测试是否*左*进行排序相同*右*当两个列表都比较的元素的方式。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_operator_eq.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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

## <a name="op_gt"></a> 运算符&gt;（列表） (STL/CLR)
大于比较的列表。  
  
### <a name="syntax"></a>语法  
  
```cpp  
template<typename Value>  
    bool operator>(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *left*  
 要比较的左容器。  
  
 *right*  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数将返回`right` `<` `left`。 使用它来测试是否*左*进行排序后*右*当两个列表都比较的元素的方式。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_operator_gt.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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

## <a name="op_gteq"></a> 运算符&gt;= （列表） (STL/CLR)
列表大于或等于比较。  
  
### <a name="syntax"></a>语法  
  
```cpp  
template<typename Value>  
    bool operator>=(list<Value>% left,  
        list<Value>% right);  
```  
  
#### <a name="parameters"></a>参数  
 *left*  
 要比较的左容器。  
  
 *right*  
 要比较的右容器。  
  
### <a name="remarks"></a>备注  
 运算符函数将返回`!(left` `<` `right)`。 使用它来测试是否*左*未排序之前*右*当两个列表都比较的元素的方式。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_list_operator_ge.cpp   
// compile with: /clr   
#include <cliext/list>   
  
int main()   
    {   
    cliext::list<wchar_t> c1;   
    c1.push_back(L'a');   
    c1.push_back(L'b');   
    c1.push_back(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    cliext::list<wchar_t> c2;   
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