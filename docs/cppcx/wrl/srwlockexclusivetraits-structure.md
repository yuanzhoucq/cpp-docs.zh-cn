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
ms.openlocfilehash: eb7b30915d6061e8470601df33fecec310d1bbca
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374310"
---
# <a name="srwlockexclusivetraits-structure"></a>SRWLockExclusiveTraits 结构

描述类在`SRWLock`独占锁模式下的常见特征。

## <a name="syntax"></a>语法

```cpp
struct SRWLockExclusiveTraits;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称   | 说明
------ | --------------------------------------------------------------------------
`Type` | 指向[SRWLOCK](srwlock-class.md)类的指针的同义词。

### <a name="public-methods"></a>公共方法

名称                                                        | 说明
----------------------------------------------------------- | --------------------------------------------------------------------
[SRWLock 排他性特征：：获取无效值](#getinvalidvalue) | 检索始终无效`SRWLockExclusiveTraits`的对象。
[SRWLock 排他性：解锁](#unlock)                   | 释放指定`SRWLock`对象的独占控件。

## <a name="inheritance-hierarchy"></a>继承层次结构

`SRWLockExclusiveTraits`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装：：处理特征

## <a name="srwlockexclusivetraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>SRWLock 排他性特征：：获取无效值

检索始终无效`SRWLockExclusiveTraits`的对象。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>返回值

空的 `SRWLockExclusiveTraits` 对象。

## <a name="srwlockexclusivetraitsunlock"></a><a name="unlock"></a>SRWLock 排他性：解锁

释放指定`SRWLock`对象的独占控件。

```cpp
inline static void Unlock(
   _In_ Type srwlock
);
```

### <a name="parameters"></a>参数

*斯沃洛克*<br/>
处理`SRWLock`对象。
