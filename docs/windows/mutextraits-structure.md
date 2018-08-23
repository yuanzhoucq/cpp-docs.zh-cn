---
title: MutexTraits 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
dev_langs:
- C++
helpviewer_keywords:
- MutexTraits structure
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 529265c4b1e5f510a92295a1ceff6d0a012163fe
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42584166"
---
# <a name="mutextraits-structure"></a>MutexTraits 结构

定义常见特征[互斥体](../windows/mutex-class1.md)类。

## <a name="syntax"></a>语法

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[MutexTraits::Unlock 方法](../windows/mutextraits-unlock-method.md)|释放全权控制共享资源。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Wrappers::HandleTraits 命名空间](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)