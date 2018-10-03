---
title: MutexTraits 结构 |Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock method
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 15ed7d9dc3a1b97e05712e003fa61f662901fc18
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234980"
---
# <a name="mutextraits-structure"></a>MutexTraits 结构

定义常见特征[互斥体](../windows/mutex-class1.md)类。

## <a name="syntax"></a>语法

```cpp
struct MutexTraits : HANDLENullTraits;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

名称                           | 描述
------------------------------ | ------------------------------------------------
[Mutextraits:: Unlock](#unlock) | 释放全权控制共享资源。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HANDLENullTraits`

`MutexTraits`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="unlock"></a>Mutextraits:: Unlock 方法

释放全权控制共享资源。

```cpp
inline static void Unlock(
   _In_ Type h
);
```

### <a name="parameters"></a>参数

*h*<br/>
互斥体对象的句柄。
