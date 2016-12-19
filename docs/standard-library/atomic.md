---
title: "&lt;atomic&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<atomic>"
  - "atomic/std::atomic_int_least32_t"
  - "atomic/std::atomic_ullong"
  - "atomic/std::atomic_ptrdiff_t"
  - "atomic/std::atomic_char16_t"
  - "atomic/std::atomic_schar"
  - "atomic/std::atomic_ulong"
  - "atomic/std::atomic_uint_fast32_t"
  - "atomic/std::atomic_uint8_t"
  - "atomic/std::atomic_int32_t"
  - "atomic/std::atomic_uint_fast64_t"
  - "atomic/std::atomic_uint32_t"
  - "atomic/std::atomic_int16_t"
  - "atomic/std::atomic_uintmax_t"
  - "atomic/std::atomic_intmax_t"
  - "atomic/std::atomic_long"
  - "atomic/std::atomic_int"
  - "atomic/std::atomic_uint_least8_t"
  - "atomic/std::atomic_size_t"
  - "atomic/std::atomic_uint_fast16_t"
  - "atomic/std::atomic_wchar_t"
  - "atomic/std::atomic_int_fast64_t"
  - "atomic/std::atomic_uint_fast8_t"
  - "atomic/std::atomic_int_fast8_t"
  - "atomic/std::atomic_intptr_t"
  - "atomic/std::atomic_uint"
  - "atomic/std::atomic_uint16_t"
  - "atomic/std::atomic_char32_t"
  - "atomic/std::atomic_uint64_t"
  - "atomic/std::atomic_ushort"
  - "atomic/std::atomic_int_least16_t"
  - "atomic/std::atomic_char"
  - "atomic/std::atomic_uint_least32_t"
  - "atomic/std::atomic_uintptr_t"
  - "atomic/std::atomic_short"
  - "atomic/std::atomic_llong"
  - "atomic/std::atomic_uint_least16_t"
  - "atomic/std::atomic_int_fast16_t"
  - "atomic/std::atomic_int_least8_t"
  - "atomic/std::atomic_int_least64_t"
  - "atomic/std::atomic_int_fast32_t"
  - "atomic/std::atomic_uchar"
  - "atomic/std::atomic_int8_t"
  - "atomic/std::atomic_int64_t"
  - "atomic/std::atomic_uint_least64_t"
dev_langs: 
  - "C++"
ms.assetid: e79a6b9f-52ff-48da-9554-654c4e1999f6
caps.latest.revision: 22
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;atomic&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定义类模板类，并且使用创建支持原子操作的类型。  
  
## 语法  
  
```cpp  
#include <atomic>  
```  
  
## 备注  
  
> [!NOTE]
>  使用 **\/clr** 或 **\/clr:pure**中，在编译代码，此头阻止。  
  
 原子操作具有帮助您使用多线程正确操作对象，而无需使用锁 mutex 的两个主要属性。  
  
-   由于操作是原子的不可分割，同一对象的第二个原子操作从不同的线程可以将第原子操作前后仅获取对象的状态。  
  
-   根据其参数，[memory\_order](../Topic/memory_order%20Enum.md) 原子操作在同一线程上建立对其他原子操作的效果可见性的要求。  因此，它不允许违反的顺序要求优化的。  
  
 在一些平台上，可以有效地实现这些类型的原子操作可能是不可行的，而无需使用 `mutex` 锁。  则对该类型使用的原子操作不锁定，原子类型是 *无锁*。  
  
 [atomic\_flag](../standard-library/atomic-flag-structure.md) 类提供保存 `bool` 标志的更小的原子类型。  其操作始终是无锁。  
  
 类模板 `atomic<Ty>` 存储其参数类型 `Ty` 对象并提供对该的原子访问存储的值。  可以实例化该使用 [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)，可以将使用 [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) 以及相等的任何测试类型。  具体来说，可以用于满足这些要求，并且在很多情况下，具有浮点类型的用户定义类型。  
  
 模板还有一组整型的专用化和指针的一部分专用化。  这些提供主要通过模板专用化不可用的附加操作。  
  
## 指针专用化  
 `atomic<Ty *>` 部分专用化适用于任何指针类型。  对指针算法的方法。  
  
## 整型专用化  
 `atomic<integral>` 专适用于所有整数类型。  这些提供主要通过模板不可用的附加操作。  
  
 每个 `atomic<integral>` 类型都有可以使用 `if directive` 中位于编译时的相应宏对该类型的操作是否是无锁。  如果宏的值为零，在类型的操作不是无锁。  如果值为 1，所以操作可能是空闲，锁定，并且需要一个运行时检查。  如果值为 2，所以操作是无锁。  可以使用函数 `atomic_is_lock_free` 确定运行时在类型的操作是否是无锁。  
  
 对于每整型，则管理该整数类型对象的相应一个原子类型。  每个 `atomic_integral` 类型都有同一组成员函数与 `atomic<Ty>` 对应的实例化，并且可以传递到任何非成员原子函数。  
  
|`atomic_integral` 类型|整型|`atomic_is_lock_free` 宏|  
|--------------------------|--------|-----------------------------|  
|`atomic_char`|`char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_schar`|`signed char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_uchar`|`unsigned char`|`ATOMIC_CHAR_LOCK_FREE`|  
|`atomic_char16_t`|`char16_t`|`ATOMIC_CHAR16_T_LOCK_FREE`|  
|`atomic_char32_t`|`char32_t`|`ATOMIC_CHAR32_T_LOCK_FREE`|  
|`atomic_wchar_t`|`wchar_t`|`ATOMIC_WCHAR_T_LOCK_FREE`|  
|`atomic_short`|`short`|`ATOMIC_SHORT_LOCK_FREE`|  
|`atomic_ushort`|`unsigned short`|`ATOMIC_SHORT_LOCK_FREE`|  
|`atomic_int`|`int`|`ATOMIC_INT_LOCK_FREE`|  
|`atomic_uint`|`unsigned int`|`ATOMIC_INT_LOCK_FREE`|  
|`atomic_long`|`long`|`ATOMIC_LONG_LOCK_FREE`|  
|`atomic_ulong`|`unsigned long`|`ATOMIC_LONG_LOCK_FREE`|  
|`atomic_llong`|`long long`|`ATOMIC_LLONG_LOCK_FREE`|  
|`atomic_ullong`|`unsigned long long`|`ATOMIC_LLONG_LOCK_FREE`|  
  
 Typedef 名称以原子模板的专用化在标题 \<inttypes.h 定义的一些存在的类型。\>  
  
|原子类型|Typedef 名称|  
|----------|----------------|  
|`atomic_int8_t`|`atomic<int8_t>`|  
|`atomic_uint8_t`|`atomic<uint8_t>`|  
|`atomic_int16_t`|`atomic<int16_t>`|  
|`atomic_uint16_t`|`atomic<uint16_t>`|  
|`atomic_int32_t`|`atomic<int32_t>`|  
|`atomic_uint32_t`|`atomic<uint32_t>`|  
|`atomic_int64_t`|`atomic<int64_t>`|  
|`atomic_uint64_t`|`atomic<uint64_t>`|  
|`atomic_int_least8_t`|`atomic<int_least8_t>`|  
|`atomic_uint_least8_t`|`atomic<uint_least8_t>`|  
|`atomic_int_least16_t`|`atomic<int_least16_t>`|  
|`atomic_uint_least16_t`|`atomic<uint_least16_t>`|  
|`atomic_int_least32_t`|`atomic<int_least32_t>`|  
|`atomic_uint_least32_t`|`atomic<uint_least32_t>`|  
|`atomic_int_least64_t`|`atomic<int_least64_t>`|  
|`atomic_uint_least64_t`|`atomic<uint_least64_t>`|  
|`atomic_int_fast8_t`|`atomic<int_fast8_t>`|  
|`atomic_uint_fast8_t`|`atomic<uint_fast8_t>`|  
|`atomic_int_fast16_t`|`atomic<int_fast16_t>`|  
|`atomic_uint_fast16_`|`atomic<uint_fast16_t>`|  
|`atomic_int_fast32_t`|`atomic<int_fast32_t>`|  
|`atomic_uint_fast32_t`|`atomic<uint_fast32_t>`|  
|`atomic_int_fast64_t`|`atomic<int_fast64_t>`|  
|`atomic_uint_fast64_t`|`atomic<uint_fast64_t>`|  
|`atomic_intptr_t`|`atomic<intptr_t>`|  
|`atomic_uintptr_t`|`atomic<uintptr_t>`|  
|`atomic_size_t`|`atomic<size_t>`|  
|`atomic_ptrdiff_t`|`atomic<ptrdiff_t>`|  
|`atomic_intmax_t`|`atomic<intmax_t>`|  
|`atomic_uintmax_t`|`atomic<uintmax_t>`|  
  
## 结构  
  
|Name|说明|  
|----------|--------|  
|[atomic 结构](../standard-library/atomic-structure.md)|描述对存储的值的原子操作的对象。|  
|[atomic\_flag 结构](../standard-library/atomic-flag-structure.md)|描述基本设置和清除 `bool` 标志的对象。|  
  
## 枚举  
  
|Name|说明|  
|----------|--------|  
|[memory\_order 枚举](../Topic/memory_order%20Enum.md)|提供用于内存位置的同步操作的符号名。  这些操作会影响一个线程上的分配如何在另一个中变得可见。|  
  
## 函数  
 在下面列表，在 `_explicit` 结束的函数不具有相应 `_explicit`的语义，但它们具有 `memory_order_seq_cst`的隐式 [memory\_order](../Topic/memory_order%20Enum.md) 参数。  
  
|Name|说明|  
|----------|--------|  
|[atomic\_compare\_exchange\_strong 函数](../Topic/atomic_compare_exchange_strong%20Function.md)|执行基本比较和交换操作。|  
|[atomic\_compare\_exchange\_strong\_explicit 函数](../Topic/atomic_compare_exchange_strong_explicit%20Function.md)|执行基本比较和交换操作。|  
|[atomic\_compare\_exchange\_weak 函数](../Topic/atomic_compare_exchange_weak%20Function.md)|执行“原子比较和交换”  操作。|  
|[atomic\_compare\_exchange\_weak\_explicit 函数](../Topic/atomic_compare_exchange_weak_explicit%20Function.md)|执行“原子比较和交换”  操作。|  
|[atomic\_exchange 函数](../Topic/atomic_exchange%20Function.md)|替换现有存储的值。|  
|[atomic\_exchange\_explicit 函数](../Topic/atomic_exchange_explicit%20Function.md)|替换现有存储的值。|  
|[atomic\_fetch\_add 函数](../Topic/atomic_fetch_add%20Function.md)|添加一个值到现有的存储的值。|  
|[atomic\_fetch\_add\_explicit 函数](../Topic/atomic_fetch_add_explicit%20Function.md)|添加一个值到现有的存储的值。|  
|[atomic\_fetch\_and 函数](../Topic/atomic_fetch_and%20Function.md)|按位对某个指定与现有存储的值的 `and`。|  
|[atomic\_fetch\_and\_explicit 函数](../Topic/atomic_fetch_and_explicit%20Function.md)|按位对某个指定与现有存储的值的 `and`。|  
|[atomic\_fetch\_or 函数](../Topic/atomic_fetch_or%20Function.md)|按位对某个指定与现有存储的值的 `or`。|  
|[atomic\_fetch\_or\_explicit 函数](../Topic/atomic_fetch_or_explicit%20Function.md)|按位对某个指定与现有存储的值的 `or`。|  
|[atomic\_fetch\_sub 函数](../Topic/atomic_fetch_sub%20Function.md)|从现有存储的值减去一个值。|  
|[atomic\_fetch\_sub\_explicit 函数](../Topic/atomic_fetch_sub_explicit%20Function.md)|从现有存储的值减去一个值。|  
|[atomic\_fetch\_xor 函数](../Topic/atomic_fetch_xor%20Function.md)|按位对某个指定与现有存储的值的 `exclusive or`。|  
|[atomic\_fetch\_xor\_explicit 函数](../Topic/atomic_fetch_xor_explicit%20Function.md)|按位对某个指定与现有存储的值的 `exclusive or`。|  
|[atomic\_flag\_clear 函数](../Topic/atomic_flag_clear%20Function.md)|将一个对象的 `atomic_flag` 标志设置为 `false`。|  
|[atomic\_flag\_clear\_explicit 函数](../Topic/atomic_flag_clear_explicit%20Function.md)|将一个对象的 `atomic_flag` 标志设置为 `false`。|  
|[atomic\_flag\_test\_and\_set 函数](../Topic/atomic_flag_test_and_set%20Function.md)|将一个对象的 `atomic_flag` 标志设置为 `true`。|  
|[atomic\_flag\_test\_and\_set\_explicit 函数](../Topic/atomic_flag_test_and_set_explicit%20Function.md)|将一个对象的 `atomic_flag` 标志设置为 `true`。|  
|[atomic\_init 函数](../Topic/atomic_init%20Function.md)|设置 `atomic` 对象中存储的值。|  
|[atomic\_is\_lock\_free 函数](../Topic/atomic_is_lock_free%20Function.md)|指定在指定对象的原子操作是无锁。|  
|[atomic\_load 函数](../Topic/atomic_load%20Function.md)|基本检索值。|  
|[atomic\_load\_explicit 函数](../Topic/atomic_load_explicit%20Function.md)|基本检索值。|  
|[atomic\_signal\_fence 函数](../Topic/atomic_signal_fence%20Function.md)|是在调用线程上建立范围之间的排序。内存要求有通知处理程序将执行在同一线程的 *大小*。|  
|[atomic\_store 函数](../Topic/atomic_store%20Function.md)|基本存储值。|  
|[atomic\_store\_explicit 函数](../Topic/atomic_store_explicit%20Function.md)|基本存储值。|  
|[atomic\_thread\_fence 函数](../Topic/atomic_thread_fence%20Function.md)|为建立顺序要求的内存与其他范围的 *大小*。|  
|[kill\_dependency 函数](../Topic/kill_dependency%20Function.md)|中断一可能的依赖关系，这些依赖关系链。|  
  
## 请参阅  
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)   
 [标准模板库](../misc/standard-template-library.md)