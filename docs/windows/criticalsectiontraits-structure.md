---
title: CriticalSectionTraits 结构 |Microsoft Docs
ms.custom: ''
ms.date: 09/26/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock method
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 420ab1019dfa2e95e00e366c64509178ad20e685
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2018
ms.locfileid: "48234317"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits 结构

专门负责`CriticalSection`对象以支持无效的关键部分或函数，以释放关键节。

## <a name="syntax"></a>语法

```
struct CriticalSectionTraits;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称   | 描述
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | 一个`typedef`的关键部分定义指针。 `Type` 定义为`typedef CRITICAL_SECTION* Type;`。

### <a name="public-methods"></a>公共方法

名称                                                       | 描述
---------------------------------------------------------- | -----------------
[Criticalsectiontraits:: Getinvalidvalue](#getinvalidvalue) | 专门负责`CriticalSection`模板，以便该模板始终无效。
[Criticalsectiontraits:: Unlock](#unlock)                   | 专门负责`CriticalSection`模板以便支持指定的关键节对象的释放所有权。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CriticalSectionTraits`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>Criticalsectiontraits:: Getinvalidvalue

专门负责`CriticalSection`模板，以便该模板始终无效。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>返回值

始终返回一个指向无效的关键部分。

### <a name="remarks"></a>备注

`Type`修饰符定义为`typedef CRITICAL_SECTION* Type;`。

## <a name="unlock"></a>Criticalsectiontraits:: Unlock

专门负责`CriticalSection`模板以便支持指定的关键节对象的释放所有权。

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>参数

*cs*<br/>
指向关键部分对象的指针。

### <a name="remarks"></a>备注

`Type`修饰符定义为`typedef CRITICAL_SECTION* Type;`。

有关详细信息，请参阅**LeaveCriticalSection 函数**中**同步函数**Windows API 文档的部分。
