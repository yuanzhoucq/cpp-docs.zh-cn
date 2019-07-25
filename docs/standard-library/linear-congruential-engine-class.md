---
title: linear_congruential_engine 类
ms.date: 11/04/2016
f1_keywords:
- random/std::linear_congruential_engine
helpviewer_keywords:
- linear_congruential_engine class
ms.assetid: 30e00ca6-1933-4701-9561-54f3e810a5a1
ms.openlocfilehash: f5b448fbf158cf9e9cfb8331c6ec7a228859fffc
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447585"
---
# <a name="linearcongruentialengine-class"></a>linear_congruential_engine 类

通过线性同余算法生成随机序列。

## <a name="syntax"></a>语法

```cpp
class linear_congruential_engine{
   public:  // types
   typedef UIntType result_type;
   // engine characteristics
   static constexpr result_type multiplier = a;
   static constexpr result_type increment = c;
   static constexpr result_type modulus = m;
   static constexpr result_type min() { return c == 0u  1u: 0u; }
   static constexpr result_type max() { return m - 1u; }
   static constexpr result_type default_seed = 1u;
   // constructors and seeding functions
   explicit linear_congruential_engine(result_type s = default_seed);
   template <class Sseq>
   explicit linear_congruential_engine(Sseq& q);
   void seed(result_type s = default_seed);
   template <class Sseq>
   void seed(Sseq& q);
   // generating functions
   result_type operator()();
   void discard(unsigned long long z);
   };
```

### <a name="parameters"></a>参数

*UIntType*\
无符号的整数结果类型。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。

*的*\
**乘数**。 **前提条件**:请参阅备注部分。

*ANSI-C*\
**递增**。 **前提条件**:请参阅备注部分。

*年*\
**取模**。 **前提条件**:请参阅 "备注"。

## <a name="members"></a>成员

||||
|-|-|-|
|`linear_congruential_engine::linear_congruential_engine`|`linear_congruential_engine::min`|`linear_congruential_engine::discard`|
|`linear_congruential_engine::operator()`|`linear_congruential_engine::max`|`linear_congruential_engine::seed`|

`default_seed` 是定义为 `1u` 且用作 `linear_congruential_engine::seed` 和单个值的构造函数的默认参数值的成员常量。

有关引擎成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。

## <a name="remarks"></a>备注

`linear_congruential_engine` 模板类是最简单的生成器引擎，但不是最快速或质量最好的生成器引擎。 [substract_with_carry_engine](../standard-library/subtract-with-carry-engine-class.md) 是对此引擎的改进。 这两个引擎的速度和结果的质量都不如 [mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md)。

此引擎使用重复关系( *period*) `x(i) = (A * x(i-1) + C) mod M` 产生用户指定的无符号整型值。

如果*M*为零, 则用于此取模运算的值`numeric_limits<result_type>::max() + 1`是。 引擎的状态是返回的最后一个值，或是种子值（如果尚未对 `operator()` 进行调用）。

如果*M*不为零, 则模板参数*A*和*C*的值必须小于*M*。

虽然可以从此引擎直接构造生成器，但也可以使用其中一个预定义的 typedef。

`minstd_rand0`：1988 最小标准引擎（Lewis、Goodman 和 Miller，1969）。

```cpp
typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
```

`minstd_rand`：更新的最小标准引擎 `minstd_rand0`（Park、Miller 和 Stockmeyer，1993）。

```cpp
typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
```

有关线性同余引擎算法的详细信息，请参阅 Wikipedia 文章[线性同余生成器](https://go.microsoft.com/fwlink/p/?linkid=402446)。

## <a name="requirements"></a>要求

**标头：** \<random>

**命名空间：** std

## <a name="see-also"></a>请参阅

[\<random>](../standard-library/random.md)
