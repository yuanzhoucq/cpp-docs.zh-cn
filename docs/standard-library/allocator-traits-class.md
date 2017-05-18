---
title: "allocator_traits 类 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::allocator_traits
- memory/std::allocator_traits::propagate_on_container_move_assignment
- memory/std::allocator_traits::const_pointer
- memory/std::allocator_traits::propagate_on_container_swap
- memory/std::allocator_traits::propagate_on_container_copy_assignment
- memory/std::allocator_traits::difference_type
- memory/std::allocator_traits::allocator_type
- memory/std::allocator_traits::value_type
- memory/std::allocator_traits::pointer
- memory/std::allocator_traits::size_type
- memory/std::allocator_traits::const_void_pointer
- memory/std::allocator_traits::void_pointer
- memory/std::allocator_traits::allocate
- memory/std::allocator_traits::construct
- memory/std::allocator_traits::deallocate
- memory/std::allocator_traits::destroy
- memory/std::allocator_traits::max_size
- memory/std::allocator_traits::select_on_container_copy_construction
dev_langs:
- C++
ms.assetid: 612974b8-b5d4-4668-82fb-824bff6821d6
caps.latest.revision: 12
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: d4fdcb8af6fa8b33ee6153563770b9bf00f02942
ms.contentlocale: zh-cn
ms.lasthandoff: 04/29/2017

---
# <a name="allocatortraits-class"></a>allocator_traits 类
此模板类描述补充*分配器类型*的对象。 分配器类型是描述分配器对象的任何类型，它用于管理已分配的存储。 具体而言，对于任何分配器类型 `Alloc`，可以使用 `allocator_traits<Alloc>` 来确定支持分配器的容器所需的所有信息。 有关详细信息，请参阅默认的 [allocator 类](../standard-library/allocator-class.md)。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template <class Alloc>
class allocator_traits;
```  
  
### <a name="typedefs"></a>Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`allocator_traits::allocator_type`|该类型是模板参数 `Alloc`的同义词。|  
|`allocator_traits::const_pointer`|如果该类型的形式正确，则此类型为 `Alloc::const_pointer`，否则，此类型为 `pointer_traits<pointer>::rebind<const value_type>`。|  
|`allocator_traits::const_void_pointer`|如果该类型的形式正确，则此类型为 `Alloc::const_void_pointer`，否则，此类型为 `pointer_traits<pointer>::rebind<const void>`。|  
|`allocator_traits::difference_type`|如果该类型的形式正确，则此类型为 `Alloc::difference_type`，否则，此类型为 `pointer_traits<pointer>::difference_type`。|  
|`allocator_traits::pointer`|如果该类型的形式正确，则此类型为 `Alloc::pointer`，否则，此类型为 `value_type *`。|  
|`allocator_traits::propagate_on_container_copy_assignment`|如果该类型的形式正确，则此类型为 `Alloc::propagate_on_container_copy_assignment`，否则，此类型为 `false_type`。|  
|`allocator_traits::propagate_on_container_move_assignment`|如果该类型的形式正确，则此类型为 `Alloc::propagate_on_container_move_assignment`，否则，此类型为 `false_type`。 如果类型为 true，则支持分配器的容器将在移动赋值上复制其存储的分配器。|  
|`allocator_traits::propagate_on_container_swap`|如果该类型的形式正确，则此类型为 `Alloc::propagate_on_container_swap`，否则，此类型为 `false_type`。 如果类型为 true，则支持分配器的容器将在交换上交换其存储的分配器。|  
|`allocator_traits::size_type`|如果该类型的形式正确，则此类型为 `Alloc::size_type`，否则，此类型为 `make_unsigned<difference_type>::type`。|  
|`allocator_traits::value_type`|此类型是 `Alloc::value_type` 的同义词。|  
|`allocator_traits::void_pointer`|如果该类型的形式正确，则此类型为 `Alloc::void_pointer`，否则，此类型为 `pointer_traits<pointer>::rebind<void>`。|  
  
### <a name="static-methods"></a>静态方法  
 以下静态方法调用给定分配器参数上的相应的方法。  
  
|名称|描述|  
|----------|-----------------|  
|[allocate](#allocate)|使用给定的分配器参数分配内存的静态方法。|  
|[construct](#construct)|使用指定的分配器构造对象的静态方法。|  
|[deallocate](#deallocate)|使用指定的分配器释放指定的对象数的静态方法。|  
|[destroy](#destroy)|使用指定的分配器调用对象上的构造函数而不释放其内存的静态方法。|  
|[max_size](#max_size)|可以分配使用指定的分配器确定对象的最大数目的静态方法。|  
|[select_on_container_copy_construction](#select_on_container_copy_construction)|在指定的分配器上调用 `select_on_container_copy_construction` 的静态方法。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<memory>  
  
 **命名空间：** std  
  
##  <a name="allocate"></a>allocator_traits:: allocate
 使用给定的分配器参数分配内存的静态方法。  
  
```cpp  
static pointer allocate(Alloc& al, size_type count);

static pointer allocate(Alloc& al, size_type count,
    typename allocator_traits<void>::const_pointer* hint);
```  
  
### <a name="parameters"></a>参数  
 `al`  
 分配器对象。  
  
 `count`  
 要分配的元素数量。  
  
 `hint`  
 通过定位在请求之前分配的对象的地址，`const_pointer` 可能帮助分配器满足存储请求。 Null 指针将被视为无提示。  
  
### <a name="return-value"></a>返回值  
 每个方法均返回指向已分配对象的指针。  
  
 第一种静态方法返回 `al.allocate(count)`。  
  
 第二种方法返回 `al.allocate(count, hint)`（如果该表达式形式正确）；否则返回 `al.allocate(count)`。  
  
##  <a name="construct"></a>allocator_traits:: construct
 使用指定的分配器构造对象的静态方法。  
  
```cpp  
template <class Uty, class Types>
static void construct(Alloc& al, Uty* ptr, Types&&... args);
```  
  
### <a name="parameters"></a>参数  
 `al`  
 分配器对象。  
  
 `ptr`  
 指向要构造对象的位置的指针。  
  
 `args`  
 传递给对象构造函数的参数列表。  
  
### <a name="remarks"></a>备注  
 如果该表达式形式正确，则静态成员函数调用 `al.construct(ptr, args...)`；否则计算 `::new (static_cast<void *>(ptr)) Uty(std::forward<Types>(args)...)` 的结果。  
  
##  <a name="deallocate"></a>allocator_traits:: deallocate
 使用指定的分配器释放指定的对象数的静态方法。  
  
```cpp  
static void deallocate(Alloc al,
    pointer ptr,
    size_type count);
```  
  
### <a name="parameters"></a>参数  
 `al`  
 分配器对象。  
  
 `ptr`  
 指向要释放对象的起始位置的指针。  
  
 `count`  
 要释放对象的数量。  
  
### <a name="remarks"></a>备注  
 此方法调用 `al.deallocate(ptr, count)`。  
  
 此方法不会引发任何操作。  
  
##  <a name="destroy"></a>allocator_traits:: destroy
 使用指定的分配器调用对象上的构造函数而不释放其内存的静态方法。  
  
```cpp  
template <class Uty>
static void destroy(Alloc& al, Uty* ptr);
```  
  
### <a name="parameters"></a>参数  
 `al`  
 分配器对象。  
  
 `ptr`  
 指向对象位置的指针。  
  
### <a name="remarks"></a>备注  
 如果该表达式形式正确，则此方法调用 `al.destroy(ptr)`；否则计算 `ptr->~Uty()` 的结果。  
  
##  <a name="max_size"></a>allocator_traits:: max_size
 可以分配使用指定的分配器确定对象的最大数目的静态方法。  
  
```cpp  
static size_type max_size(const Alloc& al);
```  
  
### <a name="parameters"></a>参数  
 `al`  
 分配器对象。  
  
### <a name="remarks"></a>备注  
 如果该表达式形式正确，则此方法返回 `al.max_size()`；否则返回 `numeric_limits<size_type>::max()`。  
  
##  <a name="select_on_container_copy_construction"></a>allocator_traits:: select_on_container_copy_construction
 在指定的分配器上调用 `select_on_container_copy_construction` 的静态方法。  
  
```cpp  
static Alloc select_on_container_copy_construction(const Alloc& al);
```  
  
### <a name="parameters"></a>参数  
 `al`  
 分配器对象。  
  
### <a name="return-value"></a>返回值  
 如果该类型形式正确，则此方法返回 `al.select_on_container_copy_construction()`；否则返回 `al`。  
  
### <a name="remarks"></a>备注  
 此方法用于在所关联的容器为构造副本时指定分配器。  
  
## <a name="see-also"></a>另请参阅  
 [\<memory>](../standard-library/memory.md)   
 [pointer_traits Struct](../standard-library/pointer-traits-struct.md)   
 [scoped_allocator_adaptor 类](../standard-library/scoped-allocator-adaptor-class.md)

