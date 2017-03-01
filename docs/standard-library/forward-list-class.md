---
title: "forward_list 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std::forward_list
- forward_list
- forward_list/std::forward_list
- std.forward_list
dev_langs:
- C++
helpviewer_keywords:
- forward_list class
ms.assetid: 89a3b805-ab60-4858-b772-5855130c11b1
caps.latest.revision: 25
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 198522429f7337a4ee3e5d5cb29ab408950618d5
ms.lasthandoff: 02/24/2017

---
# <a name="forwardlist-class"></a>forward_list 类
描述用于控制变长元素序列的对象。 序列存储为节点的单向链接列表，其中每个节点都包含 `Type` 类型的成员。  
  
## <a name="syntax"></a>语法  
  
```  
template <class Type,   
    class Allocator = allocator<Type>>  
class forward_list   
```  
  
#### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Type`|要存储在 forward_list 中的元素数据类型。|  
|`Allocator`|存储的分配器对象，用于封装有关 forward_list 的内存分配和解除分配的详细信息。 此参数可选。 默认值为 allocator< `Type`>。|  
  
## <a name="remarks"></a>备注  
 `forward_list` 对象通过 `Allocator` 类的存储对象（基于 [allocator 类](../standard-library/allocator-class.md)，通常称为 `std::allocator)`）分配和释放它所控制序列的存储。 有关详细信息，请参阅[分配器](../standard-library/allocators.md)。 分配器对象必须与 `allocator` 模板类的对象具有相同的外部接口。  
  
> [!NOTE]
>  分配容器对象时，不会复制存储的分配器对象。  
  
 通过 `forward_list` 擦除迭代器、指针和引用所控制序列的元素时，这些迭代器、指针和引用可能失效。 通过 `forward_list` 对受控序列执行插入和接合操作不会使迭代器失效。  
  
 调用 [forward_list::insert_after](#forward_list__insert_after)（它是可调用构造函数 `Type(const  T&)` 的唯一成员函数）时，可能会添加受控序列。 `forward_list` 也可能调用移动构造函数。 如果此类表达式引发异常，则容器对象不插入任何新元素，并重新引发该异常。 因此，发生这类异常时，模板类 `forward_list` 的对象仍处于已知状态。  
  
### <a name="constructors"></a>构造函数  
  
|||  
|-|-|  
|[forward_list](#forward_list__forward_list)|构造 `forward_list` 类型的对象。|  
  
### <a name="typedefs"></a>Typedef  
  
|||  
|-|-|  
|[allocator_type](#forward_list__allocator_type)|一种类型，用于表示转发列表对象的分配器类。|  
|[const_iterator](#forward_list__const_iterator)|一种类型，用于为转发列表提供常量迭代器。|  
|[const_pointer](#forward_list__const_pointer)|一种类型，用于提供指向转发列表中的 `const` 元素的指针。|  
|[const_reference](#forward_list__const_reference)|一种类型，用于提供对转发列表中元素的常量引用。|  
|[difference_type](#forward_list__difference_type)|一种有符号整数类型，可用于表示转发列表中某个范围类迭代器所指向元素之间的元素数目。|  
|[Iterator](#forward_list__iterator)|一种类型，用于为转发列表提供迭代器。|  
|[pointer](#forward_list__pointer)|一种类型，用于提供指向转发列表中元素的指针。|  
|[reference](#forward_list__reference)|一种类型，用于提供对转发列表中元素的引用。|  
|[size_type](#forward_list__size_type)|一种类型，用于表示两个元素之间的无符号距离。|  
|[value_type](#forward_list__value_type)|一种类型，用于表示转发列表中存储的元素的类型。|  
  
### <a name="member-functions"></a>成员函数  
  
|||  
|-|-|  
|[assign](#forward_list__assign)|清除转发列表中的元素，并将一组新的元素复制到目标转发列表。|  
|[before_begin](#forward_list__before_begin)|返回寻址转发列表中第一个元素之前的位置的迭代器。|  
|[begin](#forward_list__begin)|返回寻址转发列表中第一个元素的迭代器。|  
|[cbefore_begin](#forward_list__cbefore_begin)|返回寻址转发列表中第一个元素之前的位置的常量迭代器。|  
|[cbegin](#forward_list__cbegin)|返回寻址转发列表中第一个元素的常量迭代器。|  
|[cend](#forward_list__cend)|返回寻址转发列表中最后一个元素之后的位置的常量迭代器。|  
|[clear](#forward_list__clear)|清除转发列表中的所有元素。|  
|[emplace_after](#forward_list__emplace_after)|在指定位置之后移动构造新元素。|  
|[emplace_front](#forward_list__emplace_front)|在列表的起始位置添加一个就地构造的元素。|  
|[empty](#forward_list__empty)|测试转发列表是否为空。|  
|[end](#forward_list__end)|返回寻址转发列表中最后一个元素之后的位置的迭代器。|  
|[erase_after](#forward_list__erase_after)|删除转发列表中指定位置之后的元素。|  
|[front](#forward_list__front)|返回对转发列表中第一个元素的引用。|  
|[get_allocator](#forward_list__get_allocator)|返回用于构造转发列表的分配器对象的一个副本。|  
|[insert_after](#forward_list__insert_after)|在转发列表中的指定位置之后添加元素。|  
|[max_size](#forward_list__max_size)|返回转发列表的最大长度。|  
|[merge](#forward_list__merge)|将元素从参数列表中删除，将它们插入目标转发列表，将新的组合元素集以升序或其他指定顺序排序。|  
|[pop_front](#forward_list__pop_front)|删除转发列表起始处的一个元素。|  
|[push_front](#forward_list__push_front)|在转发列表起始处添加一个元素。|  
|[remove](#forward_list__remove)|清除转发列表中与指定值匹配的元素。|  
|[remove_if](#forward_list__remove_if)|将满足指定谓词的元素从转发列表中清除。|  
|[resize](#forward_list__resize)|为转发列表指定新的大小。|  
|[reverse](#forward_list__reverse)|颠倒转发列表中元素的顺序。|  
|[sort](#forward_list__sort)|按升序或按谓词指定的顺序排列元素。|  
|[splice_after](#forward_list__splice_after)|重新联结节点间的链接。|  
|[swap](#forward_list__swap)|交换两个转发列表的元素。|  
|[unique](#forward_list__unique)|删除通过了指定测试的相邻元素。|  
  
### <a name="operators"></a>运算符  
  
|||  
|-|-|  
|[operator=](#forward_list__operator_eq)|将转发列表的元素替换为另一个转发列表的副本。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<forward_list>  
  
 **命名空间：** std  
  
##  <a name="a-nameforwardlistallocatortypea--forwardlistallocatortype"></a><a name="forward_list__allocator_type"></a>  forward_list::allocator_type  
 一种类型，用于表示转发列表对象的分配器类。  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>备注  
 `allocator_type` 是模板参数 Allocator 的同义词。  
  
##  <a name="a-nameforwardlistassigna--forwardlistassign"></a><a name="forward_list__assign"></a>  forward_list::assign  
 清除转发列表中的元素，并将一组新的元素复制到目标转发列表。  
  
```  
 
void assign(
    size_type Count,   
    const Type& Val);
void assign(
    initializer_list<Type> IList);
template <class InputIterator>  
void assign(InputIterator First, InputIterator Last);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|` first`|替换范围的起始处。|  
|` last`|替换范围的结束处。|  
|` count`|要分配的元素数。|  
|` val`|要分配每个元素的值。|  
|`Type`|值的类型。|  
|`IList`|要复制的 initializer_list。|  
  
### <a name="remarks"></a>备注  
 如果 forward_list 是整数类型，则第一个成员函数的行为与 `assign((size_type)First, (Type)Last)` 相同。 否则，第一个成员函数将 `*this` 控制的序列替换为序列 [ `First, Last)`，该序列不能与初始控制序列重叠。  
  
 第二个成员函数将 `*this` 控制的序列替换为值 `Val` 的重复 `Count` 元素。  
  
 第三个成员函数将 initializer_list 的元素复制到 forward_list 中。  
  
##  <a name="a-nameforwardlistbeforebegina--forwardlistbeforebegin"></a><a name="forward_list__before_begin"></a>  forward_list::before_begin  
 返回寻址转发列表中第一个元素之前的位置的迭代器。  
  
```  
const_iterator before_begin() const;
iterator before_begin();
```  
  
### <a name="return-value"></a>返回值  
 恰好指向序列的第一个元素之前位置（或恰好在空序列末尾的位置之前）的正向迭代器。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameforwardlistbegina--forwardlistbegin"></a><a name="forward_list__begin"></a>  forward_list::begin  
 返回寻址转发列表中第一个元素的迭代器。  
  
```  
const_iterator begin() const;
iterator begin();
```  
  
### <a name="return-value"></a>返回值  
 指向序列第一个元素（或刚超出空序列末尾的位置）的正向迭代器。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameforwardlistcbeforebegina--forwardlistcbeforebegin"></a><a name="forward_list__cbefore_begin"></a>  forward_list::cbefore_begin  
 返回寻址转发列表中第一个元素之前的位置的常量迭代器。  
  
```  
const_iterator cbefore_begin() const;
```  
  
### <a name="return-value"></a>返回值  
 恰好指向序列的第一个元素之前位置（或恰好在空序列末尾的位置之前）的正向迭代器。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameforwardlistcbegina--forwardlistcbegin"></a><a name="forward_list__cbegin"></a>  forward_list::cbegin  
 返回确定范围中第一个元素地址的 `const` 迭代器。  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>返回值  
 `const` 前向访问迭代器，指向范围的第一个元素，或刚超出空范围末尾的位置（对于空范围，`cbegin() == cend()`）。  
  
### <a name="remarks"></a>备注  
 由于使用 `cbegin` 的返回值，因此不能修改范围中的元素。  
  
 可以使用此成员函数替代 `begin()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在此示例中，将 `Container` 视为支持 `begin()` 和 `cbegin()` 的可修改的 (non- `const`) 任何类型的容器。  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator  
```  
  
##  <a name="a-nameforwardlistcenda--forwardlistcend"></a><a name="forward_list__cend"></a>  forward_list::cend  
 返回一个 `const` 迭代器，此迭代器用于发现刚超出范围中最后一个元素的位置。  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>返回值  
 指向恰好超出范围末尾位置的向前访问迭代器。  
  
### <a name="remarks"></a>备注  
 `cend` 用于测试迭代器是否超过了其范围的末尾。  
  
 可以使用此成员函数替代 `end()` 成员函数，以保证返回值为 `const_iterator`。 它一般与 [auto](../cpp/auto-cpp.md) 类型推导关键字联合使用，如下例所示。 在此示例中，将 `Container` 视为支持 `end()` 和 `cend()` 的可修改的 (non- `const`) 任何类型的容器。  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 不应对 `cend` 返回的值取消引用。  
  
##  <a name="a-nameforwardlistcleara--forwardlistclear"></a><a name="forward_list__clear"></a>  forward_list::clear  
 清除转发列表中的所有元素。  
  
```  
void clear();
```  
  
### <a name="remarks"></a>备注  
 此成员函数调用 `erase_after(before_begin(), end()).`  
  
##  <a name="a-nameforwardlistconstiteratora--forwardlistconstiterator"></a><a name="forward_list__const_iterator"></a>  forward_list::const_iterator  
 一种类型，用于为转发列表提供常量迭代器。  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>备注  
 `const_iterator` 描述为可用作受控序列的常量向前迭代器的对象。 在此处描述为实现定义的类型的同义词。  
  
##  <a name="a-nameforwardlistconstpointera--forwardlistconstpointer"></a><a name="forward_list__const_pointer"></a>  forward_list::const_pointer  
 一种类型，用于提供指向转发列表中的 `const` 元素的指针。  
  
```  
typedef typename Allocator::const_pointer  
    const_pointer; 
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameforwardlistconstreferencea--forwardlistconstreference"></a><a name="forward_list__const_reference"></a>  forward_list::const_reference  
 一种类型，用于提供对转发列表中元素的常量引用。  
  
```  
typedef typename Allocator::const_reference const_reference;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameforwardlistdifferencetypea--forwardlistdifferencetype"></a><a name="forward_list__difference_type"></a>  forward_list::difference_type  
 一种有符号整数类型，可用于表示转发列表中某个范围类迭代器所指向元素之间的元素数目。  
  
```  
typedef typename Allocator::difference_type difference_type;  
```  
  
### <a name="remarks"></a>备注  
 `difference_type` 描述一个对象，可以表示受控序列中任意两个元素的地址之间的差异。  
  
##  <a name="a-nameforwardlistemplaceaftera--forwardlistemplaceafter"></a><a name="forward_list__emplace_after"></a>  forward_list::emplace_after  
 在指定位置之后移动构造新元素。  
  
```  
template <class T>  
iterator emplace_after(const_iterator Where, Type&& val);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Where`|目标转发列表中构造新元素的位置。|  
|` val`|构造函数参数。|  
  
### <a name="return-value"></a>返回值  
 指定新插入元素的迭代器。  
  
### <a name="remarks"></a>备注  
 此成员函数紧跟受控序列中 `Where` 指向的元素之后插入具有构造函数参数 ` val` 的元素。 否则，其行为与 [forward_list :: insert_after](#forward_list__insert_after) 相同。  
  
##  <a name="a-nameforwardlistemplacefronta--forwardlistemplacefront"></a><a name="forward_list__emplace_front"></a>  forward_list::emplace_front  
 在列表的起始位置添加一个就地构造的元素。  
  
```  
template <class Type>  
void emplace_front(Type&& val);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|` val`|添加到转发列表开头的元素。|  
  
### <a name="remarks"></a>备注  
 此成员函数在受控序列末尾插入具有构造函数参数 `_ val` 的元素。  
  
 如果引发了异常，该容器将保持不变，并重新引发该异常。  
  
##  <a name="a-nameforwardlistemptya--forwardlistempty"></a><a name="forward_list__empty"></a>  forward_list::empty  
 测试转发列表是否为空。  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>返回值  
 如果转发列表为空，则为 `true`；否则为 `false`。  
  
##  <a name="a-nameforwardlistenda--forwardlistend"></a><a name="forward_list__end"></a>  forward_list::end  
 返回寻址转发列表中最后一个元素之后的位置的迭代器。  
  
```  
const_iterator end() const;
iterator end();
```  
  
### <a name="return-value"></a>返回值  
 指向刚超出序列末尾位置的正向迭代器。  
  
##  <a name="a-nameforwardlisteraseaftera--forwardlisteraseafter"></a><a name="forward_list__erase_after"></a>  forward_list::erase_after  
 删除转发列表中指定位置之后的元素。  
  
```  
iterator erase_after(const_iterator Where);
iterator erase_after(const_iterator first, const_iterator last);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|`Where`|目标转发列表中擦除元素的位置。|  
|` first`|要擦除范围的起始处。|  
|` last`|要擦除范围的结尾处。|  
  
### <a name="return-value"></a>返回值  
 一个迭代器，它指定已删除的任何元素之外保留的第一个元素或 [forward_list::end](#forward_list__end)（若此类元素不存在）。  
  
### <a name="remarks"></a>备注  
 第一个成员函数将删除 `Where` 之后的受控序列的元素。  
  
 第二个成员函数将删除 `( first,  last)` 范围中受控序列的元素（不包括任一终点）。  
  
 擦除 `N` 元素会导致调用 `N` 析构函数。 发生[重新分配](../standard-library/forward-list-class.md)，因此迭代器和引用对已清除元素无效。  
  
 成员函数从不引发异常。  
  
##  <a name="a-nameforwardlistforwardlista--forwardlistforwardlist"></a><a name="forward_list__forward_list"></a>  forward_list::forward_list  
 构造 `forward_list` 类型的对象。  
  
```  
forward_list();
explicit forward_list(const Allocator& Al);
explicit forward_list(size_type Count);
forward_list(size_type Count, const Type& Val);
forward_list(size_type Count, const Type& Val, const Allocator& Al);
forward_list(const forward_list& Right);
forward_list(const forward_list& Right, const Allocator& Al);
forward_list(forward_list&& Right);
forward_list(forward_list&& Right, const Allocator& Al);
forward_list(initializer_list<Type> IList, const Alloc& Al);
template <class InputIterator>  
forward_list(InputIterator First, InputIterator Last);
template <class InputIterator>  
forward_list(InputIterator First, InputIterator Last, const Allocator& Al);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Al`|要用于此对象的分配器类。|  
|`Count`|所构造列表中元素的数目。|  
|`Val`|构造的列表中的元素值。|  
|`Right`|所构造列表要作为其副本的列表。|  
|`First`|要复制的范围元素中的第一个元素的位置。|  
|`Last`|要复制的元素范围以外的第一个元素的位置。|  
|`IList`|要复制的 initializer_list。|  
  
### <a name="remarks"></a>备注  
 所有构造函数都存储[分配器](../standard-library/allocator-class.md)并初始化受控序列。 分配器对象是参数 `Al`（如果存在）。 对于复制构造函数，则为 ` right.get_allocator()`。 否则，它是 `Allocator()`。  
  
 前两个构造函数指定一个空的初始受控序列。  
  
 第三个构造函数指定值为 `Type()` 的 `Count` 个元素的重复元素。  
  
 第四个和第五个构造函数指定值为 `Val` 的 `Count` 个元素的重复元素。  
  
 第六个构造函数指定通过 `Right` 控制的序列的副本。 如果 `InputIterator` 是整数类型，则接下来的两个构造函数指定 `(size_type)First` 元素的重复元素，元素的值为 `(Type)Last`。 否则，接下来两个构造函数指定序列 `[First, Last)`。  
  
 第九个和第十个构造函数与第六个构造函数相同，但它具有 [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) 引用。  
  
 最后一个构造函数指定具有类 `initializer_list<Type>` 的对象的初始受控序列。  
  
##  <a name="a-nameforwardlistfronta--forwardlistfront"></a><a name="forward_list__front"></a>  forward_list::front  
 返回对转发列表中第一个元素的引用。  
  
```  
reference front();
const_reference front() const;
```  
  
### <a name="return-value"></a>返回值  
 对受控序列的第一个元素的引用，必须为非空。  
  
##  <a name="a-nameforwardlistgetallocatora--forwardlistgetallocator"></a><a name="forward_list__get_allocator"></a>  forward_list::get_allocator  
 返回用于构造转发列表的分配器对象的一个副本。  
  
```  
allocator_type get_allocator() const;
```  
  
### <a name="return-value"></a>返回值  
 存储的 [allocator](../standard-library/allocator-class.md) 对象。  
  
##  <a name="a-nameforwardlistinsertaftera--forwardlistinsertafter"></a><a name="forward_list__insert_after"></a>  forward_list::insert_after  
 在转发列表中的指定位置之后添加元素。  
  
```  
iterator insert_after(const_iterator Where, const Type& Val);
void insert_after(const_iterator Where, size_type Count, const Type& Val);
void insert_after(const iterator Where, initializer_list<Type> IList);
iterator insert_after(const_iterator Where, Type&& Val);
template <class InputIterator>  
void insert_after(const_iterator Where, InputIterator First, InputIterator Last);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`Where`|目标转发列表中插入第一个元素的位置。|  
|`Count`|要插入的元素数。|  
|`First`|插入范围的起始处。|  
|`Last`|插入范围的结束处。|  
|`Val`|添加到转发列表的元素。|  
|`IList`|要插入的 initializer_list。|  
  
### <a name="return-value"></a>返回值  
 一个迭代器，指定新插入的元素（仅限第一个和最后一个成员函数）。  
  
### <a name="remarks"></a>备注  
 每个成员函数紧跟受控序列中 `Where` 指向的元素之后插入由剩余操作数指定的序列。  
  
 第一个成员函数插入一个值为 `Val` 的元素，并返回一个指定新插入的元素的迭代器。  
  
 第二个成员函数插入 `Count` 元素的重复元素，值为 `Val`。  
  
 如果 `InputIterator` 是整数类型，则第三个成员函数的行为与 `insert(it, (size_type)First, (Type)Last)` 相同。 否则，它插入序列 `[First, Last)`，该序列不能与初始受控序列重叠。  
  
 第四个成员函数插入由类 `initializer_list<Type>` 的对象指定的序列。  
  
 最后一个成员函数与第一个成员函数相同，但前者具有 [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) 引用。  
  
 插入 `N` 元素会导致调用 `N` 构造函数。 发生[重新分配](../standard-library/forward-list-class.md)，但没有迭代器或引用变为无效。  
  
 如果在一个或多个元素插入过程中引发异常，则容器将保持不变并重新引发异常。  
  
##  <a name="a-nameforwardlistiteratora--forwardlistiterator"></a><a name="forward_list__iterator"></a>  forward_list::iterator  
 一种类型，用于为转发列表提供迭代器。  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>备注  
 `iterator` 描述为可用作受控序列的前向迭代器的对象。 在此处描述为实现定义的类型的同义词。  
  
##  <a name="a-nameforwardlistmaxsizea--forwardlistmaxsize"></a><a name="forward_list__max_size"></a>  forward_list::max_size  
 返回转发列表的最大长度。  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>返回值  
 该对象可控制的最长序列的长度。  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameforwardlistmergea--forwardlistmerge"></a><a name="forward_list__merge"></a>  forward_list::merge  
 将两个排序序列合并为一个以线性时间排序的序列。 将元素从参数列表中删除，并将它们插入此 `forward_list`。 调用 `merge` 之前，这两个列表应该按相同的比较函数对象排序。 合并的列表将按该比较函数对象进行排序。  
  
```  
void merge(forward_list& right);
template <class Predicate>  
void merge(forward_list& right, Predicate comp);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|` right`|要从其开始合并的转发列表。|  
|` comp`|用于对元素进行排序的比较函数对象。|  
  
### <a name="remarks"></a>备注  
 `forward_list::merge` 将元素从 `forward_list`` right``,` 中删除，并将它们插入此 `forward_list`。 这两个序列必须由相同的谓词进行排序，如下所述。 合并的序列也可按该比较函数对象进行排序。  
  
 对于在 `i` 和 `j` 位置指定元素的迭代器 `Pi` 和 `Pj`，第一个成员函数每当 `i < j` 时采用顺序 `!(*Pj < *Pi)`。 （元素按 `ascending` 顺序进行排序。）第二个成员函数每当 `i < j` 时采用顺序 `! comp(*Pj, *Pi)`。  
  
 原始受控序列中没有元素对在所生成的受控序列中反向。 如果所生成的受控序列中的一对元素经比较相等 (`!(*Pi < *Pj) && !(*Pj < *Pi)`)，则来自原始受控序列的元素在来自由 ` right` 控制的序列的元素之前显示。  
  
 仅当 ` comp` 引发异常时才会发生异常。 在这种情况下，受控序列以未指定的顺序保留，并重新引发异常。  
  
##  <a name="a-nameforwardlistoperatoreqa--forwardlistoperator"></a><a name="forward_list__operator_eq"></a>  forward_list::operator=  
 将转发列表的元素替换为另一个转发列表的副本。  
  
```  
forward_list& operator=(const forward_list& right);
forward_list& operator=(initializer_list<Type> IList);
forward_list& operator=(forward_list&& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|` right`|要复制到转发列表的转发列表。|  
|`IList`|一个用括号括起来的初始化表达式列表，其行为类似于类型 `Type` 的元素的序列。|  
  
### <a name="remarks"></a>备注  
 第一个成员运算符使用 ` right` 控制的序列的副本替换受控序列。  
  
 第二个成员操作符从类 `initializer_list<Type>` 的对象替换受控序列。  
  
 第三个成员运算符与第一个成员运算符相同，但前者具有 [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) 引用。  
  
##  <a name="a-nameforwardlistpointera--forwardlistpointer"></a><a name="forward_list__pointer"></a>  forward_list::pointer  
 一种类型，用于提供指向转发列表中元素的指针。  
  
```  
typedef typename Allocator::pointer pointer;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameforwardlistpopfronta--forwardlistpopfront"></a><a name="forward_list__pop_front"></a>  forward_list::pop_front  
 删除转发列表起始处的一个元素。  
  
```  
void pop_front();
```  
  
### <a name="remarks"></a>备注  
 转发列表的第一个元素必须为非空。  
  
 成员函数从不引发异常。  
  
##  <a name="a-nameforwardlistpushfronta--forwardlistpushfront"></a><a name="forward_list__push_front"></a>  forward_list::push_front  
 在转发列表起始处添加一个元素。  
  
```  
void push_front(const Type& val);
void push_front(Type&& val);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|` val`|添加到转发列表开头的元素。|  
  
### <a name="remarks"></a>备注  
 如果引发了异常，该容器将保持不变，并重新引发该异常。  
  
##  <a name="a-nameforwardlistreferencea--forwardlistreference"></a><a name="forward_list__reference"></a>  forward_list::reference  
 一种类型，用于提供对转发列表中元素的引用。  
  
```  
typedef typename Allocator::reference reference;  
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameforwardlistremovea--forwardlistremove"></a><a name="forward_list__remove"></a>  forward_list::remove  
 清除转发列表中与指定值匹配的元素。  
  
```  
void remove(const Type& val);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|` val`|一个值，如果某个元素包含该值，则会导致从列表中删除该元素。|  
  
### <a name="remarks"></a>备注  
 成员函数从受控序列删除由迭代器 `P` 指定的所有元素，其中 `*P ==  val`。  
  
 成员函数从不引发异常。  
  
##  <a name="a-nameforwardlistremoveifa--forwardlistremoveif"></a><a name="forward_list__remove_if"></a>  forward_list::remove_if  
 将满足指定谓词的元素从转发列表中清除。  
  
```  
template <class Predicate>  
void remove_if(Predicate pred);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|` pred`|一元谓词，如果元素满足该谓词，则该谓词会导致此元素从列表删除。|  
  
### <a name="remarks"></a>备注  
 成员函数从受控序列删除由迭代器 `P` 指定的所有元素，其中 ` pred(*P)` 为 true。  
  
 仅当 ` pred` 引发异常时才会发生异常。 在这种情况下，受控序列以未指定的状态保留，并重新引发异常。  
  
##  <a name="a-nameforwardlistresizea--forwardlistresize"></a><a name="forward_list__resize"></a>  forward_list::resize  
 为转发列表指定新的大小。  
  
```  
void resize(size_type _Newsize);
void resize(size_type _Newsize, const Type& val);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|`_Newsize`|调整大小后的转发列表中的元素数。|  
|` val`|要用于填充的值。|  
  
### <a name="remarks"></a>备注  
 两个成员函数都可确保此后列表中的元素数为 `_Newsize`。 如果它必须使受控序列更长，则第一个成员函数追加具有值 `Type()` 的元素，而第二个成员函数追加具有值 ` val` 的元素。 若要使受控序列更短，两个成员函数可有效地调用 `erase_after(begin() + _Newsize - 1, end())`。  
  
##  <a name="a-nameforwardlistreversea--forwardlistreverse"></a><a name="forward_list__reverse"></a>  forward_list::reverse  
 颠倒转发列表中元素的顺序。  
  
```  
void reverse();
```  
  
### <a name="remarks"></a>备注  
  
##  <a name="a-nameforwardlistsizetypea--forwardlistsizetype"></a><a name="forward_list__size_type"></a>  forward_list::size_type  
 一种类型，用于表示两个元素之间的无符号距离。  
  
```  
typedef typename Allocator::size_type size_type;  
```  
  
### <a name="remarks"></a>备注  
 无符号的整数类型描述可表示任何受控序列长度的对象。  
  
##  <a name="a-nameforwardlistsorta--forwardlistsort"></a><a name="forward_list__sort"></a>  forward_list::sort  
 按升序或按谓词指定的顺序排列元素。  
  
```  
void sort();
template <class Predicate>  
void sort(Predicate pred);
```  
  
### <a name="parameters"></a>参数  
  
|参数|说明|  
|---------------|-----------------|  
|` pred`|排序谓词。|  
  
### <a name="remarks"></a>备注  
 两个成员函数通过谓词对受控序列中的元素排序，如下所述。  
  
 对于在 `i` 和 `j` 位置指定元素的迭代器 `Pi` 和 `Pj`，第一个成员函数每当 `i < j` 时采用顺序 `!(*Pj < *Pi)`。 （元素按 `ascending` 顺序进行排序。）成员模板函数每当 `i < j` 时采用顺序 `! pred(*Pj, *Pi)`。 原始受控序列中没有排序的元素对在所生成的受控序列中反向。 （排序是稳定的。）  
  
 仅当 ` pred` 引发异常时才会发生异常。 在这种情况下，受控序列以未指定的顺序保留，并重新引发异常。  
  
##  <a name="a-nameforwardlistspliceaftera--forwardlistspliceafter"></a><a name="forward_list__splice_after"></a>  forward_list::splice_after  
 从源 forward_list 中删除元素并将其插入到目标 forward_list 中。  
  
```  
// insert the entire source forward_list  
void splice_after(const_iterator Where, forward_list& Source);
void splice_after(const_iterator Where, forward_list&& Source);

// insert one element of the source forward_list  
void splice_after(const_iterator Where, forward_list& Source, const_iterator Iter);
void splice_after(const_iterator Where, forward_list&& Source, const_iterator Iter);

// insert a range of elements from the source forward_list  
void splice_after(
    const_iterator Where, 
    forward_list& Source,
    const_iterator First,
    const_iterator Last);

void splice_after(
    const_iterator Where,
    forward_list&& Source,
    const_iterator First,
    const_iterator Last);
```  
  
### <a name="parameters"></a>参数  
 `Where`  
 目标 forward_list 中要在其后面进行插入的位置。  
  
 `Source`  
 要插入目标 forward_list 中的源 forward_list。  
  
 `Iter`  
 要从源 forward_list 中进行插入的元素。  
  
 `First`  
 要从源 forward_list 中进行插入的范围中的第一个元素。  
  
 `Last`  
 要从源 forward_list 中进行插入的范围之外的第一个位置。  
  
### <a name="remarks"></a>备注  
 第一对成员函数将由 `Source` 控制的序列正好插入 `Where` 所指向的控制序列中的元素之后。 它还会删除 `Source` 中的所有元素。 （`&Source` 不能等于 `this`。）  
  
 第二对成员函数删除由 `Iter` 控制的序列中正好位于 `Source` 之后的元素，并将其正好插入到 `Where` 所指向的控制序列中的元素之后。 （如果 `Where == Iter || Where == ++Iter`，则不会发生更改。）  
  
 第三对成员函数（范围接合）将由 `(First, Last)` 控制的序列中的 `Source` 指定的子范围正好插入 `Where` 所指向的控制序列中的元素之后。 它还会删除由 `Source` 控制的序列中的原始子范围。 （如果 `&Source == this`，则范围 `(First, Last)` 不得包含 `Where` 所指向的元素。）  
  
 如果范围接合插入 `N` 个元素和 `&Source != this`，则类 [iterator](#forward_list__iterator) 的对象会递增 `N` 次。  
  
 任何迭代器、指针或指定接合的元素的引用都不会变得无效。  
  
### <a name="example"></a>示例  
  
```cpp  
// forward_list_splice_after.cpp  
// compile with: /EHsc /W4  
#include <forward_list>  
#include <iostream>  
  
using namespace std;  
  
template <typename S> void print(const S& s) {  
    for (const auto& p : s) {  
        cout << "(" << p << ") ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    forward_list<int> c1{ 10, 11 };  
    forward_list<int> c2{ 20, 21, 22 };  
    forward_list<int> c3{ 30, 31 };  
    forward_list<int> c4{ 40, 41, 42, 43 };  
  
    forward_list<int>::iterator where_iter;  
    forward_list<int>::iterator first_iter;  
    forward_list<int>::iterator last_iter;  
  
    cout << "Beginning state of lists:" << endl;  
    cout << "c1 = ";  
    print(c1);  
    cout << "c2 = ";  
    print(c2);  
    cout << "c3 = ";  
    print(c3);  
    cout << "c4 = ";  
    print(c4);  
  
    where_iter = c2.begin();  
    ++where_iter; // start at second element  
    c2.splice_after(where_iter, c1);  
    cout << "After splicing c1 into c2:" << endl;  
    cout << "c1 = ";  
    print(c1);  
    cout << "c2 = ";  
    print(c2);  
  
    first_iter = c3.begin();  
    c2.splice_after(where_iter, c3, first_iter);  
    cout << "After splicing the first element of c3 into c2:" << endl;  
    cout << "c3 = ";  
    print(c3);  
    cout << "c2 = ";  
    print(c2);  
  
    first_iter = c4.begin();  
    last_iter = c4.end();  
    // set up to get the middle elements  
    ++first_iter;  
    c2.splice_after(where_iter, c4, first_iter, last_iter);  
    cout << "After splicing a range of c4 into c2:" << endl;  
    cout << "c4 = ";  
    print(c4);  
    cout << "c2 = ";  
    print(c2);  
}  
  
```  
  
```Output  
Beginning state of lists:c1 = (10) (11)c2 = (20) (21) (22)c3 = (30) (31)c4 = (40) (41) (42) (43)After splicing c1 into c2:c1 =c2 = (20) (21) (10) (11) (22)After splicing the first element of c3 into c2:c3 = (30)c2 = (20) (21) (31) (10) (11) (22)After splicing a range of c4 into c2:c4 = (40) (41)c2 = (20) (21) (42) (43) (31) (10) (11) (22)  
```  
  
##  <a name="a-nameforwardlistswapa--forwardlistswap"></a><a name="forward_list__swap"></a>  forward_list::swap  
 交换两个转发列表的元素。  
  
```  
void swap(forward_list& right);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|` right`|提供要交换的元素的转发列表。|  
  
### <a name="remarks"></a>备注  
 成员函数交换 `*this` 和 ` right` 之间的受控序列。 如果 `get_allocator() ==  right.get_allocator()`，它在固定时间内执行此操作，它不引发任何异常，不使任何引用、指针或指定两个受控序列中的元素的迭代器失效。 否则，它所执行的元素分配和构造函数调用数量会与两个受控序列中的元素数量成正比。  
  
##  <a name="a-nameforwardlistuniquea--forwardlistunique"></a><a name="forward_list__unique"></a>  forward_list::unique  
 删除来自每个连续的相等元素组的第一个元素之外的所有元素。  
  
```  
void unique();
template <class BinaryPredicate>  
void unique(BinaryPredicate comp);
```  
  
### <a name="parameters"></a>参数  
  
|参数|描述|  
|---------------|-----------------|  
|` comp`|用于比较连续元素的二元谓词。|  
  
### <a name="remarks"></a>备注  
 保留每个唯一元素的第一个元素，并删除其余元素。 元素必须进行排序，以使具有相等值的元素在列表中相邻。  
  
 第一个成员函数从受控序列删除经比较等于其前一个元素的每个元素。 对于在 `i` 和 `j` 位置指定元素的迭代器 `Pi` 和 `Pj`，第二个成员函数删除其中 `i + 1 == j &&  comp(*Pi, *Pj)` 的每个元素。  
  
 对于长度为 `N` (> 0) 的受控序列，计算谓词 ` comp(*Pi, *Pj)` `N - 1` 次。  
  
 仅当 ` comp` 引发异常时才会发生异常。 在这种情况下，受控序列以未指定的状态保留，并重新引发异常。  
  
##  <a name="a-nameforwardlistvaluetypea--forwardlistvaluetype"></a><a name="forward_list__value_type"></a>  forward_list::value_type  
 一种类型，用于表示转发列表中存储的元素的类型。  
  
```  
typedef typename Allocator::value_type value_type;  
```  
  
### <a name="remarks"></a>备注  
 该类型是模板参数 _ `Ty` 的同义词。  
  
## <a name="see-also"></a>另请参阅  
 [<forward_list>](../standard-library/forward-list.md)


