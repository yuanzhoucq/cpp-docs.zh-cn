---
title: "hash_multiset (STL/CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "cliext::hash_multiset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "<cliext/hash_set> 标头 [STL/CLR]"
  - "<hash_set> 标头 [STL/CLR]"
  - "hash_multiset 类 [STL/CLR]"
ms.assetid: 8462bd21-6829-4dd3-ac81-c42d6fdf92f0
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# hash_multiset (STL/CLR)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此模板类描述用于控制双向访问的变长元素序列的对象。  使用容器 `hash_multiset` 管理元素序列用作哈希表，每个表项目存储节点的双向链接列表要和每个节点存储的元素。  值每个元素对排序序列用作键。  
  
 在如下描述，`GValue` 与 `GKey`相同，反之，与 `Key` 相同，除非后者是引用类型，在这种情况下，它是 `Key^`。  
  
## 语法  
  
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
  
#### 参数  
 键  
 受控序列中元素的键组件的类型。  
  
## 成员  
  
|类型定义|说明|  
|----------|--------|  
|[hash\_multiset::const\_iterator](../dotnet/hash-multiset-const-iterator-stl-clr.md)|受控序列的常量迭代器的类型。|  
|[hash\_multiset::const\_reference](../dotnet/hash-multiset-const-reference-stl-clr.md)|元素的常量引用的类型。|  
|[hash\_multiset::const\_reverse\_iterator](../dotnet/hash-multiset-const-reverse-iterator-stl-clr.md)|这种类型的常量为受控序列存储迭代器。|  
|[hash\_multiset::difference\_type](../dotnet/hash-multiset-difference-type-stl-clr.md)|两个元素间的\(可能带符号\)距离的类型。|  
|[hash\_multiset::generic\_container](../dotnet/hash-multiset-generic-container-stl-clr.md)|泛型接口的容器适配器类型。|  
|[hash\_multiset::generic\_iterator](../dotnet/hash-multiset-generic-iterator-stl-clr.md)|有关容器的泛型接口的迭代器的类型。|  
|[hash\_multiset::generic\_reverse\_iterator](../dotnet/hash-multiset-generic-reverse-iterator-stl-clr.md)|与容器的泛型接口一起使用的迭代器的类型。|  
|[hash\_multiset::generic\_value](../dotnet/hash-multiset-generic-value-stl-clr.md)|有关容器的泛型接口的元素的类型。|  
|[hash\_multiset::hasher](../dotnet/hash-multiset-hasher-stl-clr.md)|键的哈希委托。|  
|[hash\_multiset::iterator](../dotnet/hash-multiset-iterator-stl-clr.md)|受控序列的迭代器的类型。|  
|[hash\_multiset::key\_compare](../dotnet/hash-multiset-key-compare-stl-clr.md)|两个键的排序委托。|  
|[hash\_multiset::key\_type](../dotnet/hash-multiset-key-type-stl-clr.md)|排序键的类型。|  
|[hash\_multiset::reference](../dotnet/hash-multiset-reference-stl-clr.md)|元素的引用的类型。|  
|[hash\_multiset::reverse\_iterator](../dotnet/hash-multiset-reverse-iterator-stl-clr.md)|受控序列的反转迭代器的类型。|  
|[hash\_multiset::size\_type](../dotnet/hash-multiset-size-type-stl-clr.md)|两个元素间的\(非负\)距离的类型。|  
|[hash\_multiset::value\_compare](../dotnet/hash-multiset-value-compare-stl-clr.md)|两个元素值的排序委托。|  
|[hash\_multiset::value\_type](../dotnet/hash-multiset-value-type-stl-clr.md)|元素的类型。|  
  
|成员函数|说明|  
|----------|--------|  
|[hash\_multiset::begin](../dotnet/hash-multiset-begin-stl-clr.md)|指定受控序列的开头。|  
|[hash\_multiset::bucket\_count](../dotnet/hash-multiset-bucket-count-stl-clr.md)|统计存储桶数。|  
|[hash\_multiset::clear](../dotnet/hash-multiset-clear-stl-clr.md)|移除所有元素。|  
|[hash\_multiset::count](../dotnet/hash-multiset-count-stl-clr.md)|与指定键匹配的计数元素。|  
|[hash\_multiset::empty](../dotnet/hash-multiset-empty-stl-clr.md)|测试元素是否存在。|  
|[hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)|指定受控序列的末尾。|  
|[hash\_multiset::equal\_range](../dotnet/hash-multiset-equal-range-stl-clr.md)|查找与指定键匹配的范围。|  
|[hash\_multiset::erase](../dotnet/hash-multiset-erase-stl-clr.md)|移除指定位置处的元素。|  
|[hash\_multiset::find](../dotnet/hash-multiset-find-stl-clr.md)|查找与指定键匹配的元素。|  
|[hash\_multiset::hash\_delegate](../dotnet/hash-multiset-hash-delegate-stl-clr.md)|拷贝键的哈希委托。|  
|[hash\_multiset::hash\_multiset](../dotnet/hash-multiset-hash-multiset-stl-clr.md)|构造容器对象。|  
|[hash\_multiset::insert](../dotnet/hash-multiset-insert-stl-clr.md)|添加元素。|  
|[hash\_multiset::key\_comp](../dotnet/hash-multiset-key-comp-stl-clr.md)|复制两个键的排序委托。|  
|[hash\_multiset::load\_factor](../dotnet/hash-multiset-load-factor-stl-clr.md)|对每个存储桶的平均元素数进行计数。|  
|[hash\_multiset::lower\_bound](../dotnet/hash-multiset-lower-bound-stl-clr.md)|查找与指定的键范围的开头。|  
|[hash\_multiset::make\_value](../dotnet/hash-multiset-make-value-stl-clr.md)|构造一个值对象。|  
|[hash\_multiset::max\_load\_factor](../dotnet/hash-multiset-max-load-factor-stl-clr.md)|获取或设置每个存储桶的最多元素数。|  
|[hash\_multiset::rbegin](../dotnet/hash-multiset-rbegin-stl-clr.md)|指定反转的受控序列的开头。|  
|[hash\_multiset::rehash](../dotnet/hash-multiset-rehash-stl-clr.md)|重新生成哈希表。|  
|[hash\_multiset::rend](../dotnet/hash-multiset-rend-stl-clr.md)|指定反转的受控序列的末尾。|  
|[hash\_multiset::size](../dotnet/hash-multiset-size-stl-clr.md)|计算元素的数量。|  
|[hash\_multiset::swap](../dotnet/hash-multiset-swap-stl-clr.md)|交换两个容器的内容。|  
|[hash\_multiset::to\_array](../dotnet/hash-multiset-to-array-stl-clr.md)|复制控制序列到新数组。|  
|[hash\_multiset::upper\_bound](../dotnet/hash-multiset-upper-bound-stl-clr.md)|查找与指定键匹配的范围。|  
|[hash\_multiset::value\_comp](../dotnet/hash-multiset-value-comp-stl-clr.md)|复制两个元素值的排序委托。|  
  
|运算符|说明|  
|---------|--------|  
|[hash\_multiset::operator\=](../dotnet/hash-multiset-operator-assign-stl-clr.md)|替换控件序列。|  
  
## 接口  
  
|接口|说明|  
|--------|--------|  
|<xref:System.ICloneable>|复制对象。|  
|<xref:System.Collections.IEnumerable>|元素的序列。|  
|<xref:System.Collections.ICollection>|维护元素组。|  
|<xref:System.Collections.Generic.IEnumerable%601>|输入元素的序列。|  
|<xref:System.Collections.Generic.ICollection%601>|维护输入元素组。|  
|IHashKey\<值，\>|维护泛型容器。|  
  
## 备注  
 对象将它控制序列中未使用助记域，当一双向链接列表的各个节点。  若要加快访问，对象还维护着指针到列表 \(哈希表\)，有效管理整个列表为子表序列或存储桶的更改长度数组。  将元素插入到 \(近似\)平衡树， 通过更改节点间的链接保持有序，从不通过复制节点的内容到另一个节点上。  这表示您可以自由插入和移除元素，而不干扰的其余元素。  
  
 对象通过调用存储的 [hash\_set::key\_compare](../dotnet/hash-set-key-compare-stl-clr.md) 类型的委托对象，对它控制的每个桶进行排序。  当在构造哈希集合时，您可以指定该存储的委托对象；如果您不指定委托对象，默认是比较 `operator<=(key_type, key_type)`。  
  
 通过调用成员函数访问存储的委托对象`()`。[hash\_set::key\_comp](../dotnet/hash-set-key-comp-stl-clr.md) 此委托对象必须定义排序等效类型之间 [hash\_set::key\_type](../dotnet/hash-set-key-type-stl-clr.md)键。  这意味着，任何两键的 `X` 和 `Y`:  
  
 `key_comp()(X, Y)` 返回对每个调用相同的布尔值结果。  
  
 如果 `key_comp()(X, Y) && key_comp()(Y, X)` 为 true，则 `X` 和 `Y` 是具有相同顺序。  
  
 的行为与 `operator<=(key_type, key_type)`、`operator>=(key_type, key_type)` 或 `operator==(key_type, key_type)` 中的所有顺序的规则定义 eqivalent 顺序。  
  
 注意确保密钥容器只具有相同订单的元素 \(和散列为相同值，整数\) 在存储桶中是连续的。  不同于类模板 [hash\_set](../dotnet/hash-set-stl-clr.md)，模板类对象`hash_multiset`不需要任何元素的键是唯一的。\(两个或多个键可以具有相同排序。\)  
  
 对象确定哪个存储桶。应该通过调用类型 [hash\_set::hasher](../dotnet/hash-set-hasher-stl-clr.md)一个存储委托对象包含特定订单的键。  通过调用成员函数 [hash\_set::hash\_delegate](../dotnet/hash-set-hash-delegate-stl-clr.md)`()` 获取依赖于键值的整数值访问该存储区的对象。  当在构造哈希集合时，您可以指定该存储的委托对象；如果您不指定委托对象，默认是比较 `System::Object::hash_value(key_type)`。  这意味着，任何键的 `X` 和 `Y`:  
  
 `hash_delegate()(X)` 返回对每个调用相同的整形结果。  
  
 如果 `X` 和 `Y` 具有相同订单，则 `hash_delegate()(X)` 应返回整数结果与 `hash_delegate()(Y)`相同。  
  
 每个元素同时用键和值。  该序列表示的方式，允许查找，插入和去除的任意元素与多个操作独立于序列中的元素数目（固定时间）的 \- 至少在最好的情况下。  此外，插入元素不会使迭代器失效，移除元素仅会使指向已移除元素的迭代器失效。  
  
 如果哈希值不是统一分发，但是，哈希表可以降低。  非常\-\-对于始终返回相同值的哈希函数\-\-查找、插入和删除的元素数成比例在序列 \(线性时间\)。  容器竭力选择合理的哈希函数、平均存储桶大小和 Hashtable 大小 \(存储桶的总数\)，但是，您可以重写其中一个或所有这些选择。  例如，参见，函数和 [hash\_set::max\_load\_factor](../dotnet/hash-set-max-load-factor-stl-clr.md) [hash\_set::rehash](../dotnet/hash-set-rehash-stl-clr.md)。  
  
 哈希集合支持双向迭代器，这意味着可以单步执行到给定的相邻元素迭代器指定控制在序列中的元素。  特定头节点对应于 [hash\_multiset::end](../dotnet/hash-multiset-end-stl-clr.md)`()`返回的迭代器。  如果有，可以减小此迭代器达到控制序列中的最后一个元素。  您可以将哈希集合迭代器增加到头节点，则将与 `end()`比较。  但是，您无法取消引用 `end()`返回的迭代器。  
  
 注意不可以直接引用基于数字的哈希集合的元素\-\-这要求一个随机访问迭代器。  
  
 hash\_multiset 迭代器存储句柄与其关联 hash\_multiset 节点，而后者存储句柄及其关联的容器。  只可以在与它们关联的容器对象上使用迭代器。  只要其关联 hash\_multiset 节点与某些 hash\_multiset，hash\_multiset 迭代器仍然有效。  而且，有效的迭代器是可重复引用的\-\-可以用来访问或修改指定的元素值\-\-只要它不等于 `end()`。  
  
 调用析构函数清除或移除元素的存储值。  销毁容器会清除所有元素。  因此，元素类型为参考类的容器确保元素存在容器内。  但是，注意容器的处理执行销毁 `not` 元素。  
  
## 要求  
 **标头:** \<cliext\/hash\_set\>  
  
 **命名空间:** cliext  
  
## 请参阅  
 [hash\_map](../dotnet/hash-map-stl-clr.md)   
 [hash\_multiset](../dotnet/hash-multiset-stl-clr.md)   
 [hash\_set](../dotnet/hash-set-stl-clr.md)   
 [map](../dotnet/map-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [multiset](../dotnet/multiset-stl-clr.md)   
 [集合](../dotnet/set-stl-clr.md)   
 [STL\/CLR 库](../dotnet/stl-clr-library-reference.md)