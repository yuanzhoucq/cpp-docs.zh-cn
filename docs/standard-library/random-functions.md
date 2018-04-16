---
title: "&lt;random&gt; 函数 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
caps.latest.revision: 
manager: ghogen
ms.openlocfilehash: 4833ef603341c7beb65cc31697a8ac5a62e15053
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2018
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt; 函数
  
##  <a name="generate_canonical"></a>generate_canonical  
 从随机序列返回浮点值。  
  
> [!NOTE]
>  ISO C++ 标准声明此函数应返回 [`0`，`1`) 范围中的值。 Visual Studio 尚未与此约束兼容。 请使用 [uniform_real_distribution](../standard-library/uniform-real-distribution-class.md) 作为在此范围中生成值的解决方法。  
  
```  
template <class RealType, size_t Bits, class Generator>  
RealType generate_canonical(Generator& Gen);
```  
  
### <a name="parameters"></a>参数  
 `RealType`  
 浮点整型。 有关可能的类型，请参阅 [\<random>](../standard-library/random.md)。  
  
 `Bits`  
 随机数生成器。  
  
 `Gen`  
 随机数生成器。  
  
### <a name="remarks"></a>备注  
 模板函数重复调用 `operator()` 的 `Gen` 并将返回值打包到 `x` 类型的浮点值 `RealType` 中，直到它已收集指定数量的 `x` 中的尾数位。 指定的数量是 `Bits`（必须为非零）和 `RealType` 中尾数位的全部数量两者中的较小值。 第一个调用提供最低序位。 该函数返回 `x`。  
  
## <a name="see-also"></a>请参阅  
 [\<random>](../standard-library/random.md)

