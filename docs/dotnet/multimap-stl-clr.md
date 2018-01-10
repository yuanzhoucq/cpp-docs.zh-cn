---
title: "多重映射 (STL/CLR) |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: cliext::multimap
dev_langs: C++
helpviewer_keywords:
- <map> header [STL/CLR]
- <cliext/map> header [STL/CLR]
- multimap class [STL/CLR]
ms.assetid: 3dfe329d-a078-462a-b050-7999ce6110ad
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2c42fc8d71871a70e3a2d3ffa93a78a4e42d2f53
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="multimap-stlclr"></a>multimap (STL/CLR)
此模板类描述控制变长序列的元素具有双向访问的对象。 使用容器`multimap`来管理一个序列的元素作为 （几乎） 平衡的有序树的节点，各个存储一个元素。 元素包含的密钥，以进行排序序列，并映射的值，其中会赶上。  
  
 在下面，描述`GValue`相同：  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 其中：  
  
 `GKey`等同于`Key`后者为 ref 类型，除非在此情况下它是`Key^`  
  
 `GMapped`等同于`Mapped`后者为 ref 类型，除非在此情况下它是`Mapped^`  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Key,  
    typename Mapped>  
    ref class multimap  
        :   public  
        System::ICloneable,  
        System::Collections::IEnumerable,  
        System::Collections::ICollection,  
        System::Collections::Generic::IEnumerable<GValue>,  
        System::Collections::Generic::ICollection<GValue>,  
        System::Collections::Generic::IList<GValue>,  
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
|[multimap::const_iterator (STL/CLR)](../dotnet/multimap-const-iterator-stl-clr.md)|受控序列的常量迭代器的类型。|  
|[multimap::const_reference (STL/CLR)](../dotnet/multimap-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[multimap::const_reverse_iterator (STL/CLR)](../dotnet/multimap-const-reverse-iterator-stl-clr.md)|受控序列的常量反向迭代器的类型。|  
|[multimap::difference_type (STL/CLR)](../dotnet/multimap-difference-type-stl-clr.md)|两个元素间的 （可能是带符号） 距离的类型。|  
|[multimap::generic_container (STL/CLR)](../dotnet/multimap-generic-container-stl-clr.md)|容器的泛型接口的类型。|  
|[multimap::generic_iterator (STL/CLR)](../dotnet/multimap-generic-iterator-stl-clr.md)|容器的泛型接口的迭代器类型。|  
|[multimap::generic_reverse_iterator (STL/CLR)](../dotnet/multimap-generic-reverse-iterator-stl-clr.md)|容器的泛型接口的反向迭代器的类型。|  
|[multimap::generic_value (STL/CLR)](../dotnet/multimap-generic-value-stl-clr.md)|容器的泛型接口的元素的类型。|  
|[multimap::iterator (STL/CLR)](../dotnet/multimap-iterator-stl-clr.md)|受控序列的迭代器的类型。|  
|[multimap::key_compare (STL/CLR)](../dotnet/multimap-key-compare-stl-clr.md)|两个键的排序的委托。|  
|[multimap::key_type (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md)|排序键的类型。|  
|[multimap::mapped_type (STL/CLR)](../dotnet/multimap-mapped-type-stl-clr.md)|与每个键关联的映射值的类型。|  
|[multimap::reference (STL/CLR)](../dotnet/multimap-reference-stl-clr.md)|元素的引用的类型。|  
|[multimap::reverse_iterator (STL/CLR)](../dotnet/multimap-reverse-iterator-stl-clr.md)|受控序列的反向迭代器的类型。|  
|[multimap::size_type (STL/CLR)](../dotnet/multimap-size-type-stl-clr.md)|两个元素间的 （非负号） 距离的类型。|  
|[multimap::value_compare (STL/CLR)](../dotnet/multimap-value-compare-stl-clr.md)|两个元素值排序委托。|  
|[multimap::value_type (STL/CLR)](../dotnet/multimap-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[multimap::begin (STL/CLR)](../dotnet/multimap-begin-stl-clr.md)|指定受控序列的开头。|  
|[multimap::clear (STL/CLR)](../dotnet/multimap-clear-stl-clr.md)|删除所有元素。|  
|[multimap::count (STL/CLR)](../dotnet/multimap-count-stl-clr.md)|对与指定的键匹配的元素计数。|  
|[multimap::empty (STL/CLR)](../dotnet/multimap-empty-stl-clr.md)|测试元素是否存在。|  
|[multimap::end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)|指定受控序列的末尾。|  
|[multimap::equal_range (STL/CLR)](../dotnet/multimap-equal-range-stl-clr.md)|查找与指定键匹配的范围。|  
|[multimap::erase (STL/CLR)](../dotnet/multimap-erase-stl-clr.md)|移除指定位置处的元素。|  
|[multimap::find (STL/CLR)](../dotnet/multimap-find-stl-clr.md)|查找与指定键匹配的元素。|  
|[multimap::insert (STL/CLR)](../dotnet/multimap-insert-stl-clr.md)|添加元素。|  
|[multimap::key_comp (STL/CLR)](../dotnet/multimap-key-comp-stl-clr.md)|将复制为两个键排序的委托。|  
|[multimap::lower_bound (STL/CLR)](../dotnet/multimap-lower-bound-stl-clr.md)|查找与指定的键匹配的范围开始处。|  
|[multimap::make_value (STL/CLR)](../dotnet/multimap-make-value-stl-clr.md)|构造值对象。|  
|[multimap::multimap (STL/CLR)](../dotnet/multimap-multimap-stl-clr.md)|构造容器对象。|  
|[multimap::rbegin (STL/CLR)](../dotnet/multimap-rbegin-stl-clr.md)|指定反向受控序列的开头。|  
|[multimap::rend (STL/CLR)](../dotnet/multimap-rend-stl-clr.md)|指定反向受控序列的末尾。|  
|[multimap::size (STL/CLR)](../dotnet/multimap-size-stl-clr.md)|对元素数进行计数。|  
|[multimap::swap (STL/CLR)](../dotnet/multimap-swap-stl-clr.md)|交换两个容器的内容。|  
|[multimap::to_array (STL/CLR)](../dotnet/multimap-to-array-stl-clr.md)|受控的序列复制到新数组。|  
|[multimap::upper_bound (STL/CLR)](../dotnet/multimap-upper-bound-stl-clr.md)|查找与指定的键匹配的范围末尾。|  
|[multimap::value_comp (STL/CLR)](../dotnet/multimap-value-comp-stl-clr.md)|将复制两个元素值的排序委托。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[multimap::operator= (STL/CLR)](../dotnet/multimap-operator-assign-stl-clr.md)|替换受控序列。|  
|[operator!= (multimap) (STL/CLR)](../dotnet/operator-inequality-multimap-stl-clr.md)|确定如果`multimap`对象是否不等于另一个`multimap`对象。|  
|[operator< (multimap) (STL/CLR)](../dotnet/operator-less-than-multimap-stl-clr.md)|确定如果`multimap`对象是否小于另一个`multimap`对象。|  
|[operator<= (multimap) (STL/CLR)](../dotnet/operator-less-or-equal-multimap-stl-clr.md)|确定如果`multimap`对象是否小于或等于另一个`multimap`对象。|  
|[operator== (multimap) (STL/CLR)](../dotnet/operator-equality-multimap-stl-clr.md)|确定如果`multimap`对象是否等于另一个`multimap`对象。|  
|[operator> (multimap) (STL/CLR)](../dotnet/operator-greater-than-multimap-stl-clr.md)|确定如果`multimap`对象是否大于另一个`multimap`对象。|  
|[operator>= (multimap) (STL/CLR)](../dotnet/operator-greater-or-equal-multimap-stl-clr.md)|确定如果`multimap`对象是否大于或等于另一个`multimap`对象。|  
  
## <a name="interfaces"></a>接口  
  
|接口|描述|  
|---------------|-----------------|  
|<xref:System.ICloneable>|复制对象。|  
|<xref:System.Collections.IEnumerable>|通过元素的序列。|  
|<xref:System.Collections.ICollection>|维护的组元素。|  
|<xref:System.Collections.Generic.IEnumerable%601>|访问类型化的元素序列。|  
|<xref:System.Collections.Generic.ICollection%601>|维护的组类型化的元素。|  
|ITree\<密钥，值 >|维护泛型容器。|  
  
## <a name="remarks"></a>备注  
 对象分配和释放各个节点作为其控制的序列的存储。 它将元素插入到通过变更节点，永远不会通过将一个节点的内容复制到另一个之间的链接保持有序 （几乎） 平衡的树。 这意味着可以插入和移除自由不影响剩余元素的元素。  
  
 该对象进行排序它通过调用类型的存储的委托对象控制的序列[multimap:: key_compare (STL/CLR)](../dotnet/multimap-key-compare-stl-clr.md)。 在构造多重映射; 时，可以指定存储的委托对象如果指定没有委托对象时，默认值是比较`operator<(key_type, key_type)`。 通过调用成员函数来访问此存储的对象[multimap:: key_comp (STL/CLR)](../dotnet/multimap-key-comp-stl-clr.md)`()`。  
  
 此类委托对象必须进行严格弱排序键的类型在施加[multimap:: key_type (STL/CLR)](../dotnet/multimap-key-type-stl-clr.md)。 这意味着为任何两个键`X`和`Y`:  
  
 `key_comp()(X, Y)`返回相同的布尔值导致每次调用。  
  
 如果`key_comp()(X, Y)`为 true，然后`key_comp()(Y, X)`必须是 false。  
  
 如果`key_comp()(X, Y)`为 true，然后`X`称为才能进行排序之前`Y`。  
  
 如果`!key_comp()(X, Y) && !key_comp()(Y, X)`为 true，然后`X`和`Y`被认为具有等效顺序。  
  
 任何元素`X`，之前`Y`受控序列中中,`key_comp()(Y, X)`为 false。 （对于默认委托对象，密钥永远不会减小值中。）与模板类不同[映射 (STL/CLR)](../dotnet/map-stl-clr.md)，模板类的对象`multimap`不需要的所有元素的键是唯一。 （两个或多个密钥可以拥有等效顺序。）  
  
 每个元素包含一个单独的键和映射的值。 序列是按顺序 （对数时间） 允许查找、 插入和移除任意元素与大量的操作的元素数的对数成正比的方式表示。 此外，插入元素不会使迭代器失效，移除元素仅会使指向已移除元素的迭代器失效。  
  
 多重映射支持双向迭代器，这意味着你可以单步执行到给定指定受控序列中的元素的迭代器的相邻元素。 特殊的头节点对应于返回的迭代器[multimap:: end (STL/CLR)](../dotnet/multimap-end-stl-clr.md)`()`。 如果存在，可以减少此迭代器来访问控制的序列中中的最后一个元素。 可以递增的多重映射的迭代器来访问头节点，且然后将比较等于`end()`。 但不是能取消引用返回的迭代器`end()`。  
  
 请注意，不能引用直接给定其数字位置-需要随机访问迭代器的多重映射元素。  
  
 Multimap 的迭代器存储其关联的多重映射节点，后者反过来将存储到其关联的容器的句柄的句柄。 迭代器仅用于其关联的容器对象。 Multimap 的迭代器就保持有效的只要其关联的多重映射节点是与某些多重映射相关联。 此外，有效的迭代器是 dereferencable-可用来访问或更改元素值，它指定-，只要不等于`end()`。  
  
 擦除或删除元素调用析构函数作为其存储的值。 销毁容器清除所有元素。 因此，其元素类型是一个 ref 类的容器可确保任何元素生存期限超过容器。 但请注意，句柄的容器未`not`销毁它的元素。  
  
## <a name="requirements"></a>惠?  
 **标头：** \<cliext/映射 >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multimap (STL/CLR)](../dotnet/hash-multimap-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [映射 (STL/CLR)](../dotnet/map-stl-clr.md)   
 [多集 (STL/CLR)](../dotnet/multiset-stl-clr.md)   
 [设置 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)