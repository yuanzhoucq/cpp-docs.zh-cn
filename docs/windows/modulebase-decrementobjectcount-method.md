---
title: 'Modulebase:: Decrementobjectcount 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount
dev_langs:
- C++
helpviewer_keywords:
- DecrementObjectCount method
ms.assetid: a016fb07-a36e-40cd-bc7b-8f6e85e256e7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f45f52f2e979b76128be02dc7c3e931bd3b9d2c5
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42594583"
---
# <a name="modulebasedecrementobjectcount-method"></a>ModuleBase::DecrementObjectCount 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
virtual long DecrementObjectCount() = 0;
```

## <a name="return-value"></a>返回值

递减操作之前的计数。

## <a name="remarks"></a>备注

实现时，递减的对象数模块所跟踪。

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[ModuleBase 类](../windows/modulebase-class.md)  
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)