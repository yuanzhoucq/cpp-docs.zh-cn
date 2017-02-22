---
title: "multimap (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::multimap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/map> 标头 [STL/CLR]"
  - "<map> 标头 [STL/CLR]"
  - "multimap 类 [STL/CLR]"
ms.assetid: 3dfe329d-a078-462a-b050-7999ce6110ad
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# multimap (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述用于控制双向访问的变长元素序列的对象。  使用容器 `multimap` 管理用作 \(关闭\) 平衡的节点排序树的元素序列，每个存储一个元素。  元素包含一个键，排序序列和一映射值，为乘驾情况。  
  
 在如下解释 `GValue` 是相同的，如下所示：  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 其中：  
  
 同样，`GKey` 与 `Key` 相同，除非后者是 ref 类型，在这种情况下，它是 `Key^`。  
  
 同样，`GMapped` 与 `Mapped` 相同，除非后者是 ref 类型，在这种情况下，它是 `Mapped^`。  
  
## 语法  
  
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
  
#### 参数  
 键  
 受控序列中元素的键组件的类型。  
  
 已映射  
 受控序列中元素的附加组件的类型。  
  
## 成员  
  
|类型定义|说明|  
|----------|--------|  
|[multimap::const\_iterator](../dotnet/multimap-const-iterator-stl-clr.md)|受控序列的常量迭代器的类型。|  
|[multimap::const\_reference](../dotnet/multimap-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[multimap::const\_reverse\_iterator](../dotnet/multimap-const-reverse-iterator-stl-clr.md)|这种类型的常量为受控序列存储迭代器。|  
|[multimap::difference\_type](../dotnet/multimap-difference-type-stl-clr.md)|两个元素间的\(可能带符号\)距离的类型。|  
|[multimap::generic\_container](../dotnet/multimap-generic-container-stl-clr.md)|泛型接口的容器适配器类型。|  
|[multimap::generic\_iterator](../dotnet/multimap-generic-iterator-stl-clr.md)|有关容器的泛型接口的迭代器的类型。|  
|[multimap::generic\_reverse\_iterator](../dotnet/multimap-generic-reverse-iterator-stl-clr.md)|与容器的泛型接口一起使用的迭代器的类型。|  
|[multimap::generic\_value](../dotnet/multimap-generic-value-stl-clr.md)|有关容器的泛型接口的元素的类型。|  
|[multimap::iterator](../dotnet/multimap-iterator-stl-clr.md)|受控序列的迭代器的类型。|  
|[multimap::key\_compare](../dotnet/multimap-key-compare-stl-clr.md)|两个键的排序委托。|  
|[multimap::key\_type](../dotnet/multimap-key-type-stl-clr.md)|排序键的类型。|  
|[multimap::mapped\_type](../dotnet/multimap-mapped-type-stl-clr.md)|与每个键关联的映射值的类型。|  
|[multimap::reference](../dotnet/multimap-reference-stl-clr.md)|元素的引用的类型。|  
|[multimap::reverse\_iterator](../dotnet/multimap-reverse-iterator-stl-clr.md)|受控序列的反转迭代器的类型。|  
|[multimap::size\_type](../dotnet/multimap-size-type-stl-clr.md)|两个元素间的\(非负\)距离的类型。|  
|[multimap::value\_compare](../dotnet/multimap-value-compare-stl-clr.md)|两个元素值的排序委托。|  
|[multimap::value\_type](../dotnet/multimap-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|说明|  
|----------|--------|  
|[multimap::begin](../dotnet/multimap-begin-stl-clr.md)|指定受控序列的开头。|  
|[multimap::clear](../dotnet/multimap-clear-stl-clr.md)|移除所有元素。|  
|[multimap::count](../dotnet/multimap-count-stl-clr.md)|与指定键匹配的计数元素。|  
|[multimap::empty](../dotnet/multimap-empty-stl-clr.md)|测试元素是否存在。|  
|[multimap::end](../dotnet/multimap-end-stl-clr.md)|指定受控序列的末尾。|  
|[multimap::equal\_range](../dotnet/multimap-equal-range-stl-clr.md)|查找与指定键匹配的范围。|  
|[multimap::erase](../dotnet/multimap-erase-stl-clr.md)|移除指定位置处的元素。|  
|[multimap::find](../dotnet/multimap-find-stl-clr.md)|查找与指定键匹配的元素。|  
|[multimap::insert](../dotnet/multimap-insert-stl-clr.md)|添加元素。|  
|[multimap::key\_comp](../dotnet/multimap-key-comp-stl-clr.md)|复制两个键的排序委托。|  
|[multimap::lower\_bound](../dotnet/multimap-lower-bound-stl-clr.md)|查找与指定的键范围的开头。|  
|[multimap::make\_value](../dotnet/multimap-make-value-stl-clr.md)|构造一个值对象。|  
|[multimap::multimap](../dotnet/multimap-multimap-stl-clr.md)|构造容器对象。|  
|[multimap::rbegin](../dotnet/multimap-rbegin-stl-clr.md)|指定反转的受控序列的开头。|  
|[multimap::rend](../dotnet/multimap-rend-stl-clr.md)|指定反转的受控序列的末尾。|  
|[multimap::size](../dotnet/multimap-size-stl-clr.md)|计算元素的数量。|  
|[multimap::swap](../dotnet/multimap-swap-stl-clr.md)|交换两个容器的内容。|  
|[multimap::to\_array](../dotnet/multimap-to-array-stl-clr.md)|复制控制序列到新数组。|  
|[multimap::upper\_bound](../dotnet/multimap-upper-bound-stl-clr.md)|查找与指定键匹配的范围。|  
|[multimap::value\_comp](../dotnet/multimap-value-comp-stl-clr.md)|复制两个元素值的排序委托。|  
  
|运算符|说明|  
|---------|--------|  
|[multimap::operator\=](../dotnet/multimap-operator-assign-stl-clr.md)|替换控件序列。|  
|[operator\!\= \(multimap\)](../dotnet/operator-inequality-multimap-stl-clr.md)|确定 `multimap` 对象是否等与不等于另一 `multimap` 对象。|  
|[operator\< \(multimap\)](../dotnet/operator-less-than-multimap-stl-clr.md)|确定 `multimap` 对象是否小于另一 `multimap` 对象。|  
|[operator\<\= \(multimap\)](../dotnet/operator-less-or-equal-multimap-stl-clr.md)|确定一个 `multimap` 对象是否小于或等于另一个`multimap`对象。|  
|[operator\=\= \(multimap\)](../dotnet/operator-equality-multimap-stl-lr.md)|确定 `multimap` 对象是否等于另一 `multimap` 对象。|  
|[operator\> \(multimap\)](../dotnet/operator-greater-than-multimap-stl-clr.md)|确定 `multimap` 对象是否大于另一 `multimap` 对象。|  
|[operator\>\= \(multimap\)](../dotnet/operator-greater-or-equal-multimap-stl-clr.md)|确定一个 `multimap` 对象是否大于或等于另一个`multimap`对象。|  
  
## 接口  
  
|接口|说明|  
|--------|--------|  
|<xref:System.ICloneable>|复制对象。|  
|<xref:System.Collections.IEnumerable>|元素的序列。|  
|<xref:System.Collections.ICollection>|维护元素组。|  
|<xref:System.Collections.Generic.IEnumerable%601>|输入元素的序列。|  
|<xref:System.Collections.Generic.ICollection%601>|维护输入元素组。|  
|ITree\<键，值\>|维护泛型容器。|  
  
## 备注  
 对象对作为单独节点控制的序列分配并释放内存。  将元素插入到 \(近似\)平衡树， 通过更改节点间的链接保持有序，从不通过复制节点的内容到另一个节点上。  这表示您可以自由插入和移除元素，而不干扰的其余元素。  
  
 对象通过调用存储的 [multimap::key\_compare](../dotnet/multimap-key-compare-stl-clr.md) 类型的委托对象，对它控制的序列进行排序。  当在构造多重映射时，您可以指定该存储的委托对象；如果您不指定委托对象，默认是比较 `operator<(key_type, key_type)`。  通过调用成员函数访问该存储区的对象[multimap::key\_comp](../dotnet/multimap-key-comp-stl-clr.md)`()`。  
  
 此委托对象必须根据 [multimap::key\_type](../dotnet/multimap-key-type-stl-clr.md)键的类型，进行严格的弱序化。  这意味着，任何两键的 `X` 和 `Y`:  
  
 `key_comp()(X, Y)` 返回对每个调用相同的布尔值结果。  
  
 如果 `key_comp()(X, Y)` 为 true，则 `key_comp()(Y, X)` 必须是错误的。  
  
 如果 `key_comp()(X, Y)` 为 true，则 `X` 被视为 `Y`之前的排序。  
  
 如果 `!key_comp()(X, Y) && !key_comp()(Y, X)` 为 true，则 `X` 和 `Y` 是具有相同顺序。  
  
 在控制序列中，对优先于`Y` 的所有元素 `X`来说，`key_comp()(Y, X)` 为 false。\(对于默认委托对象，键值从来不会是降序排列。\)不同于类模板 [map](../dotnet/map-stl-clr.md)，模板类对象`multimap`不需要任何元素的键是唯一的。\(两个或多个键可以具有相同排序。\)  
  
 每个元素都包含一个键和一映射值。  序列以使查找、插入和删除任意元素的方式表示，序列的操作与元素的数量的对数成正比\(对数时间\)。  此外，插入元素不会使迭代器失效，移除元素仅会使指向已移除元素的迭代器失效。  
  
 多重映射支持双向迭代器，这意味着可以单步执行到给定的相邻元素迭代器指定控制在序列中的元素。  特定头节点对应于 [multimap::end](../dotnet/multimap-end-stl-clr.md)`()`返回的迭代器。  如果有，可以减小此迭代器达到控制序列中的最后一个元素。  您可以将多重映射迭代器增加到头节点，则将与 `end()`比较。  但是，您无法取消引用 `end()`返回的迭代器。  
  
 注意不可以直接引用基于多重映射的元素\-\-这要求一个随机访问迭代器。  
  
 multimap迭代器存储句柄与其关联多重映射节点，而后者存储句柄及其关联的容器。  只可以在与它们关联的容器对象上使用迭代器。  只要其与多重映射点与某个集，多个迭代器映射保持有效。  而且，有效的迭代器是可重复引用的\-\-可以用来访问或修改指定的元素值\-\-只要它不等于 `end()`。  
  
 调用析构函数清除或移除元素的存储值。  销毁容器会清除所有元素。  因此，元素类型为参考类的容器确保元素存在容器内。  但是，注意容器的处理执行销毁 `not` 元素。  
  
## 要求  
 **标头:** \<cliext\/map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_multimap](../dotnet/hash-multimap-stl-clr.md)   
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [map](../dotnet/map-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [集合](../dotnet/set-stl-clr.md)   
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)