---
title: "pointer_traits 结构 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::pointer_traits::element_type
- memory/std::pointer_traits::pointer
- memory/std::pointer_traits
- memory/std::pointer_traits::difference_type
- memory/std::pointer_traits::rebind
- xmemory0/std::pointer_traits::element_type
- xmemory0/std::pointer_traits::pointer
- xmemory0/std::pointer_traits
- xmemory0/std::pointer_traits::difference_type
- xmemory0/std::pointer_traits::rebind
dev_langs:
- C++
ms.assetid: 545aecf1-3561-4859-8b34-603c079fe1b3
caps.latest.revision: 13
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
ms.openlocfilehash: 3a5633fa4c9f45629d655edf922d40b02b68aaca
ms.lasthandoff: 02/24/2017

---
# <a name="pointertraits-struct"></a>pointer_traits 结构
提供模板类 `allocator_traits` 对象所需信息，用于描述一个采用指针类型 `Ptr` 的分配器。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template <class Ptr>
struct pointer_traits;
```  
  
## <a name="remarks"></a>备注  
 Ptr 可以是 `Ty *` 类型的原始指针或具有以下属性的类。  
```  
struct Ptr
   { // describes a pointer type usable by allocators
   typedef Ptr pointer;
   typedef T1 element_type; // optional
   typedef T2 difference_type; // optional
   template <class Other>
   using rebind = typename Ptr<Other, Rest...>; // optional
   static pointer pointer_to(element_type& obj);
   // optional
   };  
```
### <a name="typedefs"></a>Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`typedef T2 difference_type`|如果 `Ptr::difference_type` 类型存在，则类型 `T2` 为此类型，否则为 `ptrdiff_t`。 如果 `Ptr` 是原始指针，则类型为 `ptrdiff_t`。|  
|`typedef T1 element_type`|如果 `Ptr::element_type` 类型存在，则类型 `T1` 为此类型，否则为 `Ty`。 如果 `Ptr` 是原始指针，则类型为 `Ty`。|  
|`typedef Ptr pointer`|类型为 `Ptr`。|  
  
### <a name="structs"></a>结构  
  
|名称|描述|  
|----------|-----------------|  
|`pointer_traits::rebind`|尝试将基础指针类型转换为指定类型。|  
  
### <a name="methods"></a>方法  
  
|名称|描述|  
|----------|-----------------|  
|[pointer_to](#pointer_traits__pointer_to_method)|将任意引用转换为 `Ptr` 类的对象。|  
  
## <a name="requirements"></a>要求  
 **标头：**\<memory>  
  
 **命名空间：** std  
  
##  <a name="a-namepointertraitspointertomethoda--pointerto"></a><a name="pointer_traits__pointer_to_method"></a>pointer_to  
 存在 `Ptr::pointer_to(obj)` 时，则为返回该函数的静态方法。 否则，无法将任意引用转换为 `Ptr` 类的对象。 如果 `Ptr` 是原始指针，则此方法将返回 `addressof(obj)`。  
  
```cpp  
static pointer pointer_to(element_type& obj);
```  
  
## <a name="see-also"></a>另请参阅  
 [\<memory>](../standard-library/memory.md)   
 [allocator_traits 类](../standard-library/allocator-traits-class.md)


