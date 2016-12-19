---
title: "map (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/map> 标头 [STL/CLR]"
  - "<map> 标头 [STL/CLR]"
  - "map 类 [STL/CLR]"
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# map (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述用于控制双向访问的变长元素序列的对象。  使用容器 `map` 管理用作 \(关闭\) 平衡的节点排序树的元素序列，每个存储一个元素。  元素包含一个键，排序序列和一映射值，为乘驾情况。  
  
 在如下解释 `GValue` 是相同的，如下所示：  
  
 `Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`  
  
 其中：  
  
 同样，`GKey` 与 `Key` 相同，除非后者是 ref 类型，在这种情况下，它是 `Key^`。  
  
 同样，`GMapped` 与 `Mapped` 相同，除非后者是 ref 类型，在这种情况下，它是 `Mapped^`。  
  
## 语法  
  
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
  
#### 参数  
 键  
 受控序列中元素的键组件的类型。  
  
 已映射  
 受控序列中元素的值组件的类型。  
  
## 成员  
  
|类型定义|说明|  
|----------|--------|  
|[map::const\_iterator](../dotnet/map-const-iterator-stl-clr.md)|受控序列的常量迭代器的类型。|  
|[map::const\_reference](../dotnet/map-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[map::const\_reverse\_iterator](../dotnet/map-const-reverse-iterator-stl-clr.md)|这种类型的常量为受控序列存储迭代器。|  
|[map::difference\_type](../dotnet/map-difference-type-stl-clr.md)|两个元素间的\(可能带符号\)距离的类型。|  
|[map::generic\_container](../dotnet/map-generic-container-stl-clr.md)|泛型接口的容器适配器类型。|  
|[map::generic\_iterator](../dotnet/map-generic-iterator-stl-clr.md)|有关容器的泛型接口的迭代器的类型。|  
|[map::generic\_reverse\_iterator](../dotnet/map-generic-reverse-iterator-stl-clr.md)|与容器的泛型接口一起使用的迭代器的类型。|  
|[map::generic\_value](../dotnet/map-generic-value-stl-clr.md)|有关容器的泛型接口的元素的类型。|  
|[map::iterator](../dotnet/map-iterator-stl-clr.md)|受控序列的迭代器的类型。|  
|[map::key\_compare](../dotnet/map-key-compare-stl-clr.md)|两个键的排序委托。|  
|[map::key\_type](../dotnet/map-key-type-stl-clr.md)|排序键的类型。|  
|[map::mapped\_type](../dotnet/map-mapped-type-stl-clr.md)|与每个键关联的映射值的类型。|  
|[map::reference](../dotnet/map-reference-stl-clr.md)|元素的引用的类型。|  
|[map::reverse\_iterator](../dotnet/map-reverse-iterator-stl-clr.md)|受控序列的反转迭代器的类型。|  
|[map::size\_type](../dotnet/map-size-type-stl-clr.md)|两个元素间的\(非负\)距离的类型。|  
|[map::value\_compare](../dotnet/map-value-compare-stl-clr.md)|两个元素值的排序委托。|  
|[map::value\_type](../dotnet/map-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|说明|  
|----------|--------|  
|[map::begin](../dotnet/map-begin-stl-clr.md)|指定受控序列的开头。|  
|[map::clear](../dotnet/map-clear-stl-clr.md)|移除所有元素。|  
|[map::count](../dotnet/map-count-stl-clr.md)|与指定键匹配的计数元素。|  
|[map::empty](../dotnet/map-empty-stl-clr.md)|测试元素是否存在。|  
|[map::end](../dotnet/map-end-stl-clr.md)|指定受控序列的末尾。|  
|[map::equal\_range](../dotnet/map-equal-range-stl-clr.md)|查找与指定键匹配的范围。|  
|[map::erase](../dotnet/map-erase-stl-clr.md)|移除指定位置处的元素。|  
|[map::find](../dotnet/map-find-stl-clr.md)|查找与指定键匹配的元素。|  
|[map::insert](../dotnet/map-insert-stl-clr.md)|添加元素。|  
|[map::key\_comp](../dotnet/map-key-comp-stl-clr.md)|复制两个键的排序委托。|  
|[map::lower\_bound](../dotnet/map-lower-bound-stl-clr.md)|查找与指定的键范围的开头。|  
|[map::make\_value](../dotnet/map-make-value-stl-clr.md)|构造一个值对象。|  
|[map::map](../dotnet/map-map-stl-clr.md)|构造容器对象。|  
|[map::rbegin](../dotnet/map-rbegin-stl-clr.md)|指定反转的受控序列的开头。|  
|[map::rend](../dotnet/map-rend-stl-clr.md)|指定反转的受控序列的末尾。|  
|[map::size](../dotnet/map-size-stl-clr.md)|计算元素的数量。|  
|[map::swap](../dotnet/map-swap-stl-clr.md)|交换两个容器的内容。|  
|[map::to\_array](../dotnet/map-to-array-stl-clr.md)|复制控制序列到新数组。|  
|[map::upper\_bound](../dotnet/map-upper-bound-stl-clr.md)|查找与指定键匹配的范围。|  
|[map::value\_comp](../dotnet/map-value-comp-stl-clr.md)|复制两个元素值的排序委托。|  
  
|运算符|说明|  
|---------|--------|  
|[map::operator\=](../dotnet/map-operator-assign-stl-clr.md)|替换控件序列。|  
|[map::operator](../dotnet/map-operator-stl-clr.md)|映射到键映射及其关联的值。|  
|[operator\!\= \(map\)](../dotnet/operator-inequality-map-stl-clr.md)|确定 `map` 对象是否等与不等于另一 `map` 对象。|  
|[operator\< \(map\)](../dotnet/operator-less-than-map-stl-clr.md)|确定 `map` 对象是否小于另一 `map` 对象。|  
|[operator\<\= \(map\)](../dotnet/operator-less-or-equal-map-stl-clr.md)|确定一个 `map` 对象是否小于或等于另一个`map`对象。|  
|[operator\=\= \(map\)](../dotnet/operator-equality-map-stl-clr.md)|确定 `map` 对象是否等于另一 `map` 对象。|  
|[operator\> \(map\)](../dotnet/operator-greater-than-map-stl-clr.md)|确定 `map` 对象是否大于另一 `map` 对象。|  
|[operator\>\= \(map\)](../dotnet/operator-greater-or-equal-map-stl-clr.md)|确定一个 `map` 对象是否大于或等于另一个`map`对象。|  
  
## 接口  
  
|接口|说明|  
|--------|--------|  
|<xref:System.ICloneable>|复制对象。|  
|<xref:System.Collections.IEnumerable>|元素的序列。|  
|<xref:System.Collections.ICollection>|维护元素组。|  
|<xref:System.Collections.Generic.IEnumerable%601>|输入元素的序列。|  
|<xref:System.Collections.Generic.ICollection%601>|维护输入元素组。|  
|<xref:System.Collections.Generic.IDictionary%602>|维护{键，值}对的组。|  
|ITree\<键，值\>|维护泛型容器。|  
  
## 备注  
 对象对作为单独节点控制的序列分配并释放内存。  将元素插入到 \(近似\)平衡树， 通过更改节点间的链接保持有序，从不通过复制节点的内容到另一个节点上。  这表示您可以自由插入和移除元素，而不干扰的其余元素。  
  
 对象通过调用存储的 [map::key\_compare](../dotnet/map-key-compare-stl-clr.md) 类型的委托对象，对它控制的序列进行排序。  当在构造集合时，您可以指定该存储的委托对象；如果您不指定委托对象，默认是比较 `operator<(key_type, key_type)`。  通过调用成员函数访问该存储区的对象[map::key\_comp](../dotnet/map-key-comp-stl-clr.md)`()`。  
  
 此委托对象必须根据 [map::key\_type](../dotnet/map-key-type-stl-clr.md)键的类型，进行严格的弱序化。  这意味着，任何两键的 `X` 和 `Y`:  
  
 `key_comp()(X, Y)` 返回对每个调用相同的布尔值结果。  
  
 如果 `key_comp()(X, Y)` 为 true，则 `key_comp()(Y, X)` 必须是错误的。  
  
 如果 `key_comp()(X, Y)` 为 true，则 `X` 被视为 `Y`之前的排序。  
  
 如果 `!key_comp()(X, Y) && !key_comp()(Y, X)` 为 true，则 `X` 和 `Y` 是具有相同顺序。  
  
 在控制序列中，对优先于`Y` 的所有元素 `X`来说，`key_comp()(Y, X)` 为 false。\(对于默认委托对象，键值从来不会是降序排列。\)不同于类模板 [map](../dotnet/map-stl-clr.md)，模板类对象`map`不需要任何元素的键是唯一的。\(两个或多个键可以具有相同排序。\)  
  
 每个元素都包含一个键和一映射值。  序列以使查找、插入和删除任意元素的方式表示，序列的操作与元素的数量的对数成正比\(对数时间\)。  此外，插入元素不会使迭代器失效，移除元素仅会使指向已移除元素的迭代器失效。  
  
 集合支持双向迭代器，这意味着可以单步执行到给定的相邻元素迭代器指定控制在序列中的元素。  特定头节点对应于 [map::end](../dotnet/map-end-stl-clr.md)`()`返回的迭代器。  如果有，可以减小此迭代器达到控制序列中的最后一个元素。  您可以将集合迭代器增加到头节点，则将与 `end()`比较。  但是，您无法取消引用 `end()`返回的迭代器。  
  
 注意不可以直接引用基于数字的集合的元素\-\-这要求一个随机访问迭代器。  
  
 集合迭代器存储其关联集合节点的句柄，而后者存储其关联的容器的句柄。  只可以在与它们关联的容器对象上使用迭代器。  只要关联集合节点与某些集合关联，迭代器集合保持有效。  而且，有效的迭代器是可重复引用的\-\-可以用来访问或修改指定的元素值\-\-只要它不等于 `end()`。  
  
 调用析构函数清除或移除元素的存储值。  销毁容器会清除所有元素。  因此，元素类型为参考类的容器确保元素存在容器内。  但是，注意容器的处理执行销毁 `not` 元素。  
  
## 要求  
 **标头:** \<cliext\/map\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [map](../dotnet/map-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [集合](../dotnet/set-stl-clr.md)   
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)