---
title: 'Simpleactivationfactory:: Gettrustlevel 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
dev_langs:
- C++
ms.assetid: 99aa9bc9-d954-4a6f-902b-4abe00e43039
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5a1838c153dc7a0a4def9f98e5e043e36ae9414
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603840"
---
# <a name="simpleactivationfactorygettrustlevel-method"></a>SimpleActivationFactory::GetTrustLevel 方法

获取指定的类的实例的信任级别`Base`类模板参数。

## <a name="syntax"></a>语法

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>参数

*trustLvl*  
此操作完成后，当前类对象的信任级别。

## <a name="return-value"></a>返回值

始终返回 S_OK。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[SimpleActivationFactory 类](../windows/simpleactivationfactory-class.md)