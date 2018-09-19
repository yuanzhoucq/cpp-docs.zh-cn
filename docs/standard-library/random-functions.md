---
title: '&lt;random&gt; 函数 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: e01c1d71cbc0b3990e40a38484cc9c7a2cc3ebcc
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102793"
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt; 函数

## <a name="generate_canonical"></a>generate_canonical

从随机序列返回浮点值。

> [!NOTE]
> ISO C++ 标准声明此函数应返回 [`0`，`1`) 范围中的值。 Visual Studio 尚未与此约束兼容。 请使用 [uniform_real_distribution](../standard-library/uniform-real-distribution-class.md) 作为在此范围中生成值的解决方法。

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>参数

*RealType*<br/>
浮点整型。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。

*Bits*<br/>
随机数生成器。

*常规*<br/>
随机数生成器。

### <a name="remarks"></a>备注

该模板函数将调用`operator()`的*代*重复和包返回的值转换为浮点值`x`类型的*RealType*直到它已收集指定的数量中的尾数位`x`。 指定的数字是较小的一个*Bits* （这必须为非零值） 和中的尾数位的全部数量*RealType*。 第一个调用提供最低序位。 该函数返回 `x`。

## <a name="see-also"></a>请参阅

[\<random>](../standard-library/random.md)<br/>
