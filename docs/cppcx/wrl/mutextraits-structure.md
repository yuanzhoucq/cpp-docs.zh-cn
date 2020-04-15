---
title: MutexTraits 结构
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock method
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
ms.openlocfilehash: 6d4ba08ab1884e8584b0e98e931d2d63cdac5aec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371255"
---
# <a name="mutextraits-structure"></a>MutexTraits 结构

定义[Mutex](mutex-class.md)类的常见特征。

## <a name="syntax"></a>语法

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

名称                           | 说明
------------------------------ | ------------------------------------------------
[突变：：解锁](#unlock) | 释放共享资源的独占控制。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装：：处理特征

## <a name="mutextraitsunlock-method"></a><a name="unlock"></a>突变：：解锁方法

释放共享资源的独占控制。

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>参数

*H*<br/>
处理互斥体。
