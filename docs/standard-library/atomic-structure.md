---
title: "atomic 结构 | Microsoft Docs"
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
  - "atomic/std::atomic"
dev_langs: 
  - "C++"
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
caps.latest.revision: 10
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atomic 结构
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述对类型 `Ty`的存储值的基本操作的对象。  
  
## 语法  
  
```  
template <class Ty>  
struct atomic;  
```  
  
## 成员  
  
### 公共构造函数  
  
|Name|说明|  
|----------|--------|  
|[atomic::atomic 构造函数](../Topic/atomic::atomic%20Constructor.md)|构造一个基对象。|  
  
### 公共运算符  
  
|Name|说明|  
|----------|--------|  
|[atomic::operator Ty 运算符](../Topic/atomic::operator%20Ty%20Operator.md)|读取并返回该存储的值。\([atomic::load 方法](../Topic/atomic::load%20Method.md)\)|  
|[atomic::operator\= 运算符](../Topic/atomic::operator=%20Operator.md)|使用指定值替换存储的值。\([atomic::store 方法](../Topic/atomic::store%20Method.md)\)|  
|||  
|[atomic::operator\+\+ Operator](../Topic/atomic::operator++%20Operator.md)|递增存储的值。  仅使用由整型和指针专用化。|  
|[atomic::operator\+\= 运算符](../Topic/atomic::operator+=%20Operator.md)|为存储值添加指定值。  仅使用由整型和指针专用化。|  
|[atomic::operator\-\- 运算符](../Topic/atomic::operator--%20Operator.md)|递减存储的值。  仅使用由整型和指针专用化。|  
|[atomic::operator\-\= 运算符](../Topic/atomic::operator-=%20Operator.md)|从存储的值减去指定的值。  仅使用由整型和指针专用化。|  
|[atomic::operator&\= 运算符](../Topic/atomic::operator&=%20Operator.md)|对指定的值执行按位`and` 运算并存储该值 。  只使用完整的专业化。|  
|[atomic::operator&#124;\= 运算符](../Topic/atomic::operator%7C=%20Operator.md)|对指定的值执行按位`or` 运算并存储该值 。  只使用完整的专业化。|  
|[atomic::operator^\= 运算符](../Topic/atomic::operator%5E=%20Operator.md)|对指定的值执行按位`exclusive or` 运算并存储该值 。  只使用完整的专业化。|  
  
### 公共方法  
  
|Name|说明|  
|----------|--------|  
|[atomic::compare\_exchange\_strong 方法](../Topic/atomic::compare_exchange_strong%20Method.md)|对 `this` 执行`atomic_compare_and_exchange` 操作并返回结果。|  
|[atomic::compare\_exchange\_weak 方法](../Topic/atomic::compare_exchange_weak%20Method.md)|对 `this` 执行`weak_atomic_compare_and_exchange` 操作并返回结果。|  
|[atomic::fetch\_add 方法](../Topic/atomic::fetch_add%20Method.md)|为存储值添加指定值。|  
|[atomic::fetch\_and 方法](../Topic/atomic::fetch_and%20Method.md)|对指定的值执行按位`and` 运算并存储该值 。|  
|[atomic::fetch\_or 方法](../Topic/atomic::fetch_or%20Method.md)|对指定的值执行按位`or` 运算并存储该值 。|  
|[atomic::fetch\_sub 方法](../Topic/atomic::fetch_sub%20Method.md)|从存储的值减去指定的值。|  
|[atomic::fetch\_xor 方法](../Topic/atomic::fetch_xor%20Method.md)|对指定的值执行按位`exclusive or` 运算并存储该值 。|  
|[atomic::is\_lock\_free 方法](../Topic/atomic::is_lock_free%20Method.md)|指定在 `this` 的基本操作是否 *任意的锁*。  如果该类型的基本操作不使用锁，基类型是 *任意的锁*。|  
|[atomic::load 方法](../Topic/atomic::load%20Method.md)|读取并返回该存储的值。|  
|[atomic::store 方法](../Topic/atomic::store%20Method.md)|使用指定值替换存储的值。|  
  
## 备注  
 该类型 `Ty` 必须为 *常用地可复制*。  即使用 [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) 复制其字节必须生成与原始对象相等的有效 `Ty` 对象。  `compare_exchange_weak` 和 `compare_exchange_strong` 成员函数使用 [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) 确定两个 `Ty` 值是否相等。  这些功能将不使用 `Ty`\-定义的 `operator==`。  `atomic` 的成员函数使用 `memcpy` 复制类型 `Ty`的值。  
  
 部分专用化，`atomic<Ty *>`，为所有指针类型存在。  从该文件中专用化允许向托管指针值增加或减少一个偏移。  算术运算采用类型 `ptrdiff_t` 的参数并根据 `Ty` 的大小使其与普通的地址算法一致。  
  
 专用化为除 `bool`的每个整型存在。  每个专用化对于基本算术和逻辑操作提供了一组丰富的方法。  
  
||||  
|-|-|-|  
|`atomic<char>`|`atomic<signed char>`|`atomic<unsigned char>`|  
|`atomic<char16_t>`|`atomic<char32_t>`|`atomic<wchar_t>`|  
|`atomic<short>`|`atomic<unsigned short>`|`atomic<int>`|  
|`atomic<unsigned int>`|`atomic<long>`|`atomic<unsigned long>`|  
|`atomic<long long>`|`atomic<unsigned long long>`|  
  
 集成专用化从相应的 `atomic_``integral` 类型派生。  例如，`atomic<unsigned int>` 派生自 `atomic_uint`。  
  
## 要求  
 **标头：**原子  
  
 **命名空间:** std  
  
## 请参阅  
 [\<atomic\>](../standard-library/atomic.md)   
 [头文件引用](../standard-library/cpp-standard-library-header-files.md)