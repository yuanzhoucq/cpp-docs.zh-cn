---
title: CriticalSectionTraits 结构
ms.date: 09/26/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::GetInvalidValue method
- Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock method
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
ms.openlocfilehash: ce904ecbd9a5855c63fd43f07f88c215cef544ae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398597"
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
[CriticalSectionTraits::GetInvalidValue](#getinvalidvalue) | 专门负责`CriticalSection`模板，以便该模板始终无效。
[CriticalSectionTraits::Unlock](#unlock)                   | 专门负责`CriticalSection`模板以便支持指定的关键节对象的释放所有权。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CriticalSectionTraits`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**命名空间：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="getinvalidvalue"></a>CriticalSectionTraits::GetInvalidValue

专门负责`CriticalSection`模板，以便该模板始终无效。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>返回值

始终返回一个指向无效的关键部分。

### <a name="remarks"></a>备注

`Type`修饰符定义为`typedef CRITICAL_SECTION* Type;`。

## <a name="unlock"></a>CriticalSectionTraits::Unlock

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
