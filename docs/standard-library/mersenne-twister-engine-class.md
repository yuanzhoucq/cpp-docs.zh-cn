---
title: mersenne_twister_engine 类
ms.date: 11/04/2016
f1_keywords:
- random/std::mersenne_twister_engine
helpviewer_keywords:
- mersenne_twister_engine class
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
ms.openlocfilehash: 79613c76b3ea6dc15643e83a15d5bd6d90b60c6a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687700"
---
# <a name="mersenne_twister_engine-class"></a>mersenne_twister_engine 类

根据梅森旋转算法生成高质量的随机整数序列。

## <a name="syntax"></a>语法

```cpp
template <class UIntType,
    size_t W, size_t N, size_t M, size_t R,
    UIntType A, size_t U, UIntType D, size_t S,
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>
class mersenne_twister_engine;
```

### <a name="parameters"></a>参数

*UIntType* \
无符号的整数结果类型。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。

*W* \
**字大小**。 状态序列的每个字的大小（以字节为单位）。 **前提条件**：`2u < W ≤ numeric_limits<UIntType>::digits`

*N* \
**状态大小**。 状态序列中的元素（值）数量。

*M* \
**移位大小**。 每次旋转过程中要跳过的元素数量。 **前提条件**：`0 < M ≤ N`

*R*\
**掩码位**。 **前提条件**：`R ≤ W`

*一个*\
**XOR 掩码**。 **前提条件**：`A ≤ (1u<<W) - 1u`

*U*、 *S*、 *T*、 *L* \
**调和移位参数**。 在混合（调和）过程中用作移位值。 前置条件：`U,S,T,L ≤ W`

*D*、 *B*、 *C* \
**调和位掩码参数**。 在混合（调和）过程中用作位掩码值。 前置条件：`D,B,C ≤ (1u<<W) - 1u`

*F* \
**初始化乘法器**。 用于帮助初始化序列。 前置条件：`F ≤ (1u<<W) - 1u`

## <a name="members"></a>Members

||||
|-|-|-|
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|

`default_seed` 是定义为 `5489u` 且用作 `mersenne_twister_engine::seed` 和单个值的构造函数的默认参数值的成员常量。

有关引擎成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。

## <a name="remarks"></a>备注

此类模板描述了一个随机数字引擎，返回已关闭间隔 [`0`，`2`<sup>W</sup>  -  `1`] 的值。 它将保留 `W * (N - 1) + R` 位的较大整数值。 它从这个大值中一次提取*W*位，并且当它已使用所有位时，通过移动并混合该位来旋转大值，以便它具有一组要从中提取的新位。 如果 `operator()` 至少调用了*N*次，则引擎的状态为最后一个 `N` `W` 位值，否则为所使用的 `M` `W` 位值和种子的最后一个 `N - M` 值。

生成器使用移位值*N*和*M*、一个扭转值*R*和一个条件 XOR 掩码*a*定义的旋转，从而将它保留的大值。此外，根据由值*U*、 *D*、 *S*、 *B*、 *T*、 *C*和*L*定义的位硬编码矩阵，将原始移位寄存器的位打乱（调和）。

模板自变量 `UIntType` 必须大到足以保留最多 `2`<sup>W</sup> - `1` 个值。 其他模板参数的值必须满足以下要求：`2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`。

虽然可以从此引擎直接构造生成器，但是建议使用以下预定义的 typedef 中的一个：

`mt19937`：32 位梅森旋转引擎（Matsumoto 和 Nishimura，1998）。

```cpp
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,
    31, 0x9908b0df,
    11, 0xffffffff,
    7, 0x9d2c5680,
    15, 0xefc60000,
    18, 1812433253> mt19937;
```

`mt19937_64`：64 位梅森旋转引擎（Matsumoto 和 Nishimura，2000）。

```cpp
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,
    31, 0xb5026f5aa96619e9ULL,
    29, 0x5555555555555555ULL,
    17, 0x71d67fffeda60000ULL,
    37, 0xfff7eee000000000ULL,
    43, 6364136223846793005ULL> mt19937_64;
```

有关梅森旋转算法的详细信息，请参阅 Wikipedia 文章[梅森旋转](https://go.microsoft.com/fwlink/p/?linkid=402356)。

## <a name="example"></a>示例

有关代码示例，请参阅 [\<random>](../standard-library/random.md)。

## <a name="requirements"></a>要求

**标头：** \<random>

**命名空间:** std

## <a name="see-also"></a>请参阅

[\<random>](../standard-library/random.md)
