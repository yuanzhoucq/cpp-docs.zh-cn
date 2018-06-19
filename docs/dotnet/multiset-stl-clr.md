---
title: 多集 (STL/CLR) |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: reference
f1_keywords:
- cliext::multiset
dev_langs:
- C++
helpviewer_keywords:
- <cliext/set> header [STL/CLR]
- <set> header [STL/CLR]
- multiset class [STL/CLR]
ms.assetid: 7c46e2b4-cd88-49b7-a9e6-63ad5ae7feb5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3e01ec2d9c426d6b95b12fe0db9e5a2e328ae1cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33138478"
---
# <a name="multiset-stlclr"></a>multiset (STL/CLR)
此模板类描述控制变长序列的元素具有双向访问的对象。 使用容器`multiset`来管理一个序列的元素作为 （几乎） 平衡的有序树的节点，各个存储一个元素。  
  
 在下面，描述`GValue`相同`GKey`，这反过来是相同`Key`后者为 ref 类型，除非在这种情况下很`Key^`。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename Key>  
    ref class multiset  
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
  
## <a name="members"></a>成员  
  
|类型定义|描述|  
|---------------------|-----------------|  
|[multiset::const_iterator (STL/CLR)](../dotnet/multiset-const-iterator-stl-clr.md)|受控序列的常量迭代器的类型。|  
|[multiset::const_reference (STL/CLR)](../dotnet/multiset-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[multiset::const_reverse_iterator (STL/CLR)](../dotnet/multiset-const-reverse-iterator-stl-clr.md)|受控序列的常量反向迭代器的类型。|  
|[multiset::difference_type (STL/CLR)](../dotnet/multiset-difference-type-stl-clr.md)|两个元素间的 （可能是带符号） 距离的类型。|  
|[multiset::generic_container (STL/CLR)](../dotnet/multiset-generic-container-stl-clr.md)|容器的泛型接口的类型。|  
|[multiset::generic_iterator (STL/CLR)](../dotnet/multiset-generic-iterator-stl-clr.md)|容器的泛型接口的迭代器类型。|  
|[multiset::generic_reverse_iterator (STL/CLR)](../dotnet/multiset-generic-reverse-iterator-stl-clr.md)|容器的泛型接口的反向迭代器的类型。|  
|[multiset::generic_value (STL/CLR)](../dotnet/multiset-generic-value-stl-clr.md)|容器的泛型接口的元素的类型。|  
|[multiset::iterator (STL/CLR)](../dotnet/multiset-iterator-stl-clr.md)|受控序列的迭代器的类型。|  
|[multiset::key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md)|两个键的排序的委托。|  
|[multiset::key_type (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md)|排序键的类型。|  
|[multiset::reference (STL/CLR)](../dotnet/multiset-reference-stl-clr.md)|元素的引用的类型。|  
|[multiset::reverse_iterator (STL/CLR)](../dotnet/multiset-reverse-iterator-stl-clr.md)|受控序列的反向迭代器的类型。|  
|[multiset::size_type (STL/CLR)](../dotnet/multiset-size-type-stl-clr.md)|两个元素间的 （非负号） 距离的类型。|  
|[multiset::value_compare (STL/CLR)](../dotnet/multiset-value-compare-stl-clr.md)|两个元素值排序委托。|  
|[multiset::value_type (STL/CLR)](../dotnet/multiset-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|描述|  
|---------------------|-----------------|  
|[multiset::begin (STL/CLR)](../dotnet/multiset-begin-stl-clr.md)|指定受控序列的开头。|  
|[multiset::clear (STL/CLR)](../dotnet/multiset-clear-stl-clr.md)|删除所有元素。|  
|[multiset::count (STL/CLR)](../dotnet/multiset-count-stl-clr.md)|对与指定的键匹配的元素计数。|  
|[multiset::empty (STL/CLR)](../dotnet/multiset-empty-stl-clr.md)|测试元素是否存在。|  
|[multiset::end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)|指定受控序列的末尾。|  
|[multiset::equal_range (STL/CLR)](../dotnet/multiset-equal-range-stl-clr.md)|查找与指定键匹配的范围。|  
|[multiset::erase (STL/CLR)](../dotnet/multiset-erase-stl-clr.md)|移除指定位置处的元素。|  
|[multiset::find (STL/CLR)](../dotnet/multiset-find-stl-clr.md)|查找与指定键匹配的元素。|  
|[multiset::insert (STL/CLR)](../dotnet/multiset-insert-stl-clr.md)|添加元素。|  
|[multiset::key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)|将复制为两个键排序的委托。|  
|[multiset::lower_bound (STL/CLR)](../dotnet/multiset-lower-bound-stl-clr.md)|查找与指定的键匹配的范围开始处。|  
|[multiset::make_value (STL/CLR)](../dotnet/multiset-make-value-stl-clr.md)|构造值对象。|  
|[multiset::multiset (STL/CLR)](../dotnet/multiset-multiset-stl-clr.md)|构造容器对象。|  
|[multiset::rbegin (STL/CLR)](../dotnet/multiset-rbegin-stl-clr.md)|指定反向受控序列的开头。|  
|[multiset::rend (STL/CLR)](../dotnet/multiset-rend-stl-clr.md)|指定反向受控序列的末尾。|  
|[multiset::size (STL/CLR)](../dotnet/multiset-size-stl-clr.md)|对元素数进行计数。|  
|[multiset::swap (STL/CLR)](../dotnet/multiset-swap-stl-clr.md)|交换两个容器的内容。|  
|[multiset::to_array (STL/CLR)](../dotnet/multiset-to-array-stl-clr.md)|受控的序列复制到新数组。|  
|[multiset::upper_bound (STL/CLR)](../dotnet/multiset-upper-bound-stl-clr.md)|查找与指定的键匹配的范围末尾。|  
|[multiset::value_comp (STL/CLR)](../dotnet/multiset-value-comp-stl-clr.md)|将复制两个元素值的排序委托。|  
  
|运算符|描述|  
|--------------|-----------------|  
|[multiset::operator= (STL/CLR)](../dotnet/multiset-operator-assign-stl-clr.md)|替换受控序列。|  
|[operator!= (multiset) (STL/CLR)](../dotnet/operator-inequality-multiset-stl-clr.md)|确定如果`multiset`对象是否不等于另一个`multiset`对象。|  
|[operator< (multiset) (STL/CLR)](../dotnet/operator-less-than-multiset-stl-clr.md)|确定如果`multiset`对象是否小于另一个`multiset`对象。|  
|[operator<= (multiset) (STL/CLR)](../dotnet/operator-less-or-equal-multiset-stl-clr.md)|确定如果`multiset`对象是否小于或等于另一个`multiset`对象。|  
|[operator== (multiset) (STL/CLR)](../dotnet/operator-equality-multiset-stl-clr.md)|确定如果`multiset`对象是否等于另一个`multiset`对象。|  
|[operator> (multiset) (STL/CLR)](../dotnet/operator-greater-than-multiset-stl-clr.md)|确定如果`multiset`对象是否大于另一个`multiset`对象。|  
|[operator>= (multiset) (STL/CLR)](../dotnet/operator-greater-or-equal-multiset-stl-clr.md)|确定如果`multiset`对象是否大于或等于另一个`multiset`对象。|  
  
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
  
 该对象进行排序它通过调用类型的存储的委托对象控制的序列[multiset:: key_compare (STL/CLR)](../dotnet/multiset-key-compare-stl-clr.md)。 在构造多重集合; 时，可以指定存储的委托对象如果指定没有委托对象时，默认值是比较`operator<(key_type, key_type)`。 通过调用成员函数来访问此存储的对象[multiset:: key_comp (STL/CLR)](../dotnet/multiset-key-comp-stl-clr.md)`()`。  
  
 此类委托对象必须进行严格弱排序键的类型在施加[multiset:: key_type (STL/CLR)](../dotnet/multiset-key-type-stl-clr.md)。 这意味着为任何两个键`X`和`Y`:  
  
 `key_comp()(X, Y)` 返回相同的布尔值导致每次调用。  
  
 如果`key_comp()(X, Y)`为 true，然后`key_comp()(Y, X)`必须是 false。  
  
 如果`key_comp()(X, Y)`为 true，然后`X`称为才能进行排序之前`Y`。  
  
 如果`!key_comp()(X, Y) && !key_comp()(Y, X)`为 true，然后`X`和`Y`被认为具有等效顺序。  
  
 任何元素`X`，之前`Y`受控序列中中,`key_comp()(Y, X)`为 false。 （对于默认委托对象，密钥永远不会减小值中。）与模板类不同[设置 (STL/CLR)](../dotnet/set-stl-clr.md)，模板类的对象`multiset`不需要的所有元素的键是唯一。 （两个或多个密钥可以拥有等效顺序。）  
  
 每个元素用作框里和一个值。 序列是按顺序 （对数时间） 允许查找、 插入和移除任意元素与大量的操作的元素数的对数成正比的方式表示。 此外，插入元素不会使迭代器失效，移除元素仅会使指向已移除元素的迭代器失效。  
  
 多集支持双向迭代器，这意味着你可以单步执行到给定指定受控序列中的元素的迭代器的相邻元素。 特殊的头节点对应于返回的迭代器[multiset:: end (STL/CLR)](../dotnet/multiset-end-stl-clr.md)`()`。 如果存在，可以减少此迭代器来访问控制的序列中中的最后一个元素。 可以递增的多集的迭代器来访问头节点，且然后将比较等于`end()`。 但不是能取消引用返回的迭代器`end()`。  
  
 请注意，不能引用直接给定其数字位置-需要随机访问迭代器的多集元素。  
  
 Multiset 迭代器存储其关联的多集节点，反过来将存储到其关联的容器的句柄的句柄。 迭代器仅用于其关联的容器对象。 只要其关联的多集的节点是与某些多重集相关联，multiset 迭代器就保持有效。 此外，有效的迭代器是 dereferencable-可用来访问或更改元素值，它指定-，只要不等于`end()`。  
  
 擦除或删除元素调用析构函数作为其存储的值。 销毁容器清除所有元素。 因此，其元素类型是一个 ref 类的容器可确保任何元素生存期限超过容器。 但请注意，句柄的容器未`not`销毁它的元素。  
  
## <a name="requirements"></a>要求  
 **标头：** \<cliext/set >  
  
 **Namespace:** cliext  
  
## <a name="see-also"></a>请参阅  
 [hash_map (STL/CLR)](../dotnet/hash-map-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_multiset (STL/CLR)](../dotnet/hash-multiset-stl-clr.md)   
 [hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)   
 [映射 (STL/CLR)](../dotnet/map-stl-clr.md)   
 [多重集合](../dotnet/multiset-stl-clr.md)   
 [设置 (STL/CLR)](../dotnet/set-stl-clr.md)   
 [STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)