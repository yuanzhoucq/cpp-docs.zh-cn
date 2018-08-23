---
title: 'Chaininterfaces:: Iidcount 常量 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::IidCount
dev_langs:
- C++
helpviewer_keywords:
- IidCount constant
ms.assetid: d4a90aa0-513c-4e99-b978-e12149734936
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a97ea483bddb0ed6b2fadce1f9daa50eab82591a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596900"
---
# <a name="chaininterfacesiidcount-constant"></a>ChainInterfaces::IidCount 常量

模板参数所指定的接口中包含的接口 Id 总数*I0*通过*I9*。

## <a name="syntax"></a>语法

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

## <a name="return-value"></a>返回值

接口 ID 的总数。

## <a name="remarks"></a>备注

模板参数*I0*并*I1*是必需的并且参数*I2*通过*I9*都是可选的。每个接口的 IID 计数通常为 1。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[ChainInterfaces 结构](../windows/chaininterfaces-structure.md)