---
title: SRWLockSharedTraits 结构
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock method
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
ms.openlocfilehash: af567fd333854519df4543ad24084e52cda4d96e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383277"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits 结构

描述的常见特征`SRWLock`中共享锁模式的类。

## <a name="syntax"></a>语法

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称   | 描述
------ | --------------------------------------------------------------------------
`Type` | 一个指向同义词[SRWLOCK](srwlock-class.md)类。

### <a name="public-methods"></a>公共方法

名称                                                     | 描述
-------------------------------------------------------- | -----------------------------------------------------------------
[SRWLockSharedTraits::GetInvalidValue](#getinvalidvalue) | 检索`SRWLockSharedTraits`始终是无效的对象。
[SRWLockSharedTraits::Unlock](#unlock)                   | 释放指定的全权控制`SRWLock`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SRWLockSharedTraits`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**命名空间：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>SRWLockSharedTraits::GetInvalidValue

检索`SRWLockSharedTraits`始终是无效的对象。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>返回值

句柄`SRWLockSharedTraits`对象。

## <a name="unlock"></a>SRWLockSharedTraits::Unlock

释放指定的全权控制`SRWLock`对象。

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>参数

*srwlock*<br/>
句柄`SRWLock`对象。
