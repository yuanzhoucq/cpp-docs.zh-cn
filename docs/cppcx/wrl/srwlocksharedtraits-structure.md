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
ms.openlocfilehash: 0dc43d4b9c16145ed7a5abe03cddb598c59b1e94
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374291"
---
# <a name="srwlocksharedtraits-structure"></a>SRWLockSharedTraits 结构

描述`SRWLock`共享锁模式下类的常见特征。

## <a name="syntax"></a>语法

```cpp
struct SRWLockSharedTraits;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称   | 说明
------ | --------------------------------------------------------------------------
`Type` | 指向[SRWLOCK](srwlock-class.md)类的指针的同义词。

### <a name="public-methods"></a>公共方法

名称                                                     | 说明
-------------------------------------------------------- | -----------------------------------------------------------------
[SRWLock 共享特性：：获取无效值](#getinvalidvalue) | 检索始终无效`SRWLockSharedTraits`的对象。
[SRWLock 共享特性：解锁](#unlock)                   | 释放指定`SRWLock`对象的独占控件。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SRWLockSharedTraits`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装：：处理特征

## <a name="srwlocksharedtraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>SRWLock 共享特性：：获取无效值

检索始终无效`SRWLockSharedTraits`的对象。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>返回值

`SRWLockSharedTraits`对象的句柄。

## <a name="srwlocksharedtraitsunlock"></a><a name="unlock"></a>SRWLock 共享特性：解锁

释放指定`SRWLock`对象的独占控件。

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>参数

*斯沃洛克*<br/>
`SRWLock`对象的句柄。
