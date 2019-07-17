---
title: '&lt;random&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 87b640d4f3aa3fbfa23ad5603d84102301e71ea4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240387"
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt; 函数

## <a name="generate_canonical"></a> generate_canonical

从随机序列返回浮点值。

> [!NOTE]
> ISO C++ 标准声明此函数应返回 [`0`，`1`) 范围中的值。 Visual Studio 尚未与此约束兼容。 请使用 [uniform_real_distribution](../standard-library/uniform-real-distribution-class.md) 作为在此范围中生成值的解决方法。

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>参数

*RealType*\
浮点整型。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。

*Bits*\
随机数生成器。

*常规*\
随机数生成器。

### <a name="remarks"></a>备注

该模板函数将调用`operator()`的*代*重复和包返回的值转换为浮点值`x`类型的*RealType*直到它已收集指定的数量中的尾数位`x`。 指定的数字是较小的一个*Bits* （这必须为非零值） 和中的尾数位的全部数量*RealType*。 第一个调用提供最低序位。 该函数返回 `x`。
