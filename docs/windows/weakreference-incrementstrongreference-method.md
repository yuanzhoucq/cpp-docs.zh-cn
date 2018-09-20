---
title: 'Weakreference:: Incrementstrongreference 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- IncrementStrongReference method
ms.assetid: d0232426-a8cb-48b4-99d4-165de2d66cb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 345caec13a1e22bc3350f124a8b340282e3a8a42
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438803"
---
# <a name="weakreferenceincrementstrongreference-method"></a>WeakReference::IncrementStrongReference 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
ULONG IncrementStrongReference();
```

## <a name="return-value"></a>返回值

递增的强引用计数。

## <a name="remarks"></a>备注

当前的强引用计数递增**WeakReference**对象。

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[WeakReference 类](../windows/weakreference-class1.md)<br/>
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)