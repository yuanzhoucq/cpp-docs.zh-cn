---
title: "subtract_with_carry_engine 类 | Microsoft Docs"
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
  - "tr1.subtract_with_carry_engine"
  - "std::tr1::subtract_with_carry_engine"
  - "random/std::tr1::subtract_with_carry_engine"
  - "subtract_with_carry_engine"
  - "tr1::subtract_with_carry_engine"
  - "std.tr1.subtract_with_carry_engine"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "subtract_with_carry_engine 类"
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
caps.latest.revision: 20
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# subtract_with_carry_engine 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

通过带进位减法（滞后型斐波那契）算法生成随机序列。  
  
## 语法  
  
```  
template<class UIntType, size_t W, size_t S, size_t R>  
class subtract_with_carry_engine;  
```  
  
#### 参数  
 `UIntType`  
 无符号的整数结果类型。 有关可能的类型，请参阅 [\<random\>](../standard-library/random.md)。  
  
 `W`  
 **字大小**。 状态序列的每个字的大小（以字节为单位）。**前置条件**：`0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `S`  
 **短滞后**。 整数值数。**前置条件**：`0 < S < R`  
  
 `R`  
 **长滞后**。 确定生成的系列中的重复。  
  
## 成员  
  
||||  
|-|-|-|  
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|  
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|  
|`default_seed` 是定义为 `19780503u` 且用作 `subtract_with_carry_engine::seed` 和单个值的构造函数的默认参数值的成员常量。|||  
  
 有关引擎成员的详细信息，请参阅 [\<random\>](../standard-library/random.md)。  
  
## 备注  
 `substract_with_carry_engine` 模板类是 [linear\_congruential\_engine](../standard-library/linear-congruential-engine-class.md) 上的改进。 这两个引擎的速度和结果的质量都不如 [mersenne\_twister\_engine](../standard-library/mersenne-twister-engine-class.md)。  
  
 此引擎使用重复关系（*周期*）`x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M` 产生用户指定的无符号整型值，其中如果 `cy(i)`，则 `1` 包含值 `x(i - S) - x(i - R) - cy(i - 1) < 0`；如果 `0`，则 `M` 包含 `2`<sup>W</sup>。 引擎状态是进位指示器加上 `R` 值。 如果已调用 `R` 至少 `operator()` 次，则这些值将包含返回的最后 `R` 个值，否则包含已返回的 `N` 个值和种子的最后 `R - N` 个值。  
  
 模板参数 `UIntType` 必须大到足以保留最多 `M - 1` 个值。  
  
 虽然可以直接构造生成器从此引擎，您还可以使用这些预定义的 typedef 之一︰  
  
 `ranlux24_base`︰ 用作的基础 `ranlux24`。  
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`  
  
 `ranlux48_base`︰ 用作的基础 `ranlux48`。  
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`  
  
 有关带进位引擎算法的详细信息，请参阅 Wikipedia 文章 [滞后型斐波那契生成器](http://go.microsoft.com/fwlink/?LinkId=402445)。  
  
## 要求  
 **标头：**\<random\>  
  
 **命名空间:** std  
  
## 请参阅  
 [\<random\>](../standard-library/random.md)