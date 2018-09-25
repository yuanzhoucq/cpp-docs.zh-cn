---
title: IsSame 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsSame
dev_langs:
- C++
helpviewer_keywords:
- IsSame structure
ms.assetid: 1eddbc3f-3cc5-434f-8495-e4477e1f868e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b7d1879217ac43e2d7d3714f491f44b8245f4f27
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390510"
---
# <a name="issame-structure"></a>IsSame 结构

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template <
   typename T1,
   typename T2
>
struct IsSame;
template <
   typename T1
>
struct IsSame<T1, T1>;
```

### <a name="parameters"></a>参数

T1<br/>
一种类型。

T2<br/>
另一种类型。

## <a name="remarks"></a>备注

一个指定类型等同于另一个测试指定的类型。

## <a name="members"></a>成员

### <a name="public-constants"></a>公共常量

|name|描述|
|----------|-----------------|
|[IsSame::value 常量](../windows/issame-value-constant.md)|指示一种类型是否与另一个相同。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`IsSame`

## <a name="requirements"></a>要求

**标头：** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)