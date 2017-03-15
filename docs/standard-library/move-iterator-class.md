---
title: "move_iterator 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.move_iterator
- move_iterator
- iterator/std::move_iterator
- std::move_iterator
dev_langs:
- C++
helpviewer_keywords:
- move_iterator class
ms.assetid: a5e5cdd8-a264-4c6b-9f9c-68b0e8edaab7
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 2d05749ba2837a3879c91886b9266de47dd2ece6
ms.openlocfilehash: b689b6363fbe7eff8d34d709f451e46bf9a92537
ms.lasthandoff: 02/24/2017

---
# <a name="moveiterator-class"></a>move_iterator 类
类模板 `move_iterator` 是迭代器的包装器。 move_iterator 的行为与其包装（存储）的迭代器相同，但它将存储的迭代器的取消引用运算符转换为右值引用，将副本转换为移动。 有关详细信息，请参阅[右值引用声明符：&&](../cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## <a name="syntax"></a>语法  
```
class move_iterator;  
```
## <a name="remarks"></a>备注  
 模板类描述在行为上与迭代器类似（取消引用时除外）的对象。 它存储 `Iterator` 类型的随机访问迭代器，可通过成员函数 `base``()` 访问此迭代器。 对于 `move_iterator` 的所有操作将直接对存储的迭代器执行，但 `operator*` 的结果将隐式强制转换为 `value_type&&` 以进行右值引用。  
  
 `move_iterator` 可以进行包装的迭代器未定义的操作。 不应使用这些操作。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[move_iterator](#move_iterator__move_iterator)|`move_iterator` 类型的对象的构造函数。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[move_iterator::iterator_type](#move_iterator__iterator_type)|模板参数 `RandomIterator` 的同义词。|  
|[move_iterator::iterator_category](#move_iterator__iterator_category)|同一名称的较长 `typename` 表达式的同义词，`iterator_category` 用于标识迭代器的常规功能。|  
|[move_iterator::value_type](#move_iterator__value_type)|同一名称的较长 `typename` 表达式的同义词，`value_type` 用于描述迭代器元素的类型。|  
|[move_iterator::difference_type](#move_iterator__difference_type)|同一名称的较长 `typename` 表达式的同义词，`difference_type` 用于描述表示元素间的差值所需的整型。|  
|[move_iterator::pointer](#move_iterator__pointer)|模板参数 `RandomIterator` 的同义词。|  
|[move_iterator::reference](#move_iterator__reference)|`rvalue` 引用 `value_type&&` 的同义词。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[move_iterator::base](#move_iterator__base)|此成员函数返回该 `move_iterator` 包装的存储迭代器。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[move_iterator::operator*](#move_iterator__operator_star)|返回 `(reference)*``base``().`|  
|[move_iterator::operator++](#move_iterator__operator_add_add)|递增存储的迭代器。 确切行为取决于它是前置递增操作还是后置递增操作。|  
|[move_iterator::operator--](#move_iterator__operator--)|递减存储的迭代器。 确切行为取决于它是前置递减操作还是后置递减操作。|  
|[move_iterator::operator-&gt;](#move_iterator__operator-_gt_)|返回 `&**this`。|  
|[move_iterator::operator-](#move_iterator__operator-)|通过先从当前位置减去右值来返回 `move_iterator(*this) -=`。|  
|[move_iterator::operator[]](#move_iterator__operator_at)|返回 `(reference)*(*this + off)`。 允许你指定相对于当前基础位置的偏移量以获取位于偏移位置的值。|  
|[move_iterator::operator+](#move_iterator__operator_add)|返回 `move_iterator(*this) +=`值。 允许你向基础位置添加偏移量以获取位于偏移位置的值。|  
|[move_iterator::operator+=](#move_iterator__operator_add_eq)|将右值添加到存储的迭代器，并返回 `*this`。|  
|[move_iterator::operator-=](#move_iterator__operator-_eq)|从存储的迭代器减去右值，并返回 `*this`。|  
  
## <a name="requirements"></a>要求  
 **标头：** \<iterator>  
  
 **命名空间：** std  
  
##  <a name="a-namemoveiteratorbasea--moveiteratorbase"></a><a name="move_iterator__base"></a>  move_iterator::base  
 返回此 `move_iterator` 存储的迭代器。  
  
```
RandomIterator base() const;
```  
  
### <a name="remarks"></a>备注  
 成员函数将返回存储的迭代器。  
  
##  <a name="a-namemoveiteratordifferencetypea--moveiteratordifferencetype"></a><a name="move_iterator__difference_type"></a>  move_iterator::difference_type  
 类型 `difference_type` 是基于迭代器特征 `difference_type` 的 `move_iterator``typedef`，可与其互换使用。  
  
```
typedef typename iterator_traits<RandomIterator>::difference_type difference_type;
```    
  
### <a name="remarks"></a>备注  
 该类型是迭代器特征 `typename iterator_traits<RandomIterator>::pointer` 的同义词。  
  
##  <a name="a-namemoveiteratoriteratorcategorya--moveiteratoriteratorcategory"></a><a name="move_iterator__iterator_category"></a>  move_iterator::iterator_category  
 类型 `iterator_category` 是基于迭代器特征 `iterator_category` 的 `move_iterator``typedef`，可与其互换使用。  
  
```
typedef typename iterator_traits<RandomIterator>::iterator_category  iterator_category;
```    
  
### <a name="remarks"></a>备注  
 该类型是迭代器特征 `typename iterator_traits<RandomIterator>::iterator_category` 的同义词。  
  
##  <a name="a-namemoveiteratoriteratortypea--moveiteratoriteratortype"></a><a name="move_iterator__iterator_type"></a>  move_iterator::iterator_type  
 类型 `iterator_type` 基于类模板 `move_iterator` 的模板参数 `RandomIterator`，并且可在其位置互换使用。  
  
```
typedef RandomIterator iterator_type;
```  
  
### <a name="remarks"></a>备注  
 类型是模板参数 `RandomIterator` 的同义词。  
  
##  <a name="a-namemoveiteratormoveiteratora--moveiteratormoveiterator"></a><a name="move_iterator__move_iterator"></a>  move_iterator::move_iterator  
 构造一个移动迭代器。 使用参数作为存储的迭代器。  
  
```
move_iterator();
explicit move_iterator(RandomIterator right);
template <class Type>
move_iterator(const move_iterator<Type>& right);
```  
  
### <a name="parameters"></a>参数  
 `right`  
 将用作存储的迭代器的迭代器。  
  
### <a name="remarks"></a>备注  
 第一个构造函数用其默认构造函数初始化存储的迭代器。 剩余构造函数用 `base.base()` 初始化存储的迭代器。  
  
##  <a name="a-namemoveiteratoroperatoraddeqa--moveiteratoroperator"></a><a name="move_iterator__operator_add_eq"></a>  move_iterator::operator+=  
 将某一偏移量添加到存储迭代器，以便存储迭代器指向新的当前位置处的元素。 然后，运算符移动新的当前元素。  
  
```
move_iterator& operator+=(difference_type _Off);
```  
  
### <a name="parameters"></a>参数  
 `_Off`  
 将偏移量添加到当前位置，以确定新的当前位置。  
  
### <a name="return-value"></a>返回值  
 返回新的当前元素。  
  
### <a name="remarks"></a>备注  
 运算符将向存储迭代器添加 `_Off`。 然后返回 `*this`。  
  
##  <a name="a-namemoveiteratoroperator-eqa--moveiteratoroperator-"></a><a name="move_iterator__operator-_eq"></a>  move_iterator::operator-=  
 在前面的指定数目的元素之间移动。 此运算符会从存储的迭代器中减去一个偏移量。  
  
```
move_iterator& operator-=(difference_type _Off);
```  
  
### <a name="parameters"></a>参数  
  
### <a name="remarks"></a>备注  
 运算符计算 `*this += -_Off`。 然后返回 `*this`。  
  
##  <a name="a-namemoveiteratoroperatoraddadda--moveiteratoroperator"></a><a name="move_iterator__operator_add_add"></a>  move_iterator::operator++  
 递增属于此 `move_iterator.` 的存储迭代器。当前元素通过后置递增运算符进行访问。 下一个元素通过前置递增运算符进行访问。  
  
```
move_iterator& operator++();
move_iterator operator++(int);
```  
  
### <a name="parameters"></a>参数  
  
### <a name="remarks"></a>备注  
 第一个（前置递增）运算符将递增存储迭代器。 然后返回 `*this`。  
  
 第二个（后置递增）运算符生成 `*this` 的副本，并计算 `++*this`。 然后返回该副本。  
  
##  <a name="a-namemoveiteratoroperatoradda--moveiteratoroperator"></a><a name="move_iterator__operator_add"></a>move_iterator::operator+  
 返回由任意数量的元素提升的迭代器位置。  
  
```
move_iterator operator+(difference_type _Off) const;
```  
  
### <a name="parameters"></a>参数  
  
### <a name="remarks"></a>备注  
 运算符返回 `move_iterator(*this) +=` `_Off`。  
  
##  <a name="a-namemoveiteratoroperatorata--moveiteratoroperator"></a><a name="move_iterator__operator_at"></a>move_iterator::operator[]  
 允许数组索引对 `move iterator` 范围内的元素进行访问。  
  
```
reference operator[](difference_type _Off) const;
```  
  
### <a name="parameters"></a>参数  
  
### <a name="remarks"></a>备注  
 运算符返回 `(reference)*(*this + _Off)`。  
  
##  <a name="a-namemoveiteratoroperator--a--moveiteratoroperator--"></a><a name="move_iterator__operator--"></a>move_iterator::operator--  
 前置减量和后置减量成员运算符对存储的迭代器执行减量运算。  
  
```
move_iterator& operator--();
move_iterator operator--();
```  
  
### <a name="parameters"></a>参数  
  
### <a name="remarks"></a>备注  
 第一个成员运算符（前置减量）对存储的迭代器执行减量运算。 然后返回 `*this`。  
  
 第二个（后置减量）运算符生成 `*this` 的副本，并计算 `--*this` 的结果。 然后返回该副本。  
  
##  <a name="a-namemoveiteratoroperator-a--moveiteratoroperator-"></a><a name="move_iterator__operator-"></a>move_iterator::operator-  
 递减存储的迭代器，并返回指示的值。  
  
```
move_iterator operator-(difference_type _Off) const;
```  
  
### <a name="parameters"></a>参数  
  
### <a name="remarks"></a>备注  
 运算符返回 `move_iterator(*this) -= _Off`。  
  
##  <a name="a-namemoveiteratoroperatorstara--moveiteratoroperator"></a><a name="move_iterator__operator_star"></a>move_iterator::operator*  
 取消对存储的迭代器的引用，并返回值。 此行为类似 `rvalue reference` 并执行移动赋值。 该运算符会将当前元素从基迭代器中传输出去。 其后面的元素将成为新的当前元素。  
  
```
reference operator*() const;
```  
  
### <a name="remarks"></a>备注  
 运算符返回 `(reference)*``base``()`。  
  
##  <a name="a-namemoveiteratoroperator-gta--moveiteratoroperator-gt"></a><a name="move_iterator__operator-_gt_"></a>move_iterator::operator-&gt;  
 与常规 `RandomIterator``operator->` 类似，它提供对属于当前元素的字段的访问权限。  
  
```
pointer operator->() const;
```  
  
### <a name="remarks"></a>备注  
 运算符返回 `&**this`。  
  
##  <a name="a-namemoveiteratorpointera--moveiteratorpointer"></a><a name="move_iterator__pointer"></a>  move_iterator::pointer  
 类型 `pointer` 是基于 `move_iterator` 的随机迭代器 `RandomIterator` 的 `typedef`，可互换使用。  
  
```
typedef RandomIterator  pointer;
```    
  
### <a name="remarks"></a>备注  
 该类型是 `RandomIterator` 的同义词。  
  
##  <a name="a-namemoveiteratorreferencea--moveiteratorreference"></a><a name="move_iterator__reference"></a>  move_iterator::reference  
 `reference` 类是基于 `move_iterator` 的 `value_type&&` 的 `typedef`，可与 `value_type&&` 交换使用。  
  
```
typedef value_type&& reference;
```    
  
### <a name="remarks"></a>备注  
 类是 `value_type&&` 的同义词，即右值引用。  
  
##  <a name="a-namemoveiteratorvaluetypea--moveiteratorvaluetype"></a><a name="move_iterator__value_type"></a>  move_iterator::value_type  
 类型 `value_type` 是基于迭代器特征 `value_type` 的 `move_iterator``typedef`，可与其互换使用。  
  
```
typedef typename iterator_traits<RandomIterator>::value_type   value_type;
```    
  
### <a name="remarks"></a>备注  
 该类型是迭代器特征 `typename iterator_traits<RandomIterator>::value_type` 的同义词。  
  
## <a name="see-also"></a>另请参阅  
 [\<iterator>](../standard-library/iterator.md)   
 [Lvalues 和 Rvalues](../cpp/lvalues-and-rvalues-visual-cpp.md)   
 [移动构造函数和移动赋值运算符 (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)   
 [C++ 标准库参考](../standard-library/cpp-standard-library-reference.md)





