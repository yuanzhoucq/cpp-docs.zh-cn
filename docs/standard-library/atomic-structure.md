---
title: "atomic 结构 | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- atomic/std::atomic
dev_langs:
- C++
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4ecf60434799708acab4726a95380a2d3b9dbb3a
ms.openlocfilehash: fd21d2fe59dc7db7670fb94fde6d169603bbf6d1
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="atomic-structure"></a>atomic 结构
描述对类型 `Ty` 的存储值执行原子操作的对象。  
  
## <a name="syntax"></a>语法  
  
```
template <class Ty>
struct atomic;
```  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[atomic](http://msdn.microsoft.com/Library/a538c43f-4d48-4308-ae1b-bab1839bccb8)|构造一个原子对象。|  
  
### <a name="public-operators"></a>公共运算符  
  
|名称|说明|  
|----------|-----------------|  
|[atomic::operator Ty 运算符](http://msdn.microsoft.com/Library/a366c700-c7a0-4bcb-8eb4-4b57dfaea065)|读取并返回存储的值。 ([atomic:: load](http://msdn.microsoft.com/Library/05212726-cf8a-46fe-83d2-c16ac2abb7d1))|  
|[atomic::operator= 运算符](http://msdn.microsoft.com/Library/fe161d57-47ae-4bad-92bf-ce32ac8d5953)|使用指定值替换存储值。 ([atomic:: store](http://msdn.microsoft.com/Library/84759413-d664-47ef-a1f3-a73c5a62007b))|  
|[atomic::operator++ 运算符](http://msdn.microsoft.com/Library/492959e9-1ea8-4e02-a031-82b1b92e91a0)|增加存储值。 仅由整型和指针专用化使用。|  
|[atomic::operator+= 运算符](http://msdn.microsoft.com/Library/9ec97aa2-c9d7-436b-943d-2989eb2617dd)|将指定的值添加到存储值。 仅由整型和指针专用化使用。|  
|[atomic::operator-- 运算符](http://msdn.microsoft.com/Library/ad7c1ea7-1f6d-4a54-bf26-07630f749864)|减小存储值。 仅由整型和指针专用化使用。|  
|[atomic::operator-= 运算符](http://msdn.microsoft.com/Library/902d0d9f-88fd-4500-aa2d-1e50f443e77c)|从存储值减去指定的值。 仅由整型和指针专用化使用。|  
|[atomic::operator&= 运算符](http://msdn.microsoft.com/Library/90e730ac-12e1-4abb-98f5-4eadd6861a89)|对指定值和存储值执行按位 `and`。 仅由整型专用化使用。|  
|[atomic::operator&#124;= 运算符](http://msdn.microsoft.com/Library/f105eacc-31a6-4906-abba-f1cf013599b2)|对指定值和存储值执行按位 `or`。 仅由整型专用化使用。|  
|[atomic::operator^= 运算符](http://msdn.microsoft.com/Library/f2a4da9d-67e8-4249-9161-9998e72a33c2)|对指定值和存储值执行按位 `exclusive or`。 仅由整型专用化使用。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[compare_exchange_strong](http://msdn.microsoft.com/Library/47bbf894-b28c-4ece-959e-67b3863cf4ed)|对 `this` 执行 `atomic_compare_and_exchange` 操作并返回结果。|  
|[compare_exchange_weak](http://msdn.microsoft.com/Library/e15e421a-f7a3-4272-993a-f487d2242e4f)|对 `this` 执行 `weak_atomic_compare_and_exchange` 操作并返回结果。|  
|[fetch_add](http://msdn.microsoft.com/Library/c68b91f2-6e8a-4ffa-8991-6bb6d466e1f3)|将指定的值添加到存储值。|  
|[fetch_and](http://msdn.microsoft.com/Library/a9c83001-b72c-4085-9640-f63f866714b9)|对指定值和存储值执行按位 `and`。|  
|[fetch_or](http://msdn.microsoft.com/Library/4c532f7f-80c5-432a-b34b-48feacab8dca)|对指定值和存储值执行按位 `or`。|  
|[fetch_sub](http://msdn.microsoft.com/Library/8cc80d4b-0942-45a3-9db8-bbf339a903e4)|从存储值减去指定的值。|  
|[fetch_xor](http://msdn.microsoft.com/Library/92bbaff8-ee29-4a1e-aee4-d9d405285bfe)|对指定值和存储值执行按位 `exclusive or`。|  
|[is_lock_free](http://msdn.microsoft.com/Library/b99d5130-cdda-40a2-b14c-152b13a8ba45)|指定 `this` 上的原子操作是否为*无锁*。 如果对类型执行的原子操作都没有使用锁，则原子类型为*无锁*。|  
|[负载](http://msdn.microsoft.com/Library/05212726-cf8a-46fe-83d2-c16ac2abb7d1)|读取并返回存储的值。|  
|[应用商店](http://msdn.microsoft.com/Library/84759413-d664-47ef-a1f3-a73c5a62007b)|使用指定值替换存储值。|  
  
## <a name="remarks"></a>备注  
 类型 `Ty` 必须*完全可复制*。 即，使用 [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) 复制其字节必须生成一个与原始对象相等的有效 `Ty` 对象。 `compare_exchange_weak` 和 `compare_exchange_strong` 成员函数使用 [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) 来确定两个`Ty` 值是否相等。 这些函数将不会使用 `Ty`-defined `operator==`。 `atomic` 的成员函数使用 `memcpy` 复制类型 `Ty` 的值。  
  
 部分专用化 `atomic<Ty *>`，对所有指针类型都存在。 通过专用化可将偏移量添加到托管的指针值或者从其中减去该偏移量。 该算术运算采用类型为 `ptrdiff_t` 的参数，并根据 `Ty` 的大小调整该参数，以与普通地址算术保持一致。  
  
 对于除 `bool` 之外的每个整型类型都均存在专用化。 每个专用化为原子算术和逻辑运算提供了一组丰富的方法。  
  
||||  
|-|-|-|  
|`atomic<char>`|`atomic<signed char>`|`atomic<unsigned char>`|  
|`atomic<char16_t>`|`atomic<char32_t>`|`atomic<wchar_t>`|  
|`atomic<short>`|`atomic<unsigned short>`|`atomic<int>`|  
|`atomic<unsigned int>`|`atomic<long>`|`atomic<unsigned long>`|  
|`atomic<long long>`|`atomic<unsigned long long>`|  
  
 整型专用化派生自相应的 `atomic_``integral` 类型。 例如，`atomic<unsigned int>` 派生自 `atomic_uint`。  
  
## <a name="requirements"></a>要求  
 **标头︰** \<原子 >  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [\<atomic>](../standard-library/atomic.md)   
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)




