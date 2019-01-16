---
title: AgileActivationFactory 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::AgileActivationFactory
ms.assetid: fab98f32-bb93-4c0f-badb-49fbddb194b0
ms.openlocfilehash: caef4752469f7535d3c7ff3a3b36f0e255819bab
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2019
ms.locfileid: "54335772"
---
# <a name="agileactivationfactory-class"></a>AgileActivationFactory 类

表示实现的单元友好激活工厂[FtmBase](ftmbase-class.md)。

## <a name="syntax"></a>语法

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil,
    FactoryCacheFlags cacheFlagValue = FactoryCacheDefault
>
class AgileActivationFactory :
    public ActivationFactory<
        Implements<FtmBase, I0>,
        I1,
        I2,
        cacheFlagValue
    >;
```

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft:: wrl

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)<br/>
[ActivationFactory 类](activationfactory-class.md)