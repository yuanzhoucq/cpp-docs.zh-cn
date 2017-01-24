---
title: "linear_congruential_engine 类 | Microsoft Docs"
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
  - "std.tr1.linear_congruential_engine"
  - "random/std::tr1::linear_congruential_engine"
  - "linear_congruential_engine"
  - "std::tr1::linear_congruential_engine"
  - "tr1.linear_congruential_engine"
  - "tr1::linear_congruential_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "linear_congruential_engine 类"
ms.assetid: 30e00ca6-1933-4701-9561-54f3e810a5a1
caps.latest.revision: 21
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# linear_congruential_engine 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过线性同余算法生成随机序列。  
  
## 语法  
  
```  
template<class UIntType, UIntType A, UIntType C, UIntType M>  
class linear_congruential_engine{  
public:  
    // types  
    typedef UIntType result_type;  
  
    // engine characteristics  
    static constexpr result_type multiplier = a;  
    static constexpr result_type increment = c;  
    static constexpr result_type modulus = m;  
    static constexpr result_type min() { return c == 0u ? 1u: 0u; }  
    static constexpr result_type max() { return m - 1u; }  
    static constexpr result_type default_seed = 1u;  
  
    // constructors and seeding functions  
    explicit linear_congruential_engine(result_type s = default_seed);  
    template<class Sseq> explicit linear_congruential_engine(Sseq& q);  
    void seed(result_type s = default_seed);  
    template<class Sseq> void seed(Sseq& q);  
  
    // generating functions  
    result_type operator()();  
    void discard(unsigned long long z);  
};  
```  
  
#### 参数  
 `UIntType`  
 无符号的整数结果类型。 有关可能的类型，请参阅 [\<random\>](../standard-library/random.md)。  
  
 `A`  
 **乘法器**。**前置条件**：请参阅“备注”部分。  
  
 `C`  
 **递增**。**前置条件**：请参阅“备注”部分。  
  
 `M`  
 **取模**。**前置条件**：请参阅“备注”。  
  
## 成员  
  
||||  
|-|-|-|  
|`linear_congruential_engine::linear_congruential_engine`|`linear_congruential_engine::min`|`linear_congruential_engine::discard`|  
|`linear_congruential_engine::operator()`|`linear_congruential_engine::max`|`linear_congruential_engine::seed`|  
  
 `default_seed` 是定义为 `1u` 且用作 `linear_congruential_engine::seed` 和单个值的构造函数的默认参数值的成员常量。  
  
 有关引擎成员的详细信息，请参阅 [\<random\>](../standard-library/random.md)。  
  
## 备注  
 `linear_congruential_engine` 模板类是最简单的生成器引擎，但不是最快速或质量最好的生成器引擎。[substract\_with\_carry\_engine](../standard-library/subtract-with-carry-engine-class.md) 是对此引擎的改进。 这两个引擎的速度和结果的质量都不如 [mersenne\_twister\_engine](../standard-library/mersenne-twister-engine-class.md)。  
  
 此引擎使用重复关系（*周期*）`x(i) = (A * x(i-1) + C) mod M` 产生用户指定的无符号整型值。  
  
 如果 `M` 为零，则用于此取模运算的值是 `numeric_limits<result_type>::max() + 1`。 引擎的状态是返回的最后一个值，或是种子值（如果尚未对 `operator()` 进行调用）。  
  
 如果 `M` 不为零，则模板参数 `A` 和 `C` 的值必须小于 `M`。  
  
 虽然可以直接构造生成器从此引擎，您还可以使用这些预定义的 typedef 之一。  
  
 `minstd_rand0`: 1988年最小标准引擎 （Lewis、 Goodman 和 Miller，1969年）。  
  
```  
typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;  
```  
  
 `minstd_rand`︰ 更新的最小标准引擎 `minstd_rand0` （Park、 Miller 和 Stockmeyer，1993年）。  
  
```  
typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;  
```  
  
 有关线性同余引擎算法的详细信息，请参阅 Wikipedia 文章 [线性同余生成器](http://go.microsoft.com/fwlink/?LinkId=402446)。  
  
## 要求  
 **标头：**\<random\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<random\>](../standard-library/random.md)