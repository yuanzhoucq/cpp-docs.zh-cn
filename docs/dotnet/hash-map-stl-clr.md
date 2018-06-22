---
title: hash_map (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::hash_map
- cliext::hash_map::begin
- cliext::hash_map::bucket_count
- cliext::hash_map::clear
- cliext::hash_map::const_iterator
- cliext::hash_map::const_reference
- cliext::hash_map::const_reverse_iterator
- cliext::hash_map::count
- cliext::hash_map::difference_type
- cliext::hash_map::empty
- cliext::hash_map::end
- cliext::hash_map::equal_range
- cliext::hash_map::erase
- cliext::hash_map::find
- cliext::hash_map::generic_container
- cliext::hash_map::generic_iterator
- cliext::hash_map::generic_reverse_iterator
- cliext::hash_map::generic_value
- cliext::hash_map::hash_delegate
- cliext::hash_map::hash_map
- cliext::hash_map::hasher
- cliext::hash_map::insert
- cliext::hash_map::iterator
- cliext::hash_map::key_comp
- cliext::hash_map::key_compare
- cliext::hash_map::key_type
- cliext::hash_map::load_factor
- cliext::hash_map::lower_bound
- cliext::hash_map::make_value
- cliext::hash_map::mapped_type
- cliext::hash_map::max_load_factor
- cliext::hash_map::operator=
- cliext::hash_map::operator
- cliext::hash_map::rbegin
- cliext::hash_map::reference
- cliext::hash_map::rehash
- cliext::hash_map::rend
- cliext::hash_map::reverse_iterator
- cliext::hash_map::size
- cliext::hash_map::size_type
- cliext::hash_map::swap
- cliext::hash_map::to_array
- cliext::hash_map::upper_bound
- cliext::hash_map::value_comp
- cliext::hash_map::value_compare
- cliext::hash_map::value_type
dev_langs:
- C++
helpviewer_keywords:
- <cliext/hash_map> header [STL/CLR]
- <hash_map> header [STL/CLR]
- hash_map class [STL/CLR]
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
- hash_map member [STL/CLR]
- hasher member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- load_factor member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- mapped_type member [STL/CLR]
- max_load_factor member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
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
ms.assetid: c3cfc69b-04c6-42ae-a30e-0eda953fe883
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9c42a1d546af7818d0eb9d3d97d395f74d5acccf
ms.sourcegitcommit: 301bb19056e5bae84ff50f7d1df1e546efe225ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/21/2018
ms.locfileid: "36305779"
---
# <a name="hashmap-stlclr"></a>hash_map (STL/CLR)
此模板类描述控制变长序列的元素具有双向访问的对象。 使用容器`hash_map`若要管理的元素序列作为哈希表，每个表项存储双向链接列表的节点，并存储一个元素，每个节点。 元素包含的密钥，以进行排序序列，并映射的值，其中会赶上。  
  
 在下面，描述`GValue`相同：  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 其中：  
  
 `GKey` 等同于`Key`后者为 ref 类型，除非在此情况下它是 `Key^`  
  
 `GMapped` 等同于`Mapped`后者为 ref 类型，除非在此情况下它是 `Mapped^`  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class hash_map  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        System::Collections::Generic::IDictionary<Gkey, GMapped>,  
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>  
    { ..... };  
```  
  
### <a name="parameters"></a>参数  
 Key  
 受控序列中的元素的关键组件的类型。  
  
 映射  
 受控序列中的元素的其他组件的类型。  

## <a name="requirements"></a>要求  
 **标头：** \<cliext/hash_map >  
  
 **Namespace:** cliext  

## <a name="declarations"></a>声明  
  
|类型定义|Description|  
|---------------------|-----------------|  
|[hash_map::const_iterator (STL/CLR)](#const_iterator)|受控序列的常量迭代器的类型。|  
|[hash_map::const_reference (STL/CLR)](#const_reference)|元素的常量引用的类型。|  
|[hash_map::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|受控序列的常量反向迭代器的类型。|  
|[hash_map::difference_type (STL/CLR)](#difference_type)|两个元素间的 （可能是带符号） 距离的类型。|  
|[hash_map::generic_container (STL/CLR)](#generic_container)|容器的泛型接口的类型。|  
|[hash_map::generic_iterator (STL/CLR)](#generic_iterator)|容器的泛型接口的迭代器类型。|  
|[hash_map::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|容器的泛型接口的反向迭代器的类型。|  
|[hash_map::generic_value (STL/CLR)](#generic_value)|容器的泛型接口的元素的类型。|  
|[hash_map::hasher (STL/CLR)](#hasher)|用于密钥的哈希委托。|  
|[hash_map::iterator (STL/CLR)](#iterator)|受控序列的迭代器的类型。|  
|[hash_map::key_compare (STL/CLR)](#key_compare)|两个键的排序的委托。|  
|[hash_map::key_type (STL/CLR)](#key_type)|排序键的类型。|  
|[hash_map::mapped_type (STL/CLR)](#mapped_type)|与每个键关联的映射值的类型。|  
|[hash_map::reference (STL/CLR)](#reference)|元素的引用的类型。|  
|[hash_map::reverse_iterator (STL/CLR)](#reverse_iterator)|受控序列的反向迭代器的类型。|  
|[hash_map::size_type (STL/CLR)](#size_type)|两个元素间的 （非负号） 距离的类型。|  
|[hash_map::value_compare (STL/CLR)](#value_compare)|两个元素值排序委托。|  
|[hash_map::value_type (STL/CLR)](#value_type)|元素的类型。|  
  
|成员函数|Description|  
|---------------------|-----------------|  
|[hash_map::begin (STL/CLR)](#begin)|指定受控序列的开头。|  
|[hash_map::bucket_count (STL/CLR)](#bucket_count)|对存储桶的数量进行计数。|  
|[hash_map::clear (STL/CLR)](#clear)|删除所有元素。|  
|[hash_map::count (STL/CLR)](#count)|对与指定的键匹配的元素计数。|  
|[hash_map::empty (STL/CLR)](#empty)|测试元素是否存在。|  
|[hash_map::end (STL/CLR)](#end)|指定受控序列的末尾。|  
|[hash_map::equal_range (STL/CLR)](#equal_range)|查找与指定键匹配的范围。|  
|[hash_map::erase (STL/CLR)](#erase)|移除指定位置处的元素。|  
|[hash_map::find (STL/CLR)](#find)|查找与指定键匹配的元素。|  
|[hash_map::hash_delegate (STL/CLR)](#hash_delegate)|将复制的键的哈希委托。|  
|[hash_map::hash_map (STL/CLR)](#hash_map)|构造容器对象。|  
|[hash_map::insert (STL/CLR)](#insert)|添加元素。|  
|[hash_map::key_comp (STL/CLR)](#key_comp)|将复制为两个键排序的委托。|  
|[hash_map::load_factor (STL/CLR)](#load_factor)|对每个存储桶的平均元素数进行计数。|  
|[hash_map::lower_bound (STL/CLR)](#lower_bound)|查找与指定的键匹配的范围开始处。|  
|[hash_map::make_value (STL/CLR)](#make_value)|构造值对象。|  
|[hash_map::max_load_factor (STL/CLR)](#max_load_factor)|获取或设置每个存储桶的最多元素数。|  
|[hash_map::rbegin (STL/CLR)](#rbegin)|指定反向受控序列的开头。|  
|[hash_map::rehash (STL/CLR)](#rehash)|重新生成哈希表。|  
|[hash_map::rend (STL/CLR)](#rend)|指定反向受控序列的末尾。|  
|[hash_map::size (STL/CLR)](#size)|对元素数进行计数。|  
|[hash_map::swap (STL/CLR)](#swap)|交换两个容器的内容。|  
|[hash_map::to_array (STL/CLR)](#to_array)|受控的序列复制到新数组。|  
|[hash_map::upper_bound (STL/CLR)](#upper_bound)|查找与指定的键匹配的范围末尾。|  
|[hash_map::value_comp (STL/CLR)](#value_comp)|将复制两个元素值的排序委托。|  
  
|运算符|Description|  
|--------------|-----------------|  
|[hash_map::operator= (STL/CLR)](#op_as)|替换受控序列。|  
|[hash_map::operator(STL/CLR)](#op)|将键映射到其关联的映射值。|  
  
## <a name="interfaces"></a>接口  
  
|接口|Description|  
|---------------|-----------------|  
|<xref:System.ICloneable>|复制对象。|  
|<xref:System.Collections.IEnumerable>|通过元素的序列。|  
|<xref:System.Collections.ICollection>|维护的组元素。|  
|<xref:System.Collections.Generic.IEnumerable%601>|访问类型化的元素序列。|  
|<xref:System.Collections.Generic.ICollection%601>|维护的组类型化的元素。|  
|<xref:System.Collections.Generic.IDictionary%602>|维护组 {键，值} 对。|  
|IHash < 键，值 >|维护泛型容器。|  
  
## <a name="remarks"></a>备注  
 对象分配和释放存储在双向链接列表中的各个节点作为其控制的序列。 为了加快速度访问，该对象还维护有效地管理为的邻接，序列的整个列表的长短数组的指针到列表 （哈希表），或存储桶。 它会将元素插入到通过变更节点，永远不会通过将一个节点的内容复制到另一个之间的链接保持有序的存储桶中。 这意味着可以插入和移除自由不影响剩余元素的元素。  
  
 该对象进行排序它通过调用类型的存储的委托对象控制每个存储桶[hash_set:: key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md)。 在构造 hash_set; 时，可以指定存储的委托对象如果指定没有委托对象时，默认值是比较`operator<=(key_type, key_type)`。  
  
 通过调用成员函数来访问存储的委托对象[hash_set:: key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`。 此类委托对象必须定义键的类型之间的等效顺序[hash_set:: key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md)。 这意味着为任何两个键`X`和`Y`:  
  
 `key_comp()(X, Y)` 返回相同的布尔值导致每次调用。  
  
 如果`key_comp()(X, Y) && key_comp()(Y, X)`为 true，然后`X`和`Y`被认为具有等效顺序。  
  
 行为类似于任何排序规则`operator<=(key_type, key_type)`，`operator>=(key_type, key_type)`或`operator==(key_type, key_type)`定义 eqivalent 排序。  
  
 请注意，容器可确保仅元素键拥有等效顺序 （和为相同的整数值的哈希） 存储桶中相邻。 与模板类不同[hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)，模板类的对象`hash_map`可确保密钥的所有元素都是唯一。 （任何两个密钥不具有等效顺序。）  
  
 对象确定哪个存储桶应通过调用类型的存储的委托对象包含给定的排序键[hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md)。 通过调用成员函数来访问此存储的对象[hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()`获取取决于密钥的值的整数值。 在构造 hash_set; 时，可以指定存储的委托对象如果指定没有委托对象时，默认值是函数`System::Object::hash_value(key_type)`。 这意味着，任何密钥`X`和`Y`:  
  
 `hash_delegate()(X)` 每次调用返回相同的整数结果。  
  
 如果`X`和`Y`拥有等效顺序，然后`hash_delegate()(X)`应返回与相同的整数结果`hash_delegate()(Y)`。  
  
 每个元素包含一个单独的键和映射的值。 序列是允许查找、 插入和移除任意元素与大量的操作，在最佳情况下至少与序列 （常量时间）-中的元素数量无关的方式表示。 此外，插入元素不会使迭代器失效，移除元素仅会使指向已移除元素的迭代器失效。  
  
 如果哈希的值不均匀分布，但是，可以退化哈希表。 在极端情况下-始终返回相同的值-的哈希函数查找、 插入和删除是序列 （线性时间） 中的元素数量成正比。 容器致力于选择一个合理的哈希函数，平均存储桶大小，并且哈希表大小 （存储桶的总数量），但是你可以重写任何或所有这些选择。 请参阅，例如，函数[hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md)和[hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md)。  
  
 Hash_map 支持双向迭代器，这意味着你可以单步执行到给定指定受控序列中的元素的迭代器的相邻元素。 特殊的头节点对应于返回的迭代器[hash_map:: end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`()`。 如果存在，可以减少此迭代器来访问控制的序列中中的最后一个元素。 可以递增的 hash_map 迭代器来访问头节点，且然后将比较等于`end()`。 但不是能取消引用返回的迭代器`end()`。  
  
 请注意，不能引用到 hash_map 元素直接给定其数字位置-需要随机访问迭代器。  
  
 Hash_map 迭代器存储其关联的 hash_map 节点，后者反过来将存储到其关联的容器的句柄的句柄。 迭代器仅用于其关联的容器对象。 只要其关联的 hash_map 节点是与某些 hash_map 相关联，hash_map 迭代器就保持有效。 此外，有效的迭代器是 dereferencable-可用来访问或更改元素值，它指定-，只要不等于`end()`。  
  
 擦除或删除元素调用析构函数作为其存储的值。 销毁容器清除所有元素。 因此，其元素类型是一个 ref 类的容器可确保任何元素生存期限超过容器。 但请注意，句柄的容器未`not`销毁它的元素。  
  
## <a name="members"></a>成员

## <a name="begin"></a> hash_map:: begin (STL/CLR)
指定受控序列的开头。  
  
### <a name="syntax"></a>语法  
  
```  
iterator begin();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回指定的受控序列，或刚超出空序列末尾的第一个元素的双向迭代器。 用于获取指定的迭代器`current`如果受控序列的长度发生更改，可以更改的受控的序列中，但其状态的开头。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_begin.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items   
    Myhash_map::iterator it = c1.begin();   
    System::Console::WriteLine("*begin() = [{0} {1}]",   
        it->first, it->second);   
    ++it;   
    System::Console::WriteLine("*++begin() = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*begin() = [a 1]  
*++begin() = [b 2]  
```  

## <a name="bucket_count"></a> hash_map::bucket_count (STL/CLR)
对存储桶的数量进行计数。  
  
### <a name="syntax"></a>语法  
  
```  
int bucket_count();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回存储桶的当前数量。 用于确定哈希表的大小。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_bucket_count.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1 = gcnew Myhash_map;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
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
 [a 1] [b 2] [c 3]  
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

## <a name="clear"></a> hash_map:: clear (STL/CLR)
删除所有元素。  
  
### <a name="syntax"></a>语法  
  
```  
void clear();  
```  
  
### <a name="remarks"></a>备注  
 成员函数可有效地调用[hash_map:: erase (STL/CLR)](../dotnet/hash-map-erase-stl-clr.md) `(` [hash_map:: begin (STL/CLR)](../dotnet/hash-map-begin-stl-clr.md) `(),` [hash_map:: end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`())`. 你可以使用它来确保受控的序列为空。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_clear.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
  
// display contents " [a 1] [b 2]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    c1.clear();   
    System::Console::WriteLine("size() = {0}", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 0  
 [a 1] [b 2]  
size() = 0  
```  
  
## <a name="const_iterator"></a> hash_map:: const_iterator (STL/CLR)
受控序列的常量迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef T2 const_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T2`，可用作受控序列的常量的双向迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_const_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Myhash_map::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        System::Console::Write(" [{0} {1}]", cit->first, cit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
``` 

## <a name="const_reference"></a> hash_map:: const_reference (STL/CLR)
元素的常量引用的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef value_type% const_reference;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述元素的常量引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_const_reference.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Myhash_map::const_iterator cit = c1.begin();   
    for (; cit != c1.end(); ++cit)   
        {   // get a const reference to an element   
        Myhash_map::const_reference cref = *cit;   
        System::Console::Write(" [{0} {1}]", cref->first, cref->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```   

## <a name="const_reverse_iterator"></a> hash_map:: const_reverse_iterator (STL/CLR)
受控序列的常量反向迭代器的类型...  
  
### <a name="syntax"></a>语法  
  
```  
typedef T4 const_reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T4`，可用作受控序列的常量反向迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_const_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Myhash_map::const_reverse_iterator crit = c1.rbegin();   
    for (; crit != c1.rend(); ++crit)   
        System::Console::Write(" [{0} {1}]", crit->first, crit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[c 3] [b 2] [a 1]  
```  
  
## <a name="count"></a> hash_map:: count (STL/CLR)
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
// cliext_hash_map_count.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));   
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));   
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
count(L'A') = 0  
count(L'b') = 1  
count(L'C') = 0  
``` 

## <a name="difference_type"></a> hash_map:: difference_type (STL/CLR)
两个元素间的带符号距离的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef int difference_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述可能负元素计数。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_difference_type.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myhash_map::difference_type diff = 0;   
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
  
// compute negative difference   
    diff = 0;   
    for (Myhash_map::iterator it = c1.end(); it != c1.begin(); --it)   
        --diff;   
    System::Console::WriteLine("begin()-end() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
end()-begin() = 3  
begin()-end() = -3  
```   

## <a name="empty"></a> hash_map:: empty (STL/CLR)
测试元素是否存在。  
  
### <a name="syntax"></a>语法  
  
```  
bool empty();  
```  
  
### <a name="remarks"></a>备注  
 对于空受控序列，该成员函数返回 true。 它相当于[hash_map:: size (STL/CLR)](../dotnet/hash-map-size-stl-clr.md)`() == 0`。 用于测试是否 hash_map 为空。  
  
### <a name="example"></a>示例  
  
```  
// cliext_hash_map_empty.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
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
 [a 1] [b 2] [c 3]  
size() = 3  
empty() = False  
size() = 0  
empty() = True  
```  
  
## <a name="end"></a> hash_map:: end (STL/CLR)
指定受控序列的末尾。  
  
### <a name="syntax"></a>语法  
  
```  
iterator end();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回的双向迭代器，它指向刚超出受控序列的末尾。 用于获取指定的受控序列中; 末尾的迭代器其状态不更改如果更改了受控序列的长度。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_end.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect last two items   
    Myhash_map::iterator it = c1.end();   
    --it;   
    --it;   
    System::Console::WriteLine("*-- --end() = [{0} {1}]",   
        it->first, it->second);   
    ++it;   
    System::Console::WriteLine("*--end() = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*-- --end() = [b 2]  
*--end() = [c 3]  
```  
  
## <a name="equal_range"></a> hash_map:: equal_range (STL/CLR)
查找与指定键匹配的范围。  
  
### <a name="syntax"></a>语法  
  
```  
cliext::pair<iterator, iterator> equal_range(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 `key`  
 要搜索的键值。  
  
### <a name="remarks"></a>备注  
 成员函数将返回一对迭代器`cliext::pair<iterator, iterator>(lower_bound(key), upper_bound(key))`。 你可以使用它来确定的受控序列中的当前与指定的键匹配的元素范围。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_equal_range.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
typedef Myhash_map::pair_iter_iter Pairii;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// display results of failed search   
    Pairii pair1 = c1.equal_range(L'x');   
    System::Console::WriteLine("equal_range(L'x') empty = {0}",   
        pair1.first == pair1.second);   
  
// display results of successful search   
    pair1 = c1.equal_range(L'b');   
    for (; pair1.first != pair1.second; ++pair1.first)   
        System::Console::Write(" [{0} {1}]",   
            pair1.first->first, pair1.first->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
equal_range(L'x') empty = True  
 [b 2]  
```  

## <a name="erase"></a> hash_map:: erase (STL/CLR)
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
 第一个成员函数删除指向的受控序列的元素`where`，并返回指定已移除的元素之外保留的第一个元素的迭代器或[hash_map:: end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`()`如果此类元素不存在。 用于删除单个元素。  
  
 第二个成员函数范围中移除受控序列的元素 [`first`， `last`)，并返回指定已移除，任何元素之外保留的第一个元素的迭代器或`end()`如果没有此类元素存在... 用于删除零个或多个由连续的元素。  
  
 第三个成员函数删除其键具有等效顺序受控任何的序列元素到`key`，并返回已移除的元素数的计数。 你可以使用它删除，用来计数与指定的键匹配的所有元素。  
  
 每个元素擦除需要受控序列中的元素数的对数成正比的时间。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_erase.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    cliext::hash_map<wchar_t, int> c1;   
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'a', 1));   
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'b', 2));   
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (cliext::hash_map<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase an element and reinspect   
    cliext::hash_map<wchar_t, int>::iterator it =   
        c1.erase(c1.begin());   
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",   
        it->first, it->second);   
  
// add elements and display " b c d e"   
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'd', 4));   
    c1.insert(cliext::hash_map<wchar_t, int>::make_value(L'e', 5));   
    for each (cliext::hash_map<wchar_t, int>::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// erase all but end   
    it = c1.end();   
    it = c1.erase(c1.begin(), --it);   
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",   
        it->first, it->second);   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
// erase end   
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));   
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
erase(begin()) = [b 2]  
 [b 2] [c 3] [d 4] [e 5]  
erase(begin(), end()-1) = [e 5]  
size() = 1  
erase(L'x') = 0  
erase(L'e') = 1  
```  

## <a name="find"></a> hash_map:: find (STL/CLR)
查找与指定键匹配的元素。  
  
### <a name="syntax"></a>语法  
  
```  
iterator find(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
### <a name="remarks"></a>备注  
 如果受控序列中的至少一个元素具有等效顺序与`key`，成员函数将返回指定这些元素之一的迭代器; 否则它将返回[hash_map:: end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md) `()`. 用于定位指定的键相匹配的受控序列中当前的元素。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_find.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
  
    Myhash_map::iterator it = c1.find(L'b');   
    System::Console::WriteLine("find {0} = [{1} {2}]",   
        L'b', it->first, it->second);   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
find A = False  
find b = [b 2]  
find C = False  
```  

## <a name="generic_container"></a> hash_map::generic_container (STL/CLR)
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
// cliext_hash_map_generic_container.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_map::generic_container^ gc1 = %c1;   
    for each (Myhash_map::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// modify generic and display original   
    gc1->insert(Myhash_map::make_value(L'd', 4));   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// modify original and display generic   
    c1.insert(Myhash_map::make_value(L'e', 5));   
    for each (Myhash_map::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3] [d 4]  
[a 1] [b 2] [c 3] [d 4] [e 5]  
```  

## <a name="generic_iterator"></a> hash_map::generic_iterator (STL/CLR)
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
// cliext_hash_map_generic_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_map::generic_container^ gc1 = %c1;   
    for each (Myhash_map::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_map::generic_iterator gcit = gc1->begin();   
    Myhash_map::generic_value gcval = *gcit;   
    System::Console::Write(" [{0} {1}]", gcval->first, gcval->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[a 1]  
``` 

## <a name="generic_reverse_iterator"></a> hash_map::generic_reverse_iterator (STL/CLR)
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
// cliext_hash_map_generic_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_map::generic_container^ gc1 = %c1;   
    for each (Myhash_map::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_map::generic_reverse_iterator gcit = gc1->rbegin();   
    Myhash_map::generic_value gcval = *gcit;   
    System::Console::WriteLine(" [{0} {1}]", gcval->first, gcval->second);   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[c 3]  
```   

## <a name="generic_value"></a> hash_map::generic_value (STL/CLR)
使用容器的泛型接口具有的元素的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef GValue generic_value;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述类型的对象`GValue`描述使用的存储的元素值与此模板容器类的泛型接口。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_generic_value.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Myhash_map::generic_container^ gc1 = %c1;   
    for each (Myhash_map::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Myhash_map::generic_iterator gcit = gc1->begin();   
    Myhash_map::generic_value gcval = *gcit;   
    System::Console::WriteLine(" [{0} {1}]", gcval->first, gcval->second);   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
[a 1]  
```  

## <a name="hash_delegate"></a> hash_map::hash_delegate (STL/CLR)
查找与指定键匹配的元素。  
  
### <a name="syntax"></a>语法  
  
```  
hasher^ hash_delegate();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回该委托用于将密钥值转换为整数。 你可以使用它进行哈希键。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_hash_delegate.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    Myhash_map::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
hash(L'a') = 1616896120  
hash(L'b') = 570892832  
``` 

## <a name="hash_map"></a> hash_map:: hash_map (STL/CLR)
构造容器对象。  
  
### <a name="syntax"></a>语法  
  
```  
hash_map();  
explicit hash_map(key_compare^ pred);  
hash_map(key_compare^ pred, hasher^ hashfn);  
hash_map(hash_map<Key, Mapped>% right);  
hash_map(hash_map<Key, Mapped>^ right);  
template<typename InIter>  
    hash_maphash_map(InIter first, InIter last);  
template<typename InIter>  
    hash_map(InIter first, InIter last,  
        key_compare^ pred);  
template<typename InIter>  
    hash_map(InIter first, InIter last,  
        key_compare^ pred, hasher^ hashfn);  
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right);  
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right,  
    key_compare^ pred);  
hash_map(System::Collections::Generic::IEnumerable<GValue>^ right,  
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
  
 `hash_map();`  
  
 使用默认的排序谓词初始化受控的序列不包含任何元素， `key_compare()`，并使用默认哈希运算。 用于指定空的初始受控的序列，使用默认的排序谓词和哈希函数。  
  
 构造函数：  
  
 `explicit hash_map(key_compare^ pred);`  
  
 初始化受控的序列不包含任何元素，与排序的谓词`pred`，并使用默认哈希运算。 用于指定空的初始受控的序列，使用指定的排序谓词和默认哈希函数。  
  
 构造函数：  
  
 `hash_map(key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控的序列不包含任何元素，与排序的谓词`pred`，并使用哈希运算`hashfn`。 用于指定空的初始受控的序列，使用指定的排序谓词和哈希函数。  
  
 构造函数：  
  
 `hash_map(hash_map<Key, Mapped>% right);`  
  
 初始化受控的序列与序列 [`right.begin()`， `right.end()`)、 排序谓词，默认值和默认哈希函数。 用于指定是由 hash_map 对象控制的序列的副本的初始受控的序列`right`、 与的默认排序谓词和哈希函数。  
  
 构造函数：  
  
 `hash_map(hash_map<Key, Mapped>^ right);`  
  
 初始化受控的序列与序列 [`right->begin()`， `right->end()`)、 排序谓词，默认值和默认哈希函数。 用于指定是由 hash_map 对象控制的序列的副本的初始受控的序列`right`、 与的默认排序谓词和哈希函数。  
  
 构造函数：  
  
 `template<typename InIter> hash_map(InIter first, InIter last);`  
  
 初始化受控的序列与序列 [`first`， `last`)、 排序谓词，默认值和默认哈希函数。 你可以使用它以使用默认的排序谓词和哈希函数使受控的序列的另一个序列，副本。  
  
 构造函数：  
  
 `template<typename InIter> hash_map(InIter first, InIter last, key_compare^ pred);`  
  
 初始化受控的序列与序列 [`first`， `last`)，与排序的谓词`pred`，并使用默认哈希运算。 你可以使用它以使另一个序列，使用指定的排序谓词和默认哈希函数的副本的受控的序列。  
  
 构造函数：  
  
 `template<typename InIter> hash_map(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`  
  
 初始化受控的序列与序列 [`first`， `last`)，与排序的谓词`pred`，并使用哈希运算`hashfn`。 你可以使用它以使另一个序列，使用指定的排序谓词和哈希函数的副本的受控的序列。  
  
 构造函数：  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right);`  
  
 初始化与枚举器指定序列的受控的序列`right`、 排序谓词，默认值和默认哈希函数。 你可以使用它来使一个枚举器，使用默认的排序谓词和哈希函数所描述的另一个序列的副本的受控的序列。  
  
 构造函数：  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`  
  
 初始化与枚举器指定序列的受控的序列`right`，与排序的谓词`pred`，并使用默认哈希运算。 你可以使用它以使所描述的枚举，使用指定排序谓词和默认哈希的函数的另一个序列的副本的受控的序列。  
  
 构造函数：  
  
 `hash_map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`  
  
 初始化与枚举器指定序列的受控的序列`right`，与排序的谓词`pred`，并使用哈希运算`hashfn`。 你可以使用它以使所描述的枚举，使用指定的排序谓词和哈希函数的另一个序列的副本的受控的序列。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_construct.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
int myfun(wchar_t key)   
    { // hash a key   
    return (key ^ 0xdeadbeef);   
    }   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
// construct an empty container   
    Myhash_map c1;   
    System::Console::WriteLine("size() = {0}", c1.size());   
  
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule   
    Myhash_map c2 = cliext::greater_equal<wchar_t>();   
    System::Console::WriteLine("size() = {0}", c2.size());   
  
    c2.insert(c1.begin(), c1.end());   
    for each (Myhash_map::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an ordering rule and hash function   
    Myhash_map c2h(cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_map::hasher(&myfun));   
    System::Console::WriteLine("size() = {0}", c2h.size());   
  
    c2h.insert(c1.begin(), c1.end());   
    for each (Myhash_map::value_type elem in c2h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an iterator range   
    Myhash_map c3(c1.begin(), c1.end());   
    for each (Myhash_map::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule   
    Myhash_map c4(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>());   
    for each (Myhash_map::value_type elem in c4)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an iterator range and an ordering rule and hash function   
    Myhash_map c4h(c1.begin(), c1.end(),   
        cliext::greater_equal<wchar_t>(),   
        gcnew Myhash_map::hasher(&myfun));   
    for each (Myhash_map::value_type elem in c4h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct with an enumeration   
    Myhash_map c5(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_map::value_type>^)%c3);   
    for each (Myhash_map::value_type elem in c5)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule   
    Myhash_map c6(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_map::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>());   
    for each (Myhash_map::value_type elem in c6)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct with an enumeration and an ordering rule and hash function   
    Myhash_map c6h(   // NOTE: cast is not needed   
        (System::Collections::Generic::IEnumerable<   
            Myhash_map::value_type>^)%c3,   
                cliext::greater_equal<wchar_t>(),   
                gcnew Myhash_map::hasher(&myfun));   
    for each (Myhash_map::value_type elem in c6h)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    System::Console::WriteLine();   
  
// construct by copying another container   
    Myhash_map c7(c4);   
    for each (Myhash_map::value_type elem in c7)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct by copying a container handle   
    Myhash_map c8(%c3);   
    for each (Myhash_map::value_type elem in c8)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [a 1] [b 2] [c 3]  
size() = 0  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
 [c 3] [b 2] [a 1]  
  
 [a 1] [b 2] [c 3]  
 [a 1] [b 2] [c 3]  
```   

## <a name="hasher"></a> hash_map::hasher (STL/CLR)
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
// cliext_hash_map_hasher.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    Myhash_map::hasher^ myhash = c1.hash_delegate();   
  
    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));   
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));   
    return (0);   
    }  
  
```  
  
```Output  
hash(L'a') = 1616896120  
hash(L'b') = 570892832  
```  
  
## <a name="insert"></a> hash_map:: insert (STL/CLR)
添加元素。  
  
### <a name="syntax"></a>语法  
  
```  
cliext::pair<iterator, bool> insert(value_type val);  
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
  
 val  
 要插入的密钥值。  
  
 其中  
 要插入 （仅提示） 的容器中的位置。  
  
### <a name="remarks"></a>备注  
 每个成员函数将插入剩余操作数指定的序列。  
  
 第一个成员函数插入具有值的元素致力于`val`，并返回一对值`X`。 如果`X.second`为 true，`X.first`指定新插入的元素; 否则为`X.first`指定具有等效的元素排序已经存在，并且插入任何新元素。 你可以使用它来插入单个元素。  
  
 第二个成员函数将具有值的元素插入`val`，使用`where`作为提示，（用于提高性能），并返回一个迭代器，指定新插入的元素。 你可以使用它来插入单个元素，这可能是靠近你知道的元素。  
  
 第三个成员函数将序列插入 [`first`， `last`)。 你可以使用它将从另一个序列复制的零个或多个元素。  
  
 第四个成员函数将由序列插入`right`。 用于插入一个枚举器所描述的序列。  
  
 每个元素插入受控序列中需要的元素数的对数成正比的时间。 插入可能发生在分期常量时间内，但是，给定一个提示，指示某个元素的插入点旁边。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_insert.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
typedef Myhash_map::pair_iter_bool Pairib;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value, unique and duplicate   
    Pairib pair1 =   
        c1.insert(Myhash_map::make_value(L'x', 24));   
    System::Console::WriteLine("insert([L'x' 24]) = [{0} {1}] {2}",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    pair1 = c1.insert(Myhash_map::make_value(L'b', 2));   
    System::Console::WriteLine("insert([L'b' 2]) = [{0} {1}] {2}",   
        pair1.first->first, pair1.first->second, pair1.second);   
  
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert a single value with hint   
    Myhash_map::iterator it =   
        c1.insert(c1.begin(), Myhash_map::make_value(L'y', 25));   
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",   
        it->first, it->second);   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an iterator range   
    Myhash_map c2;   
    it = c1.end();   
    c2.insert(c1.begin(), --it);   
    for each (Myhash_map::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// insert an enumeration   
    Myhash_map c3;   
    c3.insert(   // NOTE: cast is not needed   
        (System::Collections::Generic::   
            IEnumerable<Myhash_map::value_type>^)%c1);   
    for each (Myhash_map::value_type elem in c3)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
insert([L'x' 24]) = [x 24] True  
insert([L'b' 2]) = [b 2] False  
 [a 1] [b 2] [c 3] [x 24]  
insert(begin(), [L'y' 25]) = [y 25]  
 [a 1] [b 2] [c 3] [x 24] [y 25]  
 [a 1] [b 2] [c 3] [x 24]  
 [a 1] [b 2] [c 3] [x 24] [y 25]  
```  

## <a name="iterator"></a> hash_map:: iterator (STL/CLR)
受控序列的迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef T1 iterator;  
```  
  
### <a name="remarks"></a>备注  
 此类型描述未指定类型的对象`T1`，可用作受控序列的双向迭代器。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Myhash_map::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        System::Console::Write(" [{0} {1}]", it->first, it->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="key_comp"></a> hash_map:: key_comp (STL/CLR)
将复制为两个键排序的委托。  
  
### <a name="syntax"></a>语法  
  
```  
key_compare^key_comp();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回使用受控的序列进行排序的排序委托。 用于比较两个键。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_key_comp.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    Myhash_map::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_map c2 = cliext::greater<wchar_t>();   
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

## <a name="key_compare"></a> hash_map:: key_compare (STL/CLR)
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
// cliext_hash_map_key_compare.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    Myhash_map::key_compare^ kcomp = c1.key_comp();   
  
    System::Console::WriteLine("compare(L'a', L'a') = {0}",   
        kcomp(L'a', L'a'));   
    System::Console::WriteLine("compare(L'a', L'b') = {0}",   
        kcomp(L'a', L'b'));   
    System::Console::WriteLine("compare(L'b', L'a') = {0}",   
        kcomp(L'b', L'a'));   
    System::Console::WriteLine();   
  
// test a different ordering rule   
    Myhash_map c2 = cliext::greater<wchar_t>();   
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

## <a name="key_type"></a> hash_map:: key_type (STL/CLR)
排序键的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Key key_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Key` 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_key_type.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using key_type   
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in key_type object   
        Myhash_map::key_type val = it->first;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
a b c  
``` 

## <a name="load_factor"></a> hash_map::load_factor (STL/CLR)
对每个存储桶的平均元素数进行计数。  
  
### <a name="syntax"></a>语法  
  
```  
float load_factor();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回`(float)` [hash_map:: size (STL/CLR)](../dotnet/hash-map-size-stl-clr.md) `() /` [hash_map::bucket_count (STL/CLR)](../dotnet/hash-map-bucket-count-stl-clr.md)`()`。 你可以使用它来确定的平均存储桶大小。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_load_factor.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1 = gcnew Myhash_map;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
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
 [a 1] [b 2] [c 3]  
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

## <a name="lower_bound"></a> hash_map:: lower_bound (STL/CLR)
查找与指定的键匹配的范围开始处。  
  
### <a name="syntax"></a>语法  
  
```  
iterator lower_bound(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
### <a name="remarks"></a>备注  
 成员函数将确定第一个元素`X`作为相同的存储桶进行哈希处理到受控序列中`key`和具有等效顺序到`key`。 如果此类元素不存在，它将返回[hash_map:: end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`()`; 否则它将返回指定的迭代器`X`。 用于当前与指定的键匹配的控制序列中查找的元素序列的开头。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_lower_bound.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",   
        c1.lower_bound(L'x') == c1.end());   
  
    Myhash_map::iterator it = c1.lower_bound(L'a');   
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.lower_bound(L'b');   
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
lower_bound(L'x')==end() = True  
*lower_bound(L'a') = [a 1]  
*lower_bound(L'b') = [b 2]  
```  

## <a name="make_value"></a> hash_map::make_value (STL/CLR)
构造值对象。  
  
### <a name="syntax"></a>语法  
  
```  
static value_type make_value(key_type key, mapped_type mapped);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要使用的密钥值。  
  
 映射  
 要搜索的映射的值。  
  
### <a name="remarks"></a>备注  
 成员函数将返回`value_type`对象，其键是`key`并且其映射的值为`mapped`。 你可以使用它来编写适用于多个其他成员函数的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_make_value.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  
## <a name="mapped_type"></a> hash_map:: mapped_type (STL/CLR)
与每个键关联的映射值的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef Mapped mapped_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 `Mapped` 的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_mapped_type.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using mapped_type   
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in mapped_type object   
        Myhash_map::mapped_type val = it->second;   
  
        System::Console::Write(" {0}", val);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
1 2 3  
```  

## <a name="max_load_factor"></a> hash_map::max_load_factor (STL/CLR)
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
// cliext_hash_map_max_load_factor.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1 = gcnew Myhash_map;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
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
 [a 1] [b 2] [c 3]  
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

## <a name="op_as"></a> hash_map:: operator = (STL/CLR)
替换受控序列。  
  
### <a name="syntax"></a>语法  
  
```  
hash_map<Key, Mapped>% operator=(hash_map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 用于复制的容器。  
  
### <a name="remarks"></a>备注  
 成员运算符副本`right`到对象，然后返回`*this`。 用它将受控序列替换为 `right` 中的受控序列的副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_operator_as.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// assign to a new container   
    Myhash_map c2;   
    c2 = c1;   
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[a 1] [b 2] [c 3]  
``` 

## <a name="op"></a> hash_map::operator(STL/CLR)
将键映射到其关联的映射值。  
  
### <a name="syntax"></a>语法  
  
```  
mapped_type operator[](key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
### <a name="remarks"></a>备注  
 成员函数工作中查找具有等效排序的元素`key`。 如果找到，它将返回关联的映射的值;否则，它可以将插入`value_type(key, mapped_type())`并返回关联 （默认值） 映射值。 查找给定其关联的键的映射值或以确保一个条目存在的密钥，如果找不到，你使用它。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_operator_sub.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'A', c1[L'A']);   
    System::Console::WriteLine("c1[{0}] = {1}",   
        L'b', c1[L'b']);   
  
// redisplay altered contents   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// alter mapped values and redisplay   
    c1[L'A'] = 10;   
    c1[L'c'] = 13;   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
c1[A] = 0  
c1[b] = 2  
 [a 1] [A 0] [b 2] [c 3]  
 [a 1] [A 10] [b 2] [c 13]  
```  

## <a name="rbegin"></a> hash_map:: rbegin (STL/CLR)
指定反向受控序列的开头。  
  
### <a name="syntax"></a>语法  
  
```  
reverse_iterator rbegin();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回指定的受控序列，或刚超出空序列的开头的最后一个元素的反向迭代器。 因此，它指定`beginning`反向序列。 用于获取指定的迭代器`current`如果受控序列的长度发生更改，可以更改按逆序的受控的序列，但其状态的开头。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_rbegin.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Myhash_map::reverse_iterator rit = c1.rbegin();   
    System::Console::WriteLine("*rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*rbegin() = [c 3]  
*++rbegin() = [b 2]  
```   

## <a name="reference"></a> hash_map:: reference (STL/CLR)
元素的引用的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef value_type% reference;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述元素的引用。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_reference.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    Myhash_map::iterator it = c1.begin();   
    for (; it != c1.end(); ++it)   
        {   // get a reference to an element   
        Myhash_map::reference ref = *it;   
        System::Console::Write(" [{0} {1}]", ref->first, ref->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  

## <a name="rehash"></a> hash_map::rehash (STL/CLR)
重新生成哈希表。  
  
### <a name="syntax"></a>语法  
  
```  
void rehash();  
```  
  
### <a name="remarks"></a>备注  
 成员函数重新生成哈希表，从而确保[hash_map::load_factor (STL/CLR)](../dotnet/hash-map-load-factor-stl-clr.md) `() <=` [hash_map::max_load_factor (STL/CLR)](../dotnet/hash-map-max-load-factor-stl-clr.md)。 否则，哈希表的大小增加，仅在需要时后插入的操作。 （它永远不会自动的大小减小。）您可以使用它来调整哈希表的大小。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_rehash.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1 = gcnew Myhash_map;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
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
 [a 1] [b 2] [c 3]  
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

## <a name="rend"></a> hash_map:: rend (STL/CLR)
指定反向受控序列的末尾。  
  
### <a name="syntax"></a>语法  
  
```  
reverse_iterator rend();  
```  
  
### <a name="remarks"></a>备注  
 成员函数返回一个反向迭代器指向刚超出开头的受控序列。 因此，它指定`end`反向序列。 用于获取指定的迭代器`current`末尾按逆序的受控的序列，但其状态可以更改，如果更改了受控序列的长度。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_rend.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// inspect first two items in reversed sequence   
    Myhash_map::reverse_iterator rit = c1.rend();   
    --rit;   
    --rit;   
    System::Console::WriteLine("*-- --rend() = [{0} {1}]",   
        rit->first, rit->second);   
    ++rit;   
    System::Console::WriteLine("*--rend() = [{0} {1}]",   
        rit->first, rit->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
*-- --rend() = [b 2]  
*--rend() = [a 1]  
```  

## <a name="reverse_iterator"></a> hash_map:: reverse_iterator (STL/CLR)
受控序列的反向迭代器的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef T3 reverse_iterator;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述了可充当受控序列的反向迭代器的未指定类型 `T3` 的对象。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_reverse_iterator.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" reversed   
    Myhash_map::reverse_iterator rit = c1.rbegin();   
    for (; rit != c1.rend(); ++rit)   
        System::Console::Write(" [{0} {1}]", rit->first, rit->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[c 3] [b 2] [a 1]  
```  

## <a name="size"></a> hash_map:: size (STL/CLR)
对元素数进行计数。  
  
### <a name="syntax"></a>语法  
  
```  
size_type size();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回受控序列的长度。 用于确定当前受控序列中的元素的数目。 如果你关注的只是序列是否具有非零大小，请参阅[hash_map:: empty (STL/CLR)](../dotnet/hash-map-empty-stl-clr.md)`()`。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_size.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// clear the container and reinspect   
    c1.clear();   
    System::Console::WriteLine("size() = {0} after clearing", c1.size());   
  
// add elements and clear again   
    c1.insert(Myhash_map::make_value(L'd', 4));   
    c1.insert(Myhash_map::make_value(L'e', 5));   
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
size() = 0 after clearing  
size() = 2 after adding 2  
```  
  
## <a name="size_type"></a> hash_map:: size_type (STL/CLR)
两个元素之间的带符号距离的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef int size_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型描述非负元素计数。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_size_type.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// compute positive difference   
    Myhash_map::size_type diff = 0;   
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)   
        ++diff;   
    System::Console::WriteLine("end()-begin() = {0}", diff);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
end()-begin() = 3  
```  

## <a name="swap"></a> hash_map:: swap (STL/CLR)
交换两个容器的内容。  
  
### <a name="syntax"></a>语法  
  
```  
void swap(hash_map<Key, Mapped>% right);  
```  
  
#### <a name="parameters"></a>参数  
 右  
 要与其交换内容的容器。  
  
### <a name="remarks"></a>备注  
 成员函数交换 `this` 和 `right`之间的受控序列。 它会以在常量时间内，则会引发任何异常。 你将它用作交换两个容器的内容的快速方法。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_swap.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct another container with repetition of values   
    Myhash_map c2;   
    c2.insert(Myhash_map::make_value(L'd', 4));   
    c2.insert(Myhash_map::make_value(L'e', 5));   
    c2.insert(Myhash_map::make_value(L'f', 6));   
    for each (Myhash_map::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// swap and redisplay   
    c1.swap(c2);   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    for each (Myhash_map::value_type elem in c2)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
[d 4] [e 5] [f 6]  
[d 4] [e 5] [f 6]  
[a 1] [b 2] [c 3]  
```  

## <a name="to_array"></a> hash_map::to_array (STL/CLR)
受控的序列复制到新数组。  
  
### <a name="syntax"></a>语法  
  
```  
cli::array<value_type>^ to_array();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回包含受控的序列的数组。 用于获取受控序列中数组形式的副本。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_to_array.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// copy the container and modify it   
    cli::array<Myhash_map::value_type>^ a1 = c1.to_array();   
  
    c1.insert(Myhash_map::make_value(L'd', 4));   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// display the earlier array copy   
    for each (Myhash_map::value_type elem in a1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3] [d 4]  
[a 1] [b 2] [c 3]  
```  

## <a name="upper_bound"></a> hash_map:: upper_bound (STL/CLR)
查找与指定的键匹配的范围末尾。  
  
### <a name="syntax"></a>语法  
  
```  
iterator upper_bound(key_type key);  
```  
  
#### <a name="parameters"></a>参数  
 密钥  
 要搜索的键值。  
  
### <a name="remarks"></a>备注  
 成员函数将确定最后一个元素`X`作为相同的存储桶进行哈希处理到受控序列中`key`和具有等效顺序到`key`。 如果此类元素不存在，或者`X`为受控序列中的最后一个元素，它将返回[hash_map:: end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`()`; 否则它将返回指定以外的第一个元素的迭代器`X`. 用于当前与指定的键匹配的控制序列中查找的元素序列的末尾。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_upper_bound.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_map::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",   
        c1.upper_bound(L'x') == c1.end());   
  
    Myhash_map::iterator it = c1.upper_bound(L'a');   
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",   
        it->first, it->second);   
    it = c1.upper_bound(L'b');   
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",   
        it->first, it->second);   
    return (0);   
    }  
  
```  
  
```Output  
 [a 1] [b 2] [c 3]  
upper_bound(L'x')==end() = True  
*upper_bound(L'a') = [b 2]  
*upper_bound(L'b') = [c 3]  
```  

## <a name="value_comp"></a> hash_map:: value_comp (STL/CLR)
将复制两个元素值的排序委托。  
  
### <a name="syntax"></a>语法  
  
```  
value_compare^ value_comp();  
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回使用受控的序列进行排序的排序委托。 使用两个元素值进行比较。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_value_comp.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    Myhash_map::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",   
        kcomp(Myhash_map::make_value(L'a', 1),   
            Myhash_map::make_value(L'a', 1)));   
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",   
        kcomp(Myhash_map::make_value(L'a', 1),   
            Myhash_map::make_value(L'b', 2)));   
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",   
        kcomp(Myhash_map::make_value(L'b', 2),   
            Myhash_map::make_value(L'a', 1)));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare([L'a', 1], [L'a', 1]) = True  
compare([L'a', 1], [L'b', 2]) = True  
compare([L'b', 2], [L'a', 1]) = False  
```  

## <a name="value_compare"></a> hash_map::value_compare (STL/CLR)
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
// cliext_hash_map_value_compare.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    Myhash_map::value_compare^ kcomp = c1.value_comp();   
  
    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",   
        kcomp(Myhash_map::make_value(L'a', 1),   
            Myhash_map::make_value(L'a', 1)));   
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",   
        kcomp(Myhash_map::make_value(L'a', 1),   
            Myhash_map::make_value(L'b', 2)));   
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",   
        kcomp(Myhash_map::make_value(L'b', 2),   
            Myhash_map::make_value(L'a', 1)));   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
compare([L'a', 1], [L'a', 1]) = True  
compare([L'a', 1], [L'b', 2]) = True  
compare([L'b', 2], [L'a', 1]) = False  
```  

## <a name="value_type"></a> hash_map:: value_type (STL/CLR)
元素的类型。  
  
### <a name="syntax"></a>语法  
  
```  
typedef generic_value value_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是 `generic_value`的同义词。  
  
### <a name="example"></a>示例  
  
```cpp  
// cliext_hash_map_value_type.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_map<wchar_t, int> Myhash_map;   
int main()   
    {   
    Myhash_map c1;   
    c1.insert(Myhash_map::make_value(L'a', 1));   
    c1.insert(Myhash_map::make_value(L'b', 2));   
    c1.insert(Myhash_map::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]" using value_type   
    for (Myhash_map::iterator it = c1.begin(); it != c1.end(); ++it)   
        {   // store element in value_type object   
        Myhash_map::value_type val = *it;   
        System::Console::Write(" [{0} {1}]", val->first, val->second);   
        }   
    System::Console::WriteLine();   
    return (0);   
    }  
  
```  
  
```Output  
[a 1] [b 2] [c 3]  
```  
  