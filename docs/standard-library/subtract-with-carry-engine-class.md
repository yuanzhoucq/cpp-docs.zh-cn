---
title: "subtract_with_carry_engine 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- subtract_with_carry_engine
- random/std::subtract_with_carry_engine
- random/std::subtract_with_carry_engine::default_seed
- random/std::subtract_with_carry_engine::discard
- random/std::subtract_with_carry_engine::min
- random/std::subtract_with_carry_engine::max
- random/std::subtract_with_carry_engine::seed
dev_langs:
- C++
helpviewer_keywords:
- subtract_with_carry_engine class
ms.assetid: 94a055f2-a620-4a22-ac34-c156924bab31
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.openlocfilehash: c73401963b231883d26aa45590a9cad305b13875
ms.contentlocale: zh-cn
ms.lasthandoff: 04/19/2017

---
# <a name="subtractwithcarryengine-class"></a>subtract_with_carry_engine 类
通过带进位减法（滞后型斐波那契）算法生成随机序列。  
  
## <a name="syntax"></a>语法  
  
```  
template <class UIntType, size_t W, size_t S, size_t R>  
class subtract_with_carry_engine;  
```  
  
#### <a name="parameters"></a>参数  
 `UIntType`  
 无符号的整数结果类型。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。  
  
 `W`  
 **字大小**。 状态序列的每个字的大小（以字节为单位）。 **前置条件**：`0 < W ≤ numeric_limits<UIntType>::digits`  
  
 `S`  
 **短滞后**。 整数值数。 **前置条件**：`0 < S < R`  
  
 `R`  
 **长滞后**。 确定生成的系列中的重复。  
  
## <a name="members"></a>成员  
  
||||  
|-|-|-|  
|`subtract_with_carry_engine::subtract_with_carry_engine`|`subtract_with_carry_engine::min`|`subtract_with_carry_engine::discard`|  
|`subtract_with_carry_engine::operator()`|`subtract_with_carry_engine::max`|`subtract_with_carry_engine::seed`|  
|`default_seed` 是定义为 `19780503u` 且用作 `subtract_with_carry_engine::seed` 和单个值的构造函数的默认参数值的成员常量。|||  
  
 有关引擎成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>备注  
 `substract_with_carry_engine` 模板类是基于 [linear_congruential_engine](../standard-library/linear-congruential-engine-class.md) 的改进。 这两个引擎的速度和结果的质量都不如 [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md)。  
  
 此引擎使用重复关系（*周期*）`x(i) = (x(i - R) - x(i - S) - cy(i - 1)) mod M`产生用户指定的无符号整型值，其中如果 `cy(i)`，则 `1` 包含值 `x(i - S) - x(i - R) - cy(i - 1) < 0`；如果 `0`，则 `M` 包含 `2`<sup>W</sup>。引擎状态是进位指示器加上 `R` 值。 如果已调用 `R` 至少 `operator()` 次，则这些值将包含返回的最后 `R` 个值，否则包含已返回的 `N` 个值和种子的最后 `R - N` 个值。  
  
 模板参数 `UIntType` 必须大到足以保留最多 `M - 1` 个值。  
  
 虽然可以从此引擎直接构造生成器，但也可以使用预定义的 typedef 之一：  
  
 `ranlux24_base`：用作 `ranlux24` 的基础。                   
`typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`  
  
 `ranlux48_base`：用作 `ranlux48` 的基础。                   
`typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`  
  
 有关带进位减法引擎算法的详细信息，请参阅 Wikipedia 文章 [Lagged Fibonacci generator](http://go.microsoft.com/fwlink/LinkId=402445)（滞后斐波纳契生成器）。  
  
## <a name="requirements"></a>要求  
 **标头：**\<random>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>另请参阅  
 [\<random>](../standard-library/random.md)


