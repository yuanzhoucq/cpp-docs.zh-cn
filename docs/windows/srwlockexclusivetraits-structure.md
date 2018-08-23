---
title: SRWLockExclusiveTraits 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
dev_langs:
- C++
helpviewer_keywords:
- SRWLockExclusiveTraits structure
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 542ad92aa636c934e3250817931dd7f31d1fe85b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601598"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits 结构

描述的常见特征`SRWLock`中排他锁模式的类。

## <a name="syntax"></a>语法

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

|名称|描述|
|----------|-----------------|
|`Type`|一个指向同义词[SRWLOCK](../windows/srwlock-class.md)类。|

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[SRWLockExclusiveTraits::GetInvalidValue 方法](../windows/srwlockexclusivetraits-getinvalidvalue-method.md)|检索**SRWLockExclusiveTraits**始终是无效的对象。|
|[SRWLockExclusiveTraits::Unlock 方法](../windows/srwlockexclusivetraits-unlock-method.md)|释放指定的全权控制`SRWLock`对象。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`SRWLockExclusiveTraits`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Wrappers::HandleTraits 命名空间](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)