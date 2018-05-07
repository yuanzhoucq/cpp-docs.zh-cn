---
title: 映射 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::map
dev_langs:
- C++
helpviewer_keywords:
- <map> header [STL/CLR]
- map class [STL/CLR]
- <cliext/map> header [STL/CLR]
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: cda679ed01e5266f0605639df45940d8f17e506d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="map-stlclr"></a>map (STL/CLR)
此模板类描述控制变长序列的元素具有双向访问的对象。 使用容器`map`来管理一个序列的元素作为 （几乎） 平衡的有序树的节点，各个存储一个元素。 元素包含的密钥，以进行排序序列，并映射的值，其中会赶上。  
  
 在下面，描述`GValue`相同：  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 其中：  
  
 `GKey` 等同于`Key`后者为 ref 类型，除非在此情况下它是 `Key^`  
  
 `GMapped` 等同于`Mapped`后者为 ref 类型，除非在此情况下它是 `Mapped^`  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class map  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
        System::Collections::Generic::IDictionary<Gkey, GMapped>,  
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>  
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
|[map::const_iterator (STL/CLR)](../dotnet/map-const-iterator-stl-clr.md)|受控序列的常量迭代器的类型。|  
|[map::const_reference (STL/CLR)](../dotnet/map-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[map::const_reverse_iterator (STL/CLR)](../dotnet/map-const-reverse-iterator-stl-clr.md)|受控序列的常量反向迭代器的类型。|  
|[map::difference_type (STL/CLR)](../dotnet/map-difference-type-stl-clr.md)|两个元素间的 （可能是带符号） 距离的类型。|  
|[map::generic_container (STL/CLR)](../dotnet/map-generic-container-stl-clr.md)|容器的泛型接口的类型。|  
|[map::generic_iterator (STL/CLR)](../dotnet/map-generic-iterator-stl-clr.md)|容器的泛型接口的迭代器类型。|  
|[map::generic_reverse_iterator (STL/CLR)](../dotnet/map-generic-reverse-iterator-stl-clr.md)|容器的泛型接口的反向迭代器的类型。|  
|[map::generic_value (STL/CLR)](../dotnet/map-generic-value-stl-clr.md)|容器的泛型接口的元素的类型。|  
|[map::iterator (STL/CLR)](../dotnet/map-iterator-stl-clr.md)|受控序列的迭代器的类型。|  
|[map::key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md)|两个键的排序的委托。|  
|[map::key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md)|排序键的类型。|  
|[map::mapped_type (STL/CLR)](../dotnet/map-mapped-type-stl-clr.md)|与每个键关联的映射值的类型。|  
|[map::reference (STL/CLR)](../dotnet/map-reference-stl-clr.md)|元素的引用的类型。|  
|[map::reverse_iterator (STL/CLR)](../dotnet/map-reverse-iterator-stl-clr.md)|受控序列的反向迭代器的类型。|  
|[map::size_type (STL/CLR)](../dotnet/map-size-type-stl-clr.md)|两个元素间的 （非负号） 距离的类型。|  
|[map::value_compare (STL/CLR)](../dotnet/map-value-compare-stl-clr.md)|两个元素值排序委托。|  
|[map::value_type (STL/CLR)](../dotnet/map-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[map::begin (STL/CLR)](../dotnet/map-begin-stl-clr.md)|指定受控序列的开头。|  
|[map::clear (STL/CLR)](../dotnet/map-clear-stl-clr.md)|删除所有元素。|  
|[map::count (STL/CLR)](../dotnet/map-count-stl-clr.md)|对与指定的键匹配的元素计数。|  
|[map::empty (STL/CLR)](../dotnet/map-empty-stl-clr.md)|测试元素是否存在。|  
|[map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)|指定受控序列的末尾。|  
|[map::equal_range (STL/CLR)](../dotnet/map-equal-range-stl-clr.md)|查找与指定键匹配的范围。|  
|[map::erase (STL/CLR)](../dotnet/map-erase-stl-clr.md)|移除指定位置处的元素。|  
|[map::find (STL/CLR)](../dotnet/map-find-stl-clr.md)|查找与指定键匹配的元素。|  
|[map::insert (STL/CLR)](../dotnet/map-insert-stl-clr.md)|添加元素。|  
|[map::key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)|将复制为两个键排序的委托。|  
|[map::lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md)|查找与指定的键匹配的范围开始处。|  
|[map::make_value (STL/CLR)](../dotnet/map-make-value-stl-clr.md)|构造值对象。|  
|[map::map (STL/CLR)](../dotnet/map-map-stl-clr.md)|构造容器对象。|  
|[map::rbegin (STL/CLR)](../dotnet/map-rbegin-stl-clr.md)|指定反向受控序列的开头。|  
|[map::rend (STL/CLR)](../dotnet/map-rend-stl-clr.md)|指定反向受控序列的末尾。|  
|[map::size (STL/CLR)](../dotnet/map-size-stl-clr.md)|对元素数进行计数。|  
|[map::swap (STL/CLR)](../dotnet/map-swap-stl-clr.md)|交换两个容器的内容。|  
|[map::to_array (STL/CLR)](../dotnet/map-to-array-stl-clr.md)|受控的序列复制到新数组。|  
|[map::upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)|查找与指定的键匹配的范围末尾。|  
|[map::value_comp (STL/CLR)](../dotnet/map-value-comp-stl-clr.md)|将复制两个元素值的排序委托。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[map::operator= (STL/CLR)](../dotnet/map-operator-assign-stl-clr.md)|替换受控序列。|  
|[map::operator(STL/CLR)](../dotnet/map-operator-stl-clr.md)|将键映射到其关联的映射值。|  
|[operator!= (map) (STL/CLR)](../dotnet/operator-inequality-map-stl-clr.md)|确定如果`map`对象是否不等于另一个`map`对象。|  
|[operator< (map) (STL/CLR)](../dotnet/operator-less-than-map-stl-clr.md)|确定如果`map`对象是否小于另一个`map`对象。|  
|[operator<= (map) (STL/CLR)](../dotnet/operator-less-or-equal-map-stl-clr.md)|确定如果`map`对象是否小于或等于另一个`map`对象。|  
|[operator== (map) (STL/CLR)](../dotnet/operator-equality-map-stl-clr.md)|确定如果`map`对象是否等于另一个`map`对象。|  
|[operator> (map) (STL/CLR)](../dotnet/operator-greater-than-map-stl-clr.md)|确定如果`map`对象是否大于另一个`map`对象。|  
|[operator>= (map) (STL/CLR)](../dotnet/operator-greater-or-equal-map-stl-clr.md)|确定如果`map`对象是否大于或等于另一个`map`对象。|  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|复制对象。|  
|<xref:System.Collections.IEnumerable>|通过元素的序列。|  
|<xref:System.Collections.ICollection>|维护的组元素。|  
|<xref:System.Collections.Generic.IEnumerable%601>|访问类型化的元素序列。|  
|<xref:System.Collections.Generic.ICollection%601>|维护的组类型化的元素。|  
|<xref:System.Collections.Generic.IDictionary%602>|维护组 {键，值} 对。|  
|ITree < 键，值 >|维护泛型容器。|  
  
## <a name="remarks"></a>备注  
 对象分配和释放各个节点作为其控制的序列的存储。 它将元素插入到通过变更节点，永远不会通过将一个节点的内容复制到另一个之间的链接保持有序 （几乎） 平衡的树。 这意味着可以插入和移除自由不影响剩余元素的元素。  
  
 该对象进行排序它通过调用类型的存储的委托对象控制的序列[map:: key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md)。 在构造映射; 时，可以指定存储的委托对象如果指定没有委托对象时，默认值是比较`operator<(key_type, key_type)`。 通过调用成员函数来访问此存储的对象[map:: key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)`()`。  
  
 此类委托对象必须进行严格弱排序键的类型在施加[map:: key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md)。 这意味着为任何两个键`X`和`Y`:  
  
 `key_comp()(X, Y)` 返回相同的布尔值导致每次调用。  
  
 如果`key_comp()(X, Y)`为 true，然后`key_comp()(Y, X)`必须是 false。  
  
 如果`key_comp()(X, Y)`为 true，然后`X`称为才能进行排序之前`Y`。  
  
 如果`!key_comp()(X, Y) && !key_comp()(Y, X)`为 true，然后`X`和`Y`被认为具有等效顺序。  
  
 任何元素`X`，之前`Y`受控序列中中,`key_comp()(Y, X)`为 false。 （对于默认委托对象，密钥永远不会减小值中。）与模板类不同[映射](../dotnet/map-stl-clr.md)，模板类的对象`map`不需要的所有元素的键是唯一。 （两个或多个密钥可以拥有等效顺序。）  
  
 每个元素包含一个单独的键和映射的值。 序列是按顺序 （对数时间） 允许查找、 插入和移除任意元素与大量的操作的元素数的对数成正比的方式表示。 此外，插入元素不会使迭代器失效，移除元素仅会使指向已移除元素的迭代器失效。  
  
 地图支持双向迭代器，这意味着你可以单步执行到给定指定受控序列中的元素的迭代器的相邻元素。 特殊的头节点对应于返回的迭代器[map:: end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`。 如果存在，可以减少此迭代器来访问控制的序列中中的最后一个元素。 可以递增的映射迭代器来访问头节点，且然后将比较等于`end()`。 但不是能取消引用返回的迭代器`end()`。  
  
 请注意，不能引用地图元素直接给定其数字位置-需要随机访问迭代器。  
  
 映射迭代器存储其关联的映射节点，后者反过来将存储到其关联的容器的句柄的句柄。 迭代器仅用于其关联的容器对象。 只要其关联的映射节点是与某个映射相关联，映射迭代器就保持有效。 此外，有效的迭代器是 dereferencable-可用来访问或更改元素值，它指定-，只要不等于`end()`。  
  
 擦除或删除元素调用析构函数作为其存储的值。 销毁容器清除所有元素。 因此，其元素类型是一个 ref 类的容器可确保任何元素生存期限超过容器。 但请注意，句柄的容器未`not`销毁它的元素。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/映射 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [映射](../dotnet/map-stl-clr.md)   
 [多集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [设置 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)