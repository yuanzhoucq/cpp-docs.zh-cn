---
title: SRWLockExclusiveTraits 结构
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits::Unlock method
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
ms.openlocfilehash: 25249b8823b8c182133e85aa4cd07d38f5874cf2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58783854"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits 结构

描述的常见特征`SRWLock`中排他锁模式的类。

## <a name="syntax"></a>语法

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称   | 描述
------ | --------------------------------------------------------------------------
`Type` | 一个指向同义词[SRWLOCK](srwlock-class.md)类。

### <a name="public-methods"></a>公共方法

名称                                                        | 描述
----------------------------------------------------------- | --------------------------------------------------------------------
[SRWLockExclusiveTraits::GetInvalidValue](#getinvalidvalue) | 检索`SRWLockExclusiveTraits`始终是无效的对象。
[SRWLockExclusiveTraits::Unlock](#unlock)                   | 释放指定的全权控制`SRWLock`对象。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SRWLockExclusiveTraits`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**命名空间：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>SRWLockExclusiveTraits::GetInvalidValue

检索`SRWLockExclusiveTraits`始终是无效的对象。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>返回值

一个空 `SRWLockExclusiveTraits` 对象。

## <a name="unlock"></a>SRWLockExclusiveTraits::Unlock

释放指定的全权控制`SRWLock`对象。

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>参数

*srwlock*<br/>
句柄`SRWLock`对象。
