---
title: 'Srwlocksharedtraits:: Unlock 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 33cdead9-1900-4094-b18e-38fcf1a0bd28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e00b898fc60953896a9c0d2b7a124e195d3bcbf1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593163"
---
# <a name="srwlocksharedtraitsunlock-method"></a>SRWLockSharedTraits::Unlock 方法

释放指定的全权控制`SRWLock`对象。

## <a name="syntax"></a>语法

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>参数

*srwlock*  
句柄`SRWLock`对象。

## <a name="return-value"></a>返回值

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="see-also"></a>请参阅

[SRWLockSharedTraits 结构](../windows/srwlocksharedtraits-structure.md)