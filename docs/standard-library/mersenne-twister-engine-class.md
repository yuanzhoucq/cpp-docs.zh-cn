---
title: "mersenne_twister_engine 类 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::mersenne_twister_engine
dev_langs:
- C++
helpviewer_keywords:
- mersenne_twister_engine class
ms.assetid: 7ee968fa-a1cc-450f-890f-7305de062685
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15294f0372a21c3ce8efe1626c30d1a3d6db23be
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="mersennetwisterengine-class"></a>mersenne_twister_engine 类
根据梅森旋转算法生成高质量的随机整数序列。  
  
## <a name="syntax"></a>语法  
  
```  
template <class UIntType,   
    size_t W, size_t N, size_t M, size_t R,  
    UIntType A, size_t U, UIntType D, size_t S,  
    UIntType B, size_t T, UIntType C, size_t L, UIntType F>  
class mersenne_twister_engine;  
```  
  
#### <a name="parameters"></a>参数  
 `UIntType`  
 无符号的整数结果类型。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。  
  
 `W`  
 **字大小**。 状态序列的每个字的大小（以字节为单位）。 **前提条件**：`2u < W ≤ numeric_limits<UIntType>::digits`  
  
 `N`  
 **状态大小**。 状态序列中的元素（值）数量。  
  
 `M`  
 **移位大小**。 每次旋转过程中要跳过的元素数量。 **前提条件**：`0 < M ≤ N`  
  
 `R`  
 **掩码位**。 **前提条件**：`R ≤ W`  
  
 `A`  
 **XOR 掩码**。 **前置条件**：`A ≤ (1u<<W) - 1u`  
  
 `U`, `S`, `T`, `L`  
 **调和移位参数**。 在混合（调和）过程中用作移位值。 前置条件：`U,S,T,L ≤ W`  
  
 `D`, `B`, `C`  
 **调和位掩码参数**。 在混合（调和）过程中用作位掩码值。 前置条件：`D,B,C ≤ (1u<<W) - 1u`  
  
 `F`  
 **初始化乘法器**。 用于帮助初始化序列。 前置条件：`F ≤ (1u<<W) - 1u`  
  
## <a name="members"></a>Members  
  
||||  
|-|-|-|  
|`mersenne_twister_engine::mersenne_twister_engine`|`mersenne_twister_engine::min`|`mersenne_twister_engine::discard`|  
|`mersenne_twister_engine::operator()`|`mersenne_twister_engine::max`|`mersenne_twister_engine::seed`|  
  
 `default_seed` 是定义为 `5489u` 且用作 `mersenne_twister_engine::seed` 和单个值的构造函数的默认参数值的成员常量。  
  
 有关引擎成员的详细信息，请参阅 [\<random>](../standard-library/random.md)。  
  
## <a name="remarks"></a>备注  
 此模板类描述了返回闭区间 [ `0`, `2`<sup>W</sup> - `1`] 上的值的随机数引擎。 它将保留 `W * (N - 1) + R` 位的较大整数值。 它从此较大值中一次提取 `W` 位，当它已使用所有的位时，它将通过对这些位进行移位和混合来旋转该较大值，以便生成可从中进行提取的新位集。 如果已调用 `N` 至少 `W` 次，则引擎的状态是所使用的最后一个 `operator()` `N` 位的值，否则是已使用的 `M` `W` 位的值和种子的最后一个 `N - M` 值。  
  
 通过使用移位值 `N` 和 `M`、旋转值 `R`，以及有条件的 XOR 掩码 `A` 定义的旋转生成的反馈移位寄存器，生成器将旋转它保留的较大值。 另外，将根据由值 `U`、`D`、`S`、`B`、`T`、`C` 和 `L` 定义的位混合矩阵，来混合（调和）原始移位寄存器。  
  
 模板自变量 `UIntType` 必须大到足以保留最多 `2`<sup>W</sup> - `1` 个值。 其他模板参数的值必须满足以下要求：`2u < W, 0 < M, M ≤ N, R ≤ W, U ≤ W, S ≤ W, T ≤ W, L ≤ W, W ≤ numeric_limits<UIntType>::digits, A ≤ (1u<<W) - 1u, B ≤ (1u<<W) - 1u, C ≤ (1u<<W) - 1u, D ≤ (1u<<W) - 1u, and F ≤ (1u<<W) - 1u`。  
  
 虽然可以从此引擎直接构造生成器，但是建议使用以下预定义的 typedef 中的一个：  
  
 `mt19937`：32 位梅森旋转引擎（Matsumoto 和 Nishimura，1998）。  
  
```  
typedef mersenne_twister_engine<unsigned int, 32, 624, 397,   
    31, 0x9908b0df,   
    11, 0xffffffff,   
    7, 0x9d2c5680,   
    15, 0xefc60000,   
    18, 1812433253> mt19937;  
```  
  
 `mt19937_64`：64 位梅森旋转引擎（Matsumoto 和 Nishimura，2000）。  
  
```  
typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,   
    31, 0xb5026f5aa96619e9ULL,   
    29, 0x5555555555555555ULL,   
    17, 0x71d67fffeda60000ULL,   
    37, 0xfff7eee000000000ULL,   
    43, 6364136223846793005ULL> mt19937_64;  
```  
  
 有关梅森旋转算法的详细信息，请参阅 Wikipedia 文章[梅森旋转](http://go.microsoft.com/fwlink/p/?linkid=402356)。  
  
## <a name="example"></a>示例  
 有关代码示例，请参阅 [\<random>](../standard-library/random.md)。  
  
## <a name="requirements"></a>惠?  
 **标头：**\<random>  
  
 **命名空间：** std  
  
## <a name="see-also"></a>请参阅  
 [\<random>](../standard-library/random.md)

