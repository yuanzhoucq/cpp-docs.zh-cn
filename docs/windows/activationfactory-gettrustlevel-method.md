---
title: 'Activationfactory:: Gettrustlevel 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- GetTrustLevel method
ms.assetid: 31547ae6-d2ab-4039-923c-154d53fb1a8b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: eba02bea09784e3431b3697eb9ac9a47de978348
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424555"
---
# <a name="activationfactorygettrustlevel-method"></a>ActivationFactory::GetTrustLevel 方法

获取对象的信任级别的当前**ActivationFactory**实例化。

## <a name="syntax"></a>语法

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>参数

*trustLvl*<br/>
在运行时的信任级别完成此操作后，类，该类**ActivationFactory**实例化。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK否则，将发出断言错误并*trustLvl*设置为`FullTrust`。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[ActivationFactory 类](../windows/activationfactory-class.md)