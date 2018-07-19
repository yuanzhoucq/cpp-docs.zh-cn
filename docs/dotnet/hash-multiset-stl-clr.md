---
title: hash_multiset (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_multiset
- cliext::hash_multiset::begin
- cliext::hash_multiset::bucket_count
- cliext::hash_multiset::clear
- cliext::hash_multiset::const_iterator
- cliext::hash_multiset::const_reference
- cliext::hash_multiset::const_reverse_iterator
- cliext::hash_multiset::count
- cliext::hash_multiset::difference_type
- cliext::hash_multiset::empty
- cliext::hash_multiset::end
- cliext::hash_multiset::equal_range
- cliext::hash_multiset::erase
- cliext::hash_multiset::find
- cliext::hash_multiset::generic_container
- cliext::hash_multiset::generic_iterator
- cliext::hash_multiset::generic_reverse_iterator
- cliext::hash_multiset::generic_value
- cliext::hash_multiset::hash_delegate
- cliext::hash_multiset::hash_multiset
- cliext::hash_multiset::hasher
- cliext::hash_multiset::insert
- cliext::hash_multiset::iterator
- cliext::hash_multiset::key_comp
- cliext::hash_multiset::key_compare
- cliext::hash_multiset::key_type
- cliext::hash_multiset::load_factor
- cliext::hash_multiset::lower_bound
- cliext::hash_multiset::make_value
- cliext::hash_multiset::max_load_factor
- cliext::hash_multiset::operator=
- cliext::hash_multiset::rbegin
- cliext::hash_multiset::reference
- cliext::hash_multiset::rehash
- cliext::hash_multiset::rend
- cliext::hash_multiset::reverse_iterator
- cliext::hash_multiset::size
- cliext::hash_multiset::size_type
- cliext::hash_multiset::swap
- cliext::hash_multiset::to_array
- cliext::hash_multiset::upper_bound
- cliext::hash_multiset::value_comp
- cliext::hash_multiset::value_compare
- cliext::hash_multiset::value_type
dev_langs:
- C++
helpviewer_keywords:
- <cliext/hash_set> header [STL/CLR]
- hash_multiset class [STL/CLR]
- <hash_set> header [STL/CLR]
- begin member [STL/CLR]
- bucket_count member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- hash_delegate member [STL/CLR]
- hash_multiset member [STL/CLR]
- hasher member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- load_factor member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- max_load_factor member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rehash member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 8462bd21-6829-4dd3-ac81-c42d6fdf92f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3e5db2aafb10ad6d95fe50d073085041a1016cac
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2018
ms.locfileid: "37079859"
---
# <a name="hashmultiset-stlclr"></a>hash_multiset (STL/CLR)
此模板类描述控制变长序列的元素具有双向访问的对象。 使用容器`hash_multiset`若要管理的元素序列作为哈希表，每个表项存储双向链接列表的节点，并存储一个元素，每个节点。 每个元素的值用作一个键，以进行排序序列。  
  
 在下面，描述`GValue`相同`GKey`，这反过来是相同`Key`后者为 ref 类型，除非在这种情况下很`Key^`。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Key>  
    ref class hash_multiset  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>  
    { ..... };  
```  
  
### <a name="parameters"></a>参数  
 键  
 受控序列中的元素的关键组件的类型。  

## <a name="requirements"></a>要求  
 **标头：** \<cliext/hash_set >  
  
 **Namespace:** cliext  
  
## <a name="declarations"></a>声明  
  
|类型定义|描述|  
|---------------------|-----------------|  
|[hash_multiset::const_iterator (STL/CLR)](#const_iterator)|受控序列的常量迭代器的类型。|  
|[hash_multiset::const_reference (STL/CLR)](#const_reference)|元素的常量引用的类型。|  
|[hash_multiset::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|受控序列的常量反向迭代器的类型。|  
|[hash_multiset::difference_type (STL/CLR)](#difference_type)|两个元素间的 （可能是带符号） 距离的类型。|  
|[hash_multiset::generic_container (STL/CLR)](#generic_container)|容器的泛型接口的类型。|  
|[hash_multiset::generic_iterator (STL/CLR)](#generic_iterator)|容器的泛型接口的迭代器类型。|  
|[hash_multiset::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型接口的反向迭代器的类型。|  
|[hash_multiset::generic_value (STL/CLR)](#generic_value)|容器的泛型接口的元素的类型。|  
|[hash_multiset::hasher (STL/CLR)](#hasher)|用于密钥的哈希委托。|  
|[hash_multiset::iterator (STL/CLR)](#iterator)|受控序列的迭代器的类型。|  
|[hash_multiset::key_compare (STL/CLR)](#key_compare)|两个键的排序的委托。|  
|[hash_multiset::key_type (STL/CLR)](#key_type)|排序键的类型。|  
|[hash_multiset::reference (STL/CLR)](#reference)|元素的引用的类型。|  
|[hash_multiset::reverse_iterator (STL/CLR)](#reverse_iterator)|受控序列的反向迭代器的类型。|  
|[hash_multiset::size_type (STL/CLR)](#size_type)|两个元素间的 （非负号） 距离的类型。|  
|[hash_multiset::value_compare (STL/CLR)](#value_compare)|两个元素值排序委托。|  
|[hash_multiset::value_type (STL/CLR)](#value_type)|元素的类型。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[hash_multiset::begin (STL/CLR)](#begin)|指定受控序列的开头。|  
|[hash_multiset::bucket_count (STL/CLR)](#bucket_count)|对存储桶的数量进行计数。|  
|[hash_multiset::clear (STL/CLR)](#clear)|删除所有元素。|  
|[hash_multiset::count (STL/CLR)](#count)|对与指定的键匹配的元素计数。|  
|[hash_multiset::empty (STL/CLR)](#empty)|测试元素是否存在。|  
|[hash_multiset::end (STL/CLR)](#end)|指定受控序列的末尾。|  
|[hash_multiset::equal_range (STL/CLR)](#equal_range)|查找与指定键匹配的范围。|  
|[hash_multiset::erase (STL/CLR)](#erase)|移除指定位置处的元素。|  
|[hash_multiset::find (STL/CLR)](#find)|查找与指定键匹配的元素。|  
|[hash_multiset::hash_delegate (STL/CLR)](#hash_delegate)|将复制的键的哈希委托。|  
|[hash_multiset::hash_multiset (STL/CLR)](#hash_multiset)|构造容器对象。|  
|[hash_multiset::insert (STL/CLR)](#insert)|添加元素。|  
|[hash_multiset::key_comp (STL/CLR)](#key_comp)|将复制为两个键排序的委托。|  
|[hash_multiset::load_factor (STL/CLR)](#load_factor)|对每个存储桶的平均元素数进行计数。|  
|[hash_multiset::lower_bound (STL/CLR)](#lower_bound)|查找与指定的键匹配的范围开始处。|  
|[hash_multiset::make_value (STL/CLR)](#make_value)|构造值对象。|  
|[hash_multiset::max_load_factor (STL/CLR)](#max_load_factor)|获取或设置每个存储桶的最多元素数。|  
|[hash_multiset::rbegin (STL/CLR)](#rbegin)|指定反向受控序列的开头。|  
|[hash_multiset::rehash (STL/CLR)](#rehash)|重新生成哈希表。|  
|[hash_multiset::rend (STL/CLR)](#rend)|指定反向受控序列的末尾。|  
|[hash_multiset::size (STL/CLR)](#size)|对元素数进行计数。|  
|[hash_multiset::swap (STL/CLR)](#swap)|交换两个容器的内容。|  
|[hash_multiset::to_array (STL/CLR)](#to_array)|受控的序列复制到新数组。|  
|[hash_multiset::upper_bound (STL/CLR)](#upper_bound)|查找与指定的键匹配的范围末尾。|  
|[hash_multiset::value_comp (STL/CLR)](#value_comp)|将复制两个元素值的排序委托。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[hash_multiset::operator= (STL/CLR)](#op)|替换受控序列。|  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|复制对象。|  
|<xref:System.Collections.IEnumerable>|通过元素的序列。|  
|<xref:System.Collections.ICollection>|维护的组元素。|  
|<xref:System.Collections.Generic.IEnumerable%601>|访问类型化的元素序列。|  
|<xref:System.Collections.Generic.ICollection%601>|维护的组类型化的元素。|  
|IHash\<密钥，值 >|维护泛型容器。|  
  
## <a name="remarks"></a>备注  
 对象分配和释放存储在双向链接列表中的各个节点作为其控制的序列。 为了加快速度访问，该对象还维护有效地管理为的邻接，序列的整个列表的长短数组的指针到列表 （哈希表），或存储桶。 它会将元素插入到通过变更节点，永远不会通过将一个节点的内容复制到另一个之间的链接保持有序的存储桶中。 这意味着可以插入和移除自由不影响剩余元素的元素。  
  
 该对象进行排序它通过调用类型的存储的委托对象控制每个存储桶[hash_set:: key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md)。 在构造 hash_set; 时，可以指定存储的委托对象如果指定没有委托对象时，默认值是比较`operator<=(key_type, key_type)`。  
  
 通过调用成员函数来访问存储的委托对象[hash_set:: key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`。 此类委托对象必须定义键的类型之间的等效顺序[hash_set:: key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md)。 这意味着为任何两个键`X`和`Y`:  
  
 `key_comp()(X, Y)` 返回相同的布尔值导致每次调用。  
  
 如果`key_comp()(X, Y) && key_comp()(Y, X)`为 true，然后`X`和`Y`被认为具有等效顺序。  
  
 行为类似于任何排序规则`operator<=(key_type, key_type)`，`operator>=(key_type, key_type)`或`operator==(key_type, key_type)`定义 eqivalent 排序。  
  
 请注意，容器可确保仅元素键拥有等效顺序 （和为相同的整数值的哈希） 存储桶中相邻。 与模板类不同[hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)，模板类的对象`hash_multiset`不需要的所有元素的键是唯一。 （两个或多个密钥可以拥有等效顺序。）  
  
 对象确定哪个存储桶应通过调用类型的存储的委托对象包含给定的排序键[hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md)。 通过调用成员函数来访问此存储的对象[hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()`获取取决于密钥的值的整数值。 在构造 hash_set; 时，可以指定存储的委托对象如果指定没有委托对象时，默认值是函数`System::Object::hash_value(key_type)`。 这意味着，任何密钥`X`和`Y`:  
  
 `hash_delegate()(X)` 每次调用返回相同的整数结果。  
  
 如果`X`和`Y`拥有等效顺序，然后`hash_delegate()(X)`应返回与相同的整数结果`hash_delegate()(Y)`。  
  
 每个元素是用作键和值。 序列是允许查找、 插入和移除任意元素与大量的操作，在最佳情况下至少与序列 （常量时间）-中的元素数量无关的方式表示。 此外，插入元素不会使迭代器失效，移除元素仅会使指向已移除元素的迭代器失效。  
  
 如果哈希的值不均匀分布，但是，可以退化哈希表。 在极端情况下-始终返回相同的值-的哈希函数查找、 插入和删除是序列 （线性时间） 中的元素数量成正比。 容器致力于选择一个合理的哈希函数，平均存储桶大小，并且哈希表大小 （存储桶的总数量），但是你可以重写任何或所有这些选择。 请参阅，例如，函数[hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md)和[hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md)。  
  
 Hash_multiset 支持双向迭代器，这意味着你可以单步执行到给定指定受控序列中的元素的迭代器的相邻元素。 特殊的头节点对应于返回的迭代器[hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`。 如果存在，可以减少此迭代器来访问控制的序列中中的最后一个元素。 可以递增的 hash_multiset 迭代器来访问头节点，且然后将比较等于`end()`。 但不是能取消引用返回的迭代器`end()`。  
  
 请注意，不能引用到 hash_multiset 元素直接给定其数字位置-需要随机访问迭代器。  
  
 Hash_multiset 迭代器存储其关联的 hash_multiset 节点，后者反过来将存储到其关联的容器的句柄的句柄。 迭代器仅用于其关联的容器对象。 Hash_multiset 迭代器就保持有效的只要其关联的 hash_multiset 节点是与某些 hash_multiset 相关联。 此外，有效的迭代器是 dereferencable-可用来访问或更改元素值，它指定-，只要不等于`end()`。  
  
 擦除或删除元素调用析构函数作为其存储的值。 销毁容器清除所有元素。 因此，其元素类型是一个 ref 类的容器可确保任何元素生存期限超过容器。 但请注意，句柄的容器未`not`销毁它的元素。  
  
## <a name="members"></a>成员

## <a name="begin"></a> hash_multiset:: begin (STL/CLR)
指定受控序列的开头。  
  
### <a name="syntax"></a>语法  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回指定的受控序列，或刚超出空序列末尾的第一个元素的双向迭代器。 用于获取指定的迭代器`current`如果受控序列的长度发生更改，可以更改的受控的序列中，但其状态的开头。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_begin.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myhash_multiset::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = {0}", *it);   
    System::Console::WriteLine("*++begin() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*begin() = a  
*++begin() = b  
```  

## <a name="bucket_count"></a> hash_multiset::bucket_count (STL/CLR)
对存储桶的数量进行计数。  
  
### <a name="syntax"></a>语法  
  
```  
int bucket_count();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回存储桶的当前数量。 用于确定哈希表的大小。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_bucket_count.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 4  
  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 0.25  
  
bucket_count() = 128  
load_factor() = 0.0234375  
max_load_factor() = 0.25  
```  

## <a name="clear"></a> hash_multiset:: clear (STL/CLR)
删除所有元素。  
  
### <a name="syntax"></a>语法  
  
```  
void clear();  
```  
  
### <a name="remarks"></a>备注  
 成员函数可有效地调用[hash_multiset:: erase (STL/CLR)](../dotnet/hash-multiset-erase-stl-clr.md) `(` [hash_multiset:: begin (STL/CLR)](../dotnet/hash-multiset-begin-stl-clr.md) `(),` [hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`())`. 你可以使用它来确保受控的序列为空。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_clear.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
  
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

## <a name="const_iterator"></a> hash_multiset:: const_iterator (STL/CLR)
受控序列的常量迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T2`，可用作受控序列的常量的双向迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_const_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myhash_multiset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" {0}", *cit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reference"></a> hash_multiset:: const_reference (STL/CLR)
元素的常量引用的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述元素的常量引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_const_reference.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Myhash_multiset::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Myhash_multiset::const_reference cref = *cit;   
        System::Console::Write(" {0}", cref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="const_reverse_iterator"></a> hash_multiset:: const_reverse_iterator (STL/CLR)
受控序列的常量反向迭代器的类型...  
  
### <a name="syntax"></a>语法  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T4`，可用作受控序列的常量反向迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myhash_multiset::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" {0}", *crit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  

## <a name="count"></a> hash_multiset:: count (STL/CLR)
查找与指定键匹配的元素数。  
  
### <a name="syntax"></a>语法  
  
```  
size_type count(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
### <a name="remarks"></a>备注  
 成员函数返回拥有等效顺序与控制序列中的元素数目`key`。 你可以使用它来确定当前受控序列中与指定的键匹配的元素的数目。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_count.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
count(L'A') = 0  
count(L'b') = 1  
count(L'C') = 0  
```  
  
## <a name="difference_type"></a> hash_multiset:: difference_type (STL/CLR)
两个元素间的带符号距离的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述可能负元素计数。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_difference_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myhash_multiset::difference_type diff = 0;   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (Myhash_multiset::iterator it = c1.end(); it != c1.begin(); --it)   
        --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
begin()-end() = -3  
```  

## <a name="empty"></a> hash_multiset:: empty (STL/CLR)
测试元素是否存在。  
  
### <a name="syntax"></a>语法  
  
```  
bool empty();  
```  
  
### <a name="remarks"></a>备注  
 对于空受控序列，该成员函数返回 true。 它相当于[hash_multiset:: size (STL/CLR)](../dotnet/hash-multiset-size-stl-clr.md)`() == 0`。 用于测试是否 hash_multiset 为空。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_empty.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
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

## <a name="end"></a> hash_multiset:: end (STL/CLR)
指定受控序列的末尾。  
  
### <a name="syntax"></a>语法  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回的双向迭代器，它指向刚超出受控序列的末尾。 用于获取指定的受控序列中; 末尾的迭代器其状态不更改如果更改了受控序列的长度。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_end.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Myhash_multiset::iterator it = c1.end();   
    --it;   
    System::Console::WriteLine("*-- --end() = {0}", *--it);   
    System::Console::WriteLine("*--end() = {0}", *++it);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --end() = b  
*--end() = c  
```  
  
## <a name="equal_range"></a> hash_multiset:: equal_range (STL/CLR)
查找与指定键匹配的范围。  
  
### <a name="syntax"></a>语法  
  
```  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
### <a name="remarks"></a>备注  
 成员函数将返回一对迭代器`cliext::pair<iterator, iterator>(` [hash_multiset:: lower_bound (STL/CLR)](../dotnet/hash-multiset-lower-bound-stl-clr.md) `(key),` [hash_multiset:: upper_bound (STL/CLR)](../dotnet/hash-multiset-upper-bound-stl-clr.md)`(key))`。 你可以使用它来确定的受控序列中的当前与指定的键匹配的元素范围。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_equal_range.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
typedef Myhash_multiset::pair_iter_iter Pairii;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" {0}", *pair1.first);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
equal_range(L'x') empty = True  
 b  
```  

## <a name="erase"></a> hash_multiset:: erase (STL/CLR)
移除指定位置处的元素。  
  
### <a name="syntax"></a>语法  
  
```  
iterator erase(iterator where);  
iterator erase(iterator first, iterator last);  
bool erase(key_type key)  
```  
  
#### <a name="parameters"></a>参数  
 第一个  
 要清除范围的起点。  
  
 密钥  
 要擦除的密钥值。  
  
 last  
 要清除范围的末尾。  
  
 其中  
 要清除的元素。  
  
### <a name="remarks"></a>备注  
 第一个成员函数删除指向的受控序列的元素`where`，并返回指定已移除的元素之外保留的第一个元素的迭代器或[hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`如果此类元素不存在。 用于删除单个元素。  
  
 第二个成员函数范围中移除受控序列的元素 [`first`， `last`)，并返回指定已移除，任何元素之外保留的第一个元素的迭代器或`end()`如果没有此类元素存在... 用于删除零个或多个由连续的元素。  
  
 第三个成员函数删除其键具有等效顺序受控任何的序列元素到`key`，并返回已移除的元素数的计数。 你可以使用它删除，用来计数与指定的键匹配的所有元素。  
  
 每个元素擦除需要受控序列中的元素数的对数成正比的时间。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_erase.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    System::Console::WriteLine("erase(begin()) = {0}",   
        *c1.erase(c1.begin()));   
  
// add elements and display " b c d e"   
    c1.insert(L'd');   
    c1.insert(L'e');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// erase all but end   
    Myhash_multiset::iterator it = c1.end();   
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

## <a name="find"></a> hash_multiset:: find (STL/CLR)
查找与指定键匹配的元素。  
  
### <a name="syntax"></a>语法  
  
```  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
### <a name="remarks"></a>备注  
 如果受控序列中的至少一个元素具有等效顺序与`key`，成员函数将返回指定这些元素之一的迭代器; 否则它将返回[hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md) `()`. 用于定位指定的键相匹配的受控序列中当前的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_find.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
    System::Console::WriteLine("find {0} = {1}",   
        L'b', *c1.find(L'b'));   
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
find A = False  
find b = b  
find C = False  
``` 

## <a name="generic_container"></a> hash_multiset::generic_container (STL/CLR)
容器的泛型接口的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Microsoft::VisualC::StlClr::  
    IHash<GKey, GValue>  
    generic_container;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述此模板容器类的泛型接口。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_generic_container.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(L'd');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.insert(L'e');   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
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
   
## <a name="generic_iterator"></a> hash_multiset::generic_iterator (STL/CLR)
与容器的泛型接口使用的迭代器类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ContainerBidirectionalIterator<generic_value>  
    generic_iterator;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述此模板容器类可与泛型接口中使用的泛型迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_multiset::generic_iterator gcit = gc1->begin();   
    Myhash_multiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a  
```  

## <a name="generic_reverse_iterator"></a> hash_multiset::generic_reverse_iterator (STL/CLR)
反向迭代器用于与容器的泛型接口类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Microsoft::VisualC::StlClr::Generic::  
    ReverseRandomAccessIterator<generic_value>  
    generic_reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述一个泛型反向迭代器，此模板容器类可与泛型接口中使用。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_multiset::generic_reverse_iterator gcit = gc1->rbegin();   
    Myhash_multiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
c  
```  

## <a name="generic_value"></a> hash_multiset::generic_value (STL/CLR)
使用容器的泛型接口具有的元素的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述类型的对象`GValue`描述使用的存储的元素值与此模板容器类的泛型接口。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_generic_value.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_multiset::generic_container^ gc1 = %c1;   
    for each (wchar_t elem in gc1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_multiset::generic_iterator gcit = gc1->begin();   
    Myhash_multiset::generic_value gcval = *gcit;   
    System::Console::WriteLine(" {0}", gcval);   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
a  
```  
  
## <a name="hash_delegate"></a> hash_multiset::hash_delegate (STL/CLR)
查找与指定键匹配的元素。  
  
### <a name="syntax"></a>语法  
  
```  
hasher^ hash_delegate();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回该委托用于将密钥值转换为整数。 你可以使用它进行哈希键。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_hash_delegate.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
hash(L'a') = 1616896120  
hash(L'b') = 570892832  
```  
  
## <a name="hash_multiset"></a> hash_multiset:: hash_multiset (STL/CLR)
构造容器对象。  
  
### <a name="syntax"></a>语法  
  
```  
hash_multiset();  
explicit hash_multiset(key_compare^ pred);  
hash_multiset(key_compare^ pred, hasher^ hashfn);  
hash_multiset(hash_multiset<Key>% right);  
hash_multiset(hash_multiset<Key>^ right);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_multiset(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred, hasher^ hashfn);  
```  
  
#### <a name="parameters"></a>参数  
 第一个  
 要插入的范围开始处。  
  
 hashfn  
 哈希与存储桶的映射键的函数。  
  
 last  
 要插入的范围的末尾。  
  
 pred  
 排序受控序列的谓词。  
  
 右  
 要插入的对象或范围。  
  
### <a name="remarks"></a>备注  
 构造函数：  
  
 `hash_multiset();`  
  
 使用默认的排序谓词初始化受控的序列不包含任何元素， `key_compare()`，并使用默认哈希运算。 用于指定空的初始受控的序列，使用默认的排序谓词和哈希函数。  
  
 构造函数：  
  
 `explicit hash_multiset(key_compare^ pred);`  
  
 初始化受控的序列不包含任何元素，与排序的谓词`pred`，并使用默认哈希运算。 用于指定空的初始受控的序列，使用指定的排序谓词和默认哈希函数。  
  
 构造函数：  
  
 `hash_multiset(key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控的序列不包含任何元素，与排序的谓词`pred`，并使用哈希运算`hashfn`。 用于指定空的初始受控的序列，使用指定的排序谓词和哈希函数。  
  
 构造函数：  
  
 `hash_multiset(hash_multiset<Key>% right);`  
  
 初始化受控的序列与序列 [`right.begin()`， `right.end()`)、 排序谓词，默认值和默认哈希函数。 用于指定是由 hash_multiset 对象控制的序列的副本的初始受控的序列`right`、 与的默认排序谓词和哈希函数。  
  
 构造函数：  
  
 `hash_multiset(hash_multiset<Key>^ right);`  
  
 初始化受控的序列与序列 [`right->begin()`， `right->end()`)、 排序谓词，默认值和默认哈希函数。 用于指定是由 hash_multiset 对象控制的序列的副本的初始受控的序列`right`、 与的默认排序谓词和哈希函数。  
  
 构造函数：  
  
 `template<typename InIter> hash_multiset(InIter first, InIter last);`  
  
 初始化受控的序列与序列 [`first`， `last`)、 排序谓词，默认值和默认哈希函数。 你可以使用它以使用默认的排序谓词和哈希函数使受控的序列的另一个序列，副本。  
  
 构造函数：  
  
 `template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred);`  
  
 初始化受控的序列与序列 [`first`， `last`)，与排序的谓词`pred`，并使用默认哈希运算。 你可以使用它以使另一个序列，使用指定的排序谓词和默认哈希函数的副本的受控的序列。  
  
 构造函数：  
  
 `template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控的序列与序列 [`first`， `last`)，与排序的谓词`pred`，并使用哈希运算`hashfn`。 你可以使用它以使另一个序列，使用指定的排序谓词和哈希函数的副本的受控的序列。  
  
 构造函数：  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化与枚举器指定序列的受控的序列`right`、 排序谓词，默认值和默认哈希函数。 你可以使用它来使一个枚举器，使用默认的排序谓词和哈希函数所描述的另一个序列的副本的受控的序列。  
  
 构造函数：  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 初始化与枚举器指定序列的受控的序列`right`，与排序的谓词`pred`，并使用默认哈希运算。 你可以使用它以使所描述的枚举，使用指定排序谓词和默认哈希的函数的另一个序列的副本的受控的序列。  
  
 构造函数：  
  
 `hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 初始化与枚举器指定序列的受控的序列`right`，与排序的谓词`pred`，并使用哈希运算`hashfn`。 你可以使用它以使所描述的枚举，使用指定的排序谓词和哈希函数的另一个序列的副本的受控的序列。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_construct.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
// construct an empty container   
    Myhash_multiset c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_multiset c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_multiset c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multiset::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (wchar_t elem in c2h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_multiset c3(c1.begin(), c1.end());   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_multiset c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c4)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_multiset c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_multiset::hasher(&myfun));   
    for each (wchar_t elem in c4h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_multiset c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);   
    for each (wchar_t elem in c5)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_multiset c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>());   
    for each (wchar_t elem in c6)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_multiset c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,   
            cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_multiset::hasher(&myfun));   
    for each (wchar_t elem in c6h)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct from a generic container   
    Myhash_multiset c7(c4);   
    for each (wchar_t elem in c7)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_multiset c8(%c3);   
    for each (wchar_t elem in c8)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 a b c  
size() = 0  
 a b c  
size() = 0  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
 c b a  
  
 a b c  
 a b c  
```  

## <a name="hasher"></a> hash_multiset::hasher (STL/CLR)
用于密钥的哈希委托。  
  
### <a name="syntax"></a>语法  
  
```  
Microsoft::VisualC::StlClr::UnaryDelegate<GKey, int>  
    hasher;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述一个委托，可将密钥值转换为整数。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_hasher.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
hash(L'a') = 1616896120  
hash(L'b') = 570892832  
```  

## <a name="insert"></a> hash_multiset:: insert (STL/CLR)
添加元素。  
  
### <a name="syntax"></a>语法  
  
```  
iterator insert(value_type val);  
iterator insert(iterator where, value_type val);  
template<typename InIter>  
    void insert(InIter first, InIter last);  
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);  
```  
  
#### <a name="parameters"></a>参数  
 第一个  
 要插入的范围开始处。  
  
 last  
 要插入的范围的末尾。  
  
 右  
 要插入的枚举。  
  
 Val  
 要插入的密钥值。  
  
 其中  
 要插入 （仅提示） 的容器中的位置。  
  
### <a name="remarks"></a>备注  
 每个成员函数将插入剩余操作数指定的序列。  
  
 第一个成员函数将具有值的元素插入`val`，并返回一个迭代器，指定新插入的元素。 你可以使用它来插入单个元素。  
  
 第二个成员函数将具有值的元素插入`val`，使用`where`作为提示，（用于提高性能），并返回一个迭代器，指定新插入的元素。 你可以使用它来插入单个元素，这可能是靠近你知道的元素。  
  
 第三个成员函数将序列插入 [`first`， `last`)。 你可以使用它将从另一个序列复制的零个或多个元素。  
  
 第四个成员函数将由序列插入`right`。 用于插入一个枚举器所描述的序列。  
  
 每个元素插入受控序列中需要的元素数的对数成正比的时间。 插入可能发生在分期常量时间内，但是，给定一个提示，指示某个元素的插入点旁边。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_insert.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    System::Console::WriteLine("insert(L'x') = {0}",   
        *c1.insert(L'x'));   
  
    System::Console::WriteLine("insert(L'b') = {0}",   
        *c1.insert(L'b'));   
  
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    System::Console::WriteLine("insert(begin(), L'y') = {0}",   
        *c1.insert(c1.begin(), L'y'));   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Myhash_multiset c2;   
    Myhash_multiset::iterator it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (wchar_t elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myhash_multiset c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);   
    for each (wchar_t elem in c3)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
insert(L'x') = x  
insert(L'b') = b  
 a b b c x  
insert(begin(), L'y') = y  
 a b b c x y  
 a b b c x  
 a b b c x y  
```  

## <a name="iterator"></a> hash_multiset:: iterator (STL/CLR)
受控序列的迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T1`，可用作受控序列的双向迭代器。  
  
### <a name="example"></a>示例  
  
```cpp 
// cliext_hash_multiset_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    Myhash_multiset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" {0}", *it);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="key_comp"></a> hash_multiset:: key_comp (STL/CLR)
将复制为两个键排序的委托。  
  
### <a name="syntax"></a>语法  
  
```  
key_compare^key_comp();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回使用受控的序列进行排序的排序委托。 用于比较两个键。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_key_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_multiset c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="key_compare"></a> hash_multiset:: key_compare (STL/CLR)
两个键的排序的委托。  
  
### <a name="syntax"></a>语法  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>  
    key_compare;  
```  
  
### <a name="remarks"></a>备注  
 类型为委托来决定其密钥的自变量的顺序的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_key_compare.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_multiset c2 = cliext::greater<wchar_t>();   
    kcomp = c2.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
  
compare(L'a', L'a') = False  
compare(L'a', L'b') = False  
compare(L'b', L'a') = True  
```  

## <a name="key_type"></a> hash_multiset:: key_type (STL/CLR)
排序键的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Key` 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_key_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using key_type   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Myhash_multiset::key_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  

## <a name="load_factor"></a> hash_multiset::load_factor (STL/CLR)
对每个存储桶的平均元素数进行计数。  
  
### <a name="syntax"></a>语法  
  
```  
float load_factor();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回`(float)` [hash_multiset:: size (STL/CLR)](../dotnet/hash-multiset-size-stl-clr.md) `() /` [hash_multiset::bucket_count (STL/CLR)](../dotnet/hash-multiset-bucket-count-stl-clr.md)`()`。 你可以使用它来确定的平均存储桶大小。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_load_factor.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 4  
  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 0.25  
  
bucket_count() = 128  
load_factor() = 0.0234375  
max_load_factor() = 0.25  
```  

## <a name="lower_bound"></a> hash_multiset:: lower_bound (STL/CLR)
查找与指定的键匹配的范围开始处。  
  
### <a name="syntax"></a>语法  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
### <a name="remarks"></a>备注  
 成员函数将确定第一个元素`X`作为相同的存储桶进行哈希处理到受控序列中`key`和具有等效顺序到`key`。 如果此类元素不存在，它将返回[hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; 否则它将返回指定的迭代器`X`。 用于当前与指定的键匹配的控制序列中查找的元素序列的开头。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_lower_bound.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*lower_bound(L'a') = {0}",   
        *c1.lower_bound(L'a'));   
    System::Console::WriteLine("*lower_bound(L'b') = {0}",   
        *c1.lower_bound(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = a  
*lower_bound(L'b') = b  
```  

## <a name="make_value"></a> hash_multiset::make_value (STL/CLR)
构造值对象。  
  
### <a name="syntax"></a>语法  
  
```  
static value_type make_value(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要使用的密钥值。  
  
### <a name="remarks"></a>备注  
 成员函数将返回`value_type`对象，其键是`key`。 你可以使用它来编写适用于多个其他成员函数的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_make_value.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(Myhash_multiset::make_value(L'a'));   
    c1.insert(Myhash_multiset::make_value(L'b'));   
    c1.insert(Myhash_multiset::make_value(L'c'));   
  
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
  
## <a name="max_load_factor"></a> hash_multiset::max_load_factor (STL/CLR)
获取或设置每个存储桶的最多元素数。  
  
### <a name="syntax"></a>语法  
  
```  
float max_load_factor();  
void max_load_factor(float new_factor);  
```  
  
#### <a name="parameters"></a>参数  
 new_factor  
 新的最大加载因子来存储。  
  
### <a name="remarks"></a>备注  
 第一个成员函数返回当前存储的最大加载因子。 你可以使用它来确定的最大平均存储桶大小。  
  
 第二个成员函数将存储的最大加载因子的`new_factor`。 不自动 rehashing 发生之前的后续插入。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_max_load_factor.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 4  
  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 0.25  
  
bucket_count() = 128  
load_factor() = 0.0234375  
max_load_factor() = 0.25  
```  

## <a name="op"></a> hash_multiset::operator = (STL/CLR)
替换受控序列。  
  
### <a name="syntax"></a>语法  
  
```  
hash_multiset<Key>% operator=(hash_multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 用于复制的容器。  
  
### <a name="remarks"></a>备注  
 成员运算符副本`right`到对象，然后返回`*this`。 用它将受控序列替换为 `right` 中的受控序列的副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_operator_as.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myhash_multiset c2;   
    c2 = c1;   
// display contents " a b c"   
    for each (Myhash_multiset::value_type elem in c2)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
a b c  
```  

## <a name="rbegin"></a> hash_multiset:: rbegin (STL/CLR)
指定反向受控序列的开头。  
  
### <a name="syntax"></a>语法  
  
```  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回指定的受控序列，或刚超出空序列的开头的最后一个元素的反向迭代器。 因此，它指定`beginning`反向序列。 用于获取指定的迭代器`current`如果受控序列的长度发生更改，可以更改按逆序的受控的序列，但其状态的开头。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_rbegin.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Myhash_multiset::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = {0}", *rit);   
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*rbegin() = c  
*++rbegin() = b  
```  

## <a name="reference"></a> hash_multiset:: reference (STL/CLR)
元素的引用的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述元素的引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_reference.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    Myhash_multiset::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Myhash_multiset::reference ref = *it;   
        System::Console::Write(" {0}", ref);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
``` 

## <a name="rehash"></a> hash_multiset::rehash (STL/CLR)
重新生成哈希表。  
  
### <a name="syntax"></a>语法  
  
```  
void rehash();  
```  
  
### <a name="remarks"></a>备注  
 成员函数重新生成哈希表，从而确保[hash_multiset::load_factor (STL/CLR)](../dotnet/hash-multiset-load-factor-stl-clr.md) `() <=` [hash_multiset::max_load_factor (STL/CLR)](../dotnet/hash-multiset-max-load-factor-stl-clr.md)。 否则，哈希表的大小增加，仅在需要时后插入的操作。 （它永远不会自动的大小减小。）您可以使用它来调整哈希表的大小。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_rehash.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect current parameters   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// change max_load_factor and redisplay   
    c1.max_load_factor(0.25f);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    System::Console::WriteLine();   
  
// rehash and redisplay   
    c1.rehash(100);   
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());   
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());   
    System::Console::WriteLine("max_load_factor() = {0}",   
        c1.max_load_factor());   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 4  
  
bucket_count() = 16  
load_factor() = 0.1875  
max_load_factor() = 0.25  
  
bucket_count() = 128  
load_factor() = 0.0234375  
max_load_factor() = 0.25  
```  

## <a name="rend"></a> hash_multiset:: rend (STL/CLR)
指定反向受控序列的末尾。  
  
### <a name="syntax"></a>语法  
  
```  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回一个反向迭代器指向刚超出开头的受控序列。 因此，它指定`end`反向序列。 用于获取指定的迭代器`current`末尾按逆序的受控的序列，但其状态可以更改，如果更改了受控序列的长度。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_rend.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myhash_multiset::reverse_iterator rit = c1.rend();   
    --rit;   
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);   
    System::Console::WriteLine("*--rend() = {0}", *++rit);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
*-- --rend() = b  
*--rend() = a  
```  

## <a name="reverse_iterator"></a> hash_multiset:: reverse_iterator (STL/CLR)
受控序列的反向迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述了可充当受控序列的反向迭代器的未指定类型 `T3` 的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" reversed   
    Myhash_multiset::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" {0}", *rit);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
c b a  
```  

## <a name="size"></a> hash_multiset:: size (STL/CLR)
对元素数进行计数。  
  
### <a name="syntax"></a>语法  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回受控序列的长度。 用于确定当前受控序列中的元素的数目。 如果你关注的只是序列是否具有非零大小，请参阅[hash_multiset:: empty (STL/CLR)](../dotnet/hash-multiset-empty-stl-clr.md)`()`。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_size.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(L'a');   
    c1.insert(L'b');   
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

## <a name="size_type"></a> hash_multiset:: size_type (STL/CLR)
两个元素之间的带符号距离的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述非负元素计数。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_size_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myhash_multiset::size_type diff = 0;   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
end()-begin() = 3  
```

## <a name="swap"></a> hash_multiset:: swap (STL/CLR)
交换两个容器的内容。  
  
### <a name="syntax"></a>语法  
  
```  
void swap(hash_multiset<Key>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要与其交换内容的容器。  
  
### <a name="remarks"></a>备注  
 成员函数交换 `this` 和 `right`之间的受控序列。 它会以在常量时间内，则会引发任何异常。 你将它用作交换两个容器的内容的快速方法。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_swap.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Myhash_multiset c2;   
    c2.insert(L'd');   
    c2.insert(L'e');   
    c2.insert(L'f');   
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
d e f  
d e f  
a b c  
```    

## <a name="to_array"></a> hash_multiset::to_array (STL/CLR)
受控的序列复制到新数组。  
  
### <a name="syntax"></a>语法  
  
```  
cli::array<value_type>^ to_array();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回包含受控的序列的数组。 用于获取受控序列中数组形式的副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_to_array.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// copy the container and modify it   
    cli::array<wchar_t>^ a1 = c1.to_array();   
  
    c1.insert(L'd');   
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
  
## <a name="upper_bound"></a> hash_multiset:: upper_bound (STL/CLR)
查找与指定的键匹配的范围末尾。  
  
### <a name="syntax"></a>语法  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
### <a name="remarks"></a>备注  
 成员函数将确定最后一个元素`X`作为相同的存储桶进行哈希处理到受控序列中`key`和具有等效顺序到`key`。 如果此类元素不存在，或者`X`为受控序列中的最后一个元素，它将返回[hash_multiset:: end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; 否则它将返回指定以外的第一个元素的迭代器`X`. 用于当前与指定的键匹配的控制序列中查找的元素序列的末尾。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_upper_bound.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display initial contents " a b c"   
    for each (wchar_t elem in c1)   
        System::Console::Write(" {0}", elem);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    System::Console::WriteLine("*upper_bound(L'a') = {0}",   
        *c1.upper_bound(L'a'));   
    System::Console::WriteLine("*upper_bound(L'b') = {0}",   
        *c1.upper_bound(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
 a b c  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = b  
*upper_bound(L'b') = c  
```  

## <a name="value_comp"></a> hash_multiset:: value_comp (STL/CLR)
将复制两个元素值的排序委托。  
  
### <a name="syntax"></a>语法  
  
```  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回使用受控的序列进行排序的排序委托。 使用两个元素值进行比较。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_value_comp.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="value_compare"></a> hash_multiset:: value_compare (STL/CLR)
两个元素值排序委托。  
  
### <a name="syntax"></a>语法  
  
```  
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>  
    value_compare;  
```  
  
### <a name="remarks"></a>备注  
 该类型是确定其值自变量的顺序的委托的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_value_compare.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare(L'a', L'a') = True  
compare(L'a', L'b') = True  
compare(L'b', L'a') = False  
```  

## <a name="value_type"></a> hash_multiset:: value_type (STL/CLR)
元素的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef generic_value value_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是 `generic_value`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_multiset_value_type.cpp   
// compile with: /clr   
#include <cliext/hash_set>   
  
typedef cliext::hash_multiset<wchar_t> Myhash_multiset;   
int main()   
    {   
    Myhash_multiset c1;   
    c1.insert(L'a');   
    c1.insert(L'b');   
    c1.insert(L'c');   
  
// display contents " a b c" using value_type   
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Myhash_multiset::value_type val = *it;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
```  
