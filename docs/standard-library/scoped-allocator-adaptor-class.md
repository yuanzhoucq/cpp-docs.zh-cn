---
title: "scoped_allocator_adaptor 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- std.scoped_allocator_adaptor
- scoped_allocator_adaptor
- scoped_allocator/std::scoped_allocator_adaptor
- std::scoped_allocator_adaptor
dev_langs:
- C++
helpviewer_keywords:
- scoped_allocator_adaptor Class
ms.assetid: 0d9b06a1-9a4a-4669-9470-8805cae48e89
caps.latest.revision: 10
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
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: f4c343592c2c767d52a66091ecca5b1bd4ae9e88
ms.lasthandoff: 02/24/2017

---
# <a name="scopedallocatoradaptor-class"></a>scoped_allocator_adaptor 类
表示分配器嵌套。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template <class Outer, class... Inner>  
class scoped_allocator_adaptor;  
```  
  
## <a name="remarks"></a>备注  
 模板类可封装一个或多个分配器的嵌套。 每个这样的类都具有一个类型为 `outer_allocator_type` 的最外层分配器，该类型也即 `Outer`，是 `scoped_allocator_adaptor` 对象的公共基类。 `Outer` 可用于分配容器要使用的内存。 通过调用 `outer_allocator` 可获取对此分配器基对象的引用。  
  
 嵌套的其余部分具有 `inner_allocator_type` 类型。 内部分配器用于为容器中的元素分配内存。 通过调用 `inner_allocator` 可获取对此类型的存储对象的引用。 如果 `Inner...` 不为空，则 `inner_allocator_type` 将具有类型 `scoped_allocator_adaptor<Inner...>`，`inner_allocator` 指示成员对象。 否则，`inner_allocator_type` 将具有类型 `scoped_allocator_adaptor<Outer>`，`inner_allocator` 指示整个对象。  
  
 嵌套的表现行为好像可以具有任意深度，可根据需要复制其最里层的封装分配器。  
  
 可借助界面中不可见的几个概念来帮助理解此模板类的行为。 最外层分配器，可协调对构造和销毁方法的所有调用。 它实际上是由递归函数 `OUTERMOST(X)` 定义的，其中 `OUTERMOST(X)` 是以下项之一。  
  
-   如果 `X.outer_allocator()` 的格式正确，则 `OUTERMOST(X)` 为 `OUTERMOST(X.outer_allocator())`。  
  
-   否则 `OUTERMOST(X)` 为 `X`。  
  
 需要定义三种类型以便进行展示：  
  
|类型|描述|  
|----------|-----------------|  
|`Outermost`|`OUTERMOST(*this)` 的类型。|  
|`Outermost_traits`|`allocator_traits<Outermost>`|  
|`Outer_traits`|`allocator_traits<Outer>`|  
  
### <a name="constructors"></a>构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[scoped_allocator_adaptor::scoped_allocator_adaptor 构造函数](#scoped_allocator_adaptor__scoped_allocator_adaptor_constructor)|构造 `scoped_allocator_adaptor` 对象。|  
  
### <a name="typedefs"></a>Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`const_pointer`|此类型是 `const_pointer`（与分配器 `Outer` 关联）的同义词。|  
|`const_void_pointer`|此类型是 `const_void_pointer`（与分配器 `Outer` 关联）的同义词。|  
|`difference_type`|此类型是 `difference_type`（与分配器 `Outer` 关联）的同义词。|  
|`inner_allocator_type`|此类型是嵌套适配器 `scoped_allocator_adaptor<Inner...>` 类型的同义词。|  
|`outer_allocator_type`|此类型是基本分配器 `Outer` 类型的同义词。|  
|`pointer`|此类型是 `pointer`（与分配器 `Outer` 关联）的同义词。|  
|`propagate_on_container_copy_assignment`|仅当 `Outer_traits::propagate_on_container_copy_assignment` 或 `inner_allocator_type::propagate_on_container_copy_assignment` 为 true 时，该类型才为 true。|  
|`propagate_on_container_move_assignment`|仅当 `Outer_traits::propagate_on_container_move_assignment` 或 `inner_allocator_type::propagate_on_container_move_assignment` 为 true 时，该类型才为 true。|  
|`propagate_on_container_swap`|仅当 `Outer_traits::propagate_on_container_swap` 或 `inner_allocator_type::propagate_on_container_swap` 为 true 时，该类型才为 true。|  
|`size_type`|此类型是 `size_type`（与分配器 `Outer` 关联）的同义词。|  
|`value_type`|此类型是 `value_type`（与分配器 `Outer` 关联）的同义词。|  
|`void_pointer`|此类型是 `void_pointer`（与分配器 `Outer` 关联）的同义词。|  
  
### <a name="structs"></a>结构  
  
|名称|描述|  
|----------|-----------------|  
|[scoped_allocator_adaptor::rebind 结构](#scoped_allocator_adaptor__rebind_struct)|将 `Outer::rebind\<Other>::other` 类型定义为 `scoped_allocator_adaptor\<Other, Inner...>` 的同义词。|  
  
### <a name="methods"></a>方法  
  
|名称|描述|  
|----------|-----------------|  
|[scoped_allocator_adaptor::allocate 方法](#scoped_allocator_adaptor__allocate_method)|通过使用 `Outer` 分配器分配内存。|  
|[scoped_allocator_adaptor::construct 方法](#scoped_allocator_adaptor__construct_method)|构造对象。|  
|[scoped_allocator_adaptor::deallocate 方法](#scoped_allocator_adaptor__deallocate_method)|通过使用外部分配器释放对象。|  
|[scoped_allocator_adaptor::destroy 方法](#scoped_allocator_adaptor__destroy_method)|销毁指定的对象。|  
|[scoped_allocator_adaptor::inner_allocator 方法](#scoped_allocator_adaptor__inner_allocator_method)|检索对类型为 `inner_allocator_type` 的存储对象的引用。|  
|[scoped_allocator_adaptor::max_size 方法](#scoped_allocator_adaptor__max_size_method)|确定可通过外部分配器分配的对象的最大数目。|  
|[scoped_allocator_adaptor::outer_allocator 方法](#scoped_allocator_adaptor__outer_allocator_method)|检索对类型为 `outer_allocator_type` 的存储对象的引用。|  
|[scoped_allocator_adaptor::select_on_container_copy_construction 方法](#scoped_allocator_adaptor__select_on_container_copy_construction_method)|创建一个新的 `scoped_allocator_adaptor` 对象，其中每个存储分配器对象都可通过调用每个相应分配器的 `select_on_container_copy_construction` 进行初始化。|  
  
## <a name="requirements"></a>要求  
 **标头：** \<scoped_allocator&1;>  
  
 **命名空间：** std  
  
##  <a name="a-namescopedallocatoradaptorallocatemethoda--scopedallocatoradaptorallocate-method"></a><a name="scoped_allocator_adaptor__allocate_method"></a>  scoped_allocator_adaptor::allocate 方法  
 通过使用 `Outer` 分配器分配内存。  
  
```cpp  
pointer allocate(size_type count);pointer allocate(size_type count, const_void_pointer hint);
```  
  
### <a name="parameters"></a>参数  
 `count`  
 要分配足够大的存储空间的元素数。  
  
 `hint`  
 通过定位在请求之前分配的对象地址，指针可能对分配器对象有所帮助。  
  
### <a name="return-value"></a>返回值  
 第一个成员函数返回 `Outer_traits::allocate(outer_allocator(), count)`。 第二个成员函数返回 `Outer_traits::allocate(outer_allocator(), count, hint)`。  
  
##  <a name="a-namescopedallocatoradaptorconstructmethoda--scopedallocatoradaptorconstruct-method"></a><a name="scoped_allocator_adaptor__construct_method"></a>  scoped_allocator_adaptor::construct 方法  
 构造对象。  
  
```cpp  
template <class Ty, class... Atypes>  
void construct(Ty* ptr, Atypes&&... args);

template <class Ty1, class Ty2, class... Atypes1, class... Atypes2>  
void construct(pair<Ty1, Ty2>* ptr, piecewise_construct_t,  
    tuple<Atypes1&&...>  
first, tuple<Atypes1&&...> second);

template <class Ty1, class Ty2>  
void construct(pair<Ty1, Ty2>* ptr);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr,  
    class Uy1&& first, class Uy2&& second);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr, const pair<Uy1, Uy2>& right);

template <class Ty1, class Ty2, class Uy1, class Uy2>  
void construct(pair<Ty1, Ty2>* ptr, pair<Uy1, Uy2>&& right);
```  
  
### <a name="parameters"></a>参数  
 `ptr`  
 指向要构造对象的内存位置的指针。  
  
 `args`  
 参数列表。  
  
 `first`  
 属于一对中第一种类型的对象。  
  
 `second`  
 属于一对中第二种类型的对象。  
  
 `right`  
 要移动或复制的现有对象。  
  
### <a name="remarks"></a>备注  
 第一种方法通过调用 `Outermost_traits::construct(OUTERMOST(*this), ptr, xargs...)` 在 `ptr` 处构造对象，其中 `xargs...` 是以下项之一。  
  
-   如果 `uses_allocator<Ty, inner_allocator_type>` 为 false，则 `xargs...` 为 `args...`。  
  
-   如果 `uses_allocator<Ty, inner_allocator_type>` 为 true 且 `is_constructible<Ty, allocator_arg_t, inner_allocator_type, args...>` 为 true，则 `xargs...` 为 `allocator_arg, inner_allocator(), args...`。  
  
-   如果 `uses_allocator<Ty, inner_allocator_type>` 为 true 且 `is_constructible<Ty, args..., inner_allocator()>` 为 true，则 `xargs...` 为 `args..., inner_allocator()`。  
  
 第二种方法通过调用 `Outermost_traits::construct(OUTERMOST(*this), &ptr->first, xargs...)` 和 `Outermost_traits::construct(OUTERMOST(*this), &ptr->second, xargs...)` 在 `ptr` 处构造对对象，其中 `xargs...` 在上述列表中是 `first...` 被修改的，而 `xargs...` 在上述列表中是 `second...` 被修改的。  
  
 第三种方法的行为与 `this->construct(ptr, piecewise_construct, tuple<>, tuple<>)` 相同。  
  
 第四种方法的行为与 `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(first), forward_as_tuple(std::forward<Uy2>(second))` 相同。  
  
 第五种方法的行为与 `this->construct(ptr, piecewise_construct, forward_as_tuple(right.first), forward_as_tuple(right.second))` 相同。  
  
 第六种方法的行为与 `this->construct(ptr, piecewise_construct, forward_as_tuple(std::forward<Uy1>(right.first), forward_as_tuple(std::forward<Uy2>(right.second))` 相同。  
  
##  <a name="a-namescopedallocatoradaptordeallocatemethoda--scopedallocatoradaptordeallocate-method"></a><a name="scoped_allocator_adaptor__deallocate_method"></a>  scoped_allocator_adaptor::deallocate 方法  
 通过使用外部分配器释放对象。  
  
```cpp  
void deallocate(pointer ptr, size_type count);
```  
  
### <a name="parameters"></a>参数  
 `ptr`  
 指向要释放对象的起始位置的指针。  
  
 `count`  
 要释放的对象数。  
  
##  <a name="a-namescopedallocatoradaptordestroymethoda--scopedallocatoradaptordestroy-method"></a><a name="scoped_allocator_adaptor__destroy_method"></a>  scoped_allocator_adaptor::destroy 方法  
 销毁指定的对象。  
  
```cpp  
template <class Ty>  
void destroy(Ty* ptr)  
```  
  
### <a name="parameters"></a>参数  
 `ptr`  
 指向要销毁对象的指针。  
  
### <a name="return-value"></a>返回值  
 `Outermost_traits::destroy(OUTERMOST(*this), ptr)`  
  
##  <a name="a-namescopedallocatoradaptorinnerallocatormethoda--scopedallocatoradaptorinnerallocator-method"></a><a name="scoped_allocator_adaptor__inner_allocator_method"></a>  scoped_allocator_adaptor::inner_allocator 方法  
 检索对类型为 `inner_allocator_type` 的存储对象的引用。  
  
```cpp  
inner_allocator_type& inner_allocator() noexcept;  
const inner_allocator_type& inner_allocator() const noexcept;  
```  
  
### <a name="return-value"></a>返回值  
 对类型为 `inner_allocator_type` 的存储对象的引用。  
  
##  <a name="a-namescopedallocatoradaptormaxsizemethoda--scopedallocatoradaptormaxsize-method"></a><a name="scoped_allocator_adaptor__max_size_method"></a>  scoped_allocator_adaptor::max_size 方法  
 确定可通过外部分配器分配的对象的最大数目。  
  
```cpp  
size_type max_size();
```  
  
### <a name="return-value"></a>返回值  
 `Outer_traits::max_size(outer_allocator())`  
  
##  <a name="a-namescopedallocatoradaptorouterallocatormethoda--scopedallocatoradaptorouterallocator-method"></a><a name="scoped_allocator_adaptor__outer_allocator_method"></a>  scoped_allocator_adaptor::outer_allocator 方法  
 检索对类型为 `outer_allocator_type` 的存储对象的引用。  
  
```cpp  
outer_allocator_type& outer_allocator() noexcept;  
const outer_allocator_type& outer_allocator() const noexcept;  
```  
  
### <a name="return-value"></a>返回值  
 对类型为 `outer_allocator_type` 的存储对象的引用。  
  
##  <a name="a-namescopedallocatoradaptorrebindstructa--scopedallocatoradaptorrebind-struct"></a><a name="scoped_allocator_adaptor__rebind_struct"></a>  scoped_allocator_adaptor::rebind 结构  
 将 `Outer::rebind\<Other>::other` 类型定义为 `scoped_allocator_adaptor\<Other, Inner...>` 的同义词。  
  
重新绑定结构 {  
   typedef Other_traits::rebind\<Other>  
   Other_alloc;  
   typedef scoped_allocator_adaptor\<Other_alloc, Inner...> other;  
   };  
  
##  <a name="a-namescopedallocatoradaptorscopedallocatoradaptorconstructora--scopedallocatoradaptorscopedallocatoradaptor-constructor"></a><a name="scoped_allocator_adaptor__scoped_allocator_adaptor_constructor"></a>  scoped_allocator_adaptor::scoped_allocator_adaptor 构造函数  
 构造 `scoped_allocator_adaptor` 对象。  
  
```cpp  
scoped_allocator_adaptor();

scoped_allocator_adaptor(const scoped_allocator_adaptor& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(
 const scoped_allocator_adaptor<Outer2, Inner...>& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(
 scoped_allocator_adaptor<Outer2, Inner...>&& right) noexcept;  
template <class Outer2>  
scoped_allocator_adaptor(Outer2&& al,  
    const Inner&... rest) noexcept;  
```  
  
### <a name="parameters"></a>参数  
 `right`  
 现有 `scoped_allocator_adaptor`。  
  
 `al`  
 要用作外部分配器的现有分配器。  
  
 `rest`  
 要用作内部分配器的分配器列表。  
  
### <a name="remarks"></a>备注  
 第一个构造函数默认构造其存储分配器对象。 后面的三个构造函数中的每一个都会从 `right` 中的相应对象构造其存储分配器对象。 最后一个构造函数从参数列表中相应参数构造其存储分配器对象。  
  
##  <a name="a-namescopedallocatoradaptorselectoncontainercopyconstructionmethoda--scopedallocatoradaptorselectoncontainercopyconstruction-method"></a><a name="scoped_allocator_adaptor__select_on_container_copy_construction_method"></a>  scoped_allocator_adaptor::select_on_container_copy_construction 方法  
 创建一个新的 `scoped_allocator_adaptor` 对象，其中每个存储分配器对象都可通过调用每个相应分配器的 `select_on_container_copy_construction` 进行初始化。  
  
```cpp  
scoped_allocator_adaptor select_on_container_copy_construction();
```  
  
### <a name="return-value"></a>返回值  
 实际上，此方法将返回 `scoped_allocator_adaptor(Outer_traits::select_on_container_copy_construction(*this), inner_allocator().select_on_container_copy_construction())`。 结果为新的 `scoped_allocator_adaptor` 对象，其中每个存储分配器对象都可通过调用相应分配器 `al` 的 `al.select_on_container_copy_construction()` 进行初始化。  
  
## <a name="see-also"></a>另请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)




