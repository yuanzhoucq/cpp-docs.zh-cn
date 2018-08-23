---
title: 'Activationfactory:: Release 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method
ms.assetid: 5bc25ff0-ee3c-4a2d-a9b6-2d8f158033ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2d21210455a19a45b5dfde3b5bb31920f33cb777
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605289"
---
# <a name="activationfactoryrelease-method"></a>ActivationFactory::Release 方法

递减引用计数的当前**ActivationFactory**对象。

## <a name="syntax"></a>语法

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[ActivationFactory 类](../windows/activationfactory-class.md)