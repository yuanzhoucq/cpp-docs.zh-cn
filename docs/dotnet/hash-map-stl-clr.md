---
title: "hash_map (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::hash_map
dev_langs: C++
helpviewer_keywords:
- <cliext/hash_map> header [STL/CLR]
- <hash_map> header [STL/CLR]
- hash_map class [STL/CLR]
ms.assetid: c3cfc69b-04c6-42ae-a30e-0eda953fe883
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cff0a45360a74bcfd7612b4eabe60dcc1057507a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hashmap-stlclr"></a>hash_map (STL/CLR)
此模板类描述控制变长序列的元素具有双向访问的对象。 使用容器`hash_map`若要管理的元素序列作为哈希表，每个表项存储双向链接列表的节点，并存储一个元素，每个节点。 元素包含的密钥，以进行排序序列，并映射的值，其中会赶上。  
  
 在下面，描述`GValue`相同：  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 其中：  
  
 `GKey`等同于`Key`后者为 ref 类型，除非在此情况下它是`Key^`  
  
 `GMapped`等同于`Mapped`后者为 ref 类型，除非在此情况下它是`Mapped^`  
  
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
  
#### <a name="parameters"></a>参数  
 键  
 受控序列中的元素的关键组件的类型。  
  
 映射  
 受控序列中的元素的其他组件的类型。  
  
## <a name="members"></a>成员  
  
|类型定义|描述|  
|---------------------|-----------------|  
|[hash_map::const_iterator (STL/CLR)](../dotnet/hash-map-const-iterator-stl-clr.md)|受控序列的常量迭代器的类型。|  
|[hash_map::const_reference (STL/CLR)](../dotnet/hash-map-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[hash_map::const_reverse_iterator (STL/CLR)](../dotnet/hash-map-const-reverse-iterator-stl-clr.md)|受控序列的常量反向迭代器的类型。|  
|[hash_map::difference_type (STL/CLR)](../dotnet/hash-map-difference-type-stl-clr.md)|两个元素间的 （可能是带符号） 距离的类型。|  
|[hash_map::generic_container (STL/CLR)](../dotnet/hash-map-generic-container-stl-clr.md)|容器的泛型接口的类型。|  
|[hash_map::generic_iterator (STL/CLR)](../dotnet/hash-map-generic-iterator-stl-clr.md)|容器的泛型接口的迭代器类型。|  
|[hash_map::generic_reverse_iterator (STL/CLR)](../dotnet/hash-map-generic-reverse-iterator-stl-clr.md)|容器的泛型接口的反向迭代器的类型。|  
|[hash_map::generic_value (STL/CLR)](../dotnet/hash-map-generic-value-stl-clr.md)|容器的泛型接口的元素的类型。|  
|[hash_map::hasher (STL/CLR)](../dotnet/hash-map-hasher-stl-clr.md)|用于密钥的哈希委托。|  
|[hash_map::iterator (STL/CLR)](../dotnet/hash-map-iterator-stl-clr.md)|受控序列的迭代器的类型。|  
|[hash_map::key_compare (STL/CLR)](../dotnet/hash-map-key-compare-stl-clr.md)|两个键的排序的委托。|  
|[hash_map::key_type (STL/CLR)](../dotnet/hash-map-key-type-stl-clr.md)|排序键的类型。|  
|[hash_map::mapped_type (STL/CLR)](../dotnet/hash-map-mapped-type-stl-clr.md)|与每个键关联的映射值的类型。|  
|[hash_map::reference (STL/CLR)](../dotnet/hash-map-reference-stl-clr.md)|元素的引用的类型。|  
|[hash_map::reverse_iterator (STL/CLR)](../dotnet/hash-map-reverse-iterator-stl-clr.md)|受控序列的反向迭代器的类型。|  
|[hash_map::size_type (STL/CLR)](../dotnet/hash-map-size-type-stl-clr.md)|两个元素间的 （非负号） 距离的类型。|  
|[hash_map::value_compare (STL/CLR)](../dotnet/hash-map-value-compare-stl-clr.md)|两个元素值排序委托。|  
|[hash_map::value_type (STL/CLR)](../dotnet/hash-map-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[hash_map::begin (STL/CLR)](../dotnet/hash-map-begin-stl-clr.md)|指定受控序列的开头。|  
|[hash_map::bucket_count (STL/CLR)](../dotnet/hash-map-bucket-count-stl-clr.md)|对存储桶的数量进行计数。|  
|[hash_map::clear (STL/CLR)](../dotnet/hash-map-clear-stl-clr.md)|删除所有元素。|  
|[hash_map::count (STL/CLR)](../dotnet/hash-map-count-stl-clr.md)|对与指定的键匹配的元素计数。|  
|[hash_map::empty (STL/CLR)](../dotnet/hash-map-empty-stl-clr.md)|测试元素是否存在。|  
|[hash_map::end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)|指定受控序列的末尾。|  
|[hash_map::equal_range (STL/CLR)](../dotnet/hash-map-equal-range-stl-clr.md)|查找与指定键匹配的范围。|  
|[hash_map::erase (STL/CLR)](../dotnet/hash-map-erase-stl-clr.md)|移除指定位置处的元素。|  
|[hash_map::find (STL/CLR)](../dotnet/hash-map-find-stl-clr.md)|查找与指定键匹配的元素。|  
|[hash_map::hash_delegate (STL/CLR)](../dotnet/hash-map-hash-delegate-stl-clr.md)|将复制的键的哈希委托。|  
|[hash_map::hash_map (STL/CLR)](../dotnet/hash-map-hash-map-stl-clr.md)|构造容器对象。|  
|[hash_map::insert (STL/CLR)](../dotnet/hash-map-insert-stl-clr.md)|添加元素。|  
|[hash_map::key_comp (STL/CLR)](../dotnet/hash-map-key-comp-stl-clr.md)|将复制为两个键排序的委托。|  
|[hash_map::load_factor (STL/CLR)](../dotnet/hash-map-load-factor-stl-clr.md)|对每个存储桶的平均元素数进行计数。|  
|[hash_map::lower_bound (STL/CLR)](../dotnet/hash-map-lower-bound-stl-clr.md)|查找与指定的键匹配的范围开始处。|  
|[hash_map::make_value (STL/CLR)](../dotnet/hash-map-make-value-stl-clr.md)|构造值对象。|  
|[hash_map::max_load_factor (STL/CLR)](../dotnet/hash-map-max-load-factor-stl-clr.md)|获取或设置每个存储桶的最多元素数。|  
|[hash_map::rbegin (STL/CLR)](../dotnet/hash-map-rbegin-stl-clr.md)|指定反向受控序列的开头。|  
|[hash_map::rehash (STL/CLR)](../dotnet/hash-map-rehash-stl-clr.md)|重新生成哈希表。|  
|[hash_map::rend (STL/CLR)](../dotnet/hash-map-rend-stl-clr.md)|指定反向受控序列的末尾。|  
|[hash_map::size (STL/CLR)](../dotnet/hash-map-size-stl-clr.md)|对元素数进行计数。|  
|[hash_map::swap (STL/CLR)](../dotnet/hash-map-swap-stl-clr.md)|交换两个容器的内容。|  
|[hash_map::to_array (STL/CLR)](../dotnet/hash-map-to-array-stl-clr.md)|受控的序列复制到新数组。|  
|[hash_map::upper_bound (STL/CLR)](../dotnet/hash-map-upper-bound-stl-clr.md)|查找与指定的键匹配的范围末尾。|  
|[hash_map::value_comp (STL/CLR)](../dotnet/hash-map-value-comp-stl-clr.md)|将复制两个元素值的排序委托。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[hash_map::operator= (STL/CLR)](../dotnet/hash-map-operator-assign-stl-clr.md)|替换受控序列。|  
|[hash_map::operator(STL/CLR)](../dotnet/hash-map-operator-stl-clr.md)|将键映射到其关联的映射值。|  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
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
  
 `key_comp()(X, Y)`返回相同的布尔值导致每次调用。  
  
 如果`key_comp()(X, Y) && key_comp()(Y, X)`为 true，然后`X`和`Y`被认为具有等效顺序。  
  
 行为类似于任何排序规则`operator<=(key_type, key_type)`，`operator>=(key_type, key_type)`或`operator==(key_type, key_type)`定义 eqivalent 排序。  
  
 请注意，容器可确保仅元素键拥有等效顺序 （和为相同的整数值的哈希） 存储桶中相邻。 与模板类不同[hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)，模板类的对象`hash_map`可确保密钥的所有元素都是唯一。 （任何两个密钥不具有等效顺序。）  
  
 对象确定哪个存储桶应通过调用类型的存储的委托对象包含给定的排序键[hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md)。 通过调用成员函数来访问此存储的对象[hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()`获取取决于密钥的值的整数值。 在构造 hash_set; 时，可以指定存储的委托对象如果指定没有委托对象时，默认值是函数`System::Object::hash_value(key_type)`。 这意味着，任何密钥`X`和`Y`:  
  
 `hash_delegate()(X)`每次调用返回相同的整数结果。  
  
 如果`X`和`Y`拥有等效顺序，然后`hash_delegate()(X)`应返回与相同的整数结果`hash_delegate()(Y)`。  
  
 每个元素包含一个单独的键和映射的值。 序列是允许查找、 插入和移除任意元素与大量的操作，在最佳情况下至少与序列 （常量时间）-中的元素数量无关的方式表示。 此外，插入元素不会使迭代器失效，移除元素仅会使指向已移除元素的迭代器失效。  
  
 如果哈希的值不均匀分布，但是，可以退化哈希表。 在极端情况下-始终返回相同的值-的哈希函数查找、 插入和删除是序列 （线性时间） 中的元素数量成正比。 容器致力于选择一个合理的哈希函数，平均存储桶大小，并且哈希表大小 （存储桶的总数量），但是你可以重写任何或所有这些选择。 请参阅，例如，函数[hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md)和[hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md)。  
  
 Hash_map 支持双向迭代器，这意味着你可以单步执行到给定指定受控序列中的元素的迭代器的相邻元素。 特殊的头节点对应于返回的迭代器[hash_map:: end (STL/CLR)](../dotnet/hash-map-end-stl-clr.md)`()`。 如果存在，可以减少此迭代器来访问控制的序列中中的最后一个元素。 可以递增的 hash_map 迭代器来访问头节点，且然后将比较等于`end()`。 但不是能取消引用返回的迭代器`end()`。  
  
 请注意，不能引用到 hash_map 元素直接给定其数字位置-需要随机访问迭代器。  
  
 Hash_map 迭代器存储其关联的 hash_map 节点，后者反过来将存储到其关联的容器的句柄的句柄。 迭代器仅用于其关联的容器对象。 只要其关联的 hash_map 节点是与某些 hash_map 相关联，hash_map 迭代器就保持有效。 此外，有效的迭代器是 dereferencable-可用来访问或更改元素值，它指定-，只要不等于`end()`。  
  
 擦除或删除元素调用析构函数作为其存储的值。 销毁容器清除所有元素。 因此，其元素类型是一个 ref 类的容器可确保任何元素生存期限超过容器。 但请注意，句柄的容器未`not`销毁它的元素。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/hash_map >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [hash_map](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [映射 (STL/CLR)](../dotnet/map-stl-clr.md)   
 [多重映射 (STL/CLR)](../dotnet/multimap-stl-clr.md)   
 [多集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [设置 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)