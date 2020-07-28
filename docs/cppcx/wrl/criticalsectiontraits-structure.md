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
ms.openlocfilehash: 3573cad21734a97629cbc12b76d73b99024cbc2f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220504"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits 结构

专用化 `CriticalSection` 对象，以支持无效的临界区或函数以释放关键部分。

## <a name="syntax"></a>语法

```
struct CriticalSectionTraits;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称   | 描述
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | 一个 **`typedef`** ，它定义指向关键部分的指针。 `Type` 定义为 `typedef CRITICAL_SECTION* Type;`。

### <a name="public-methods"></a>公共方法

“属性”                                                       | 描述
---------------------------------------------------------- | -----------------
[CriticalSectionTraits：： GetInvalidValue](#getinvalidvalue) | 专用化 `CriticalSection` 模板，使模板始终无效。
[CriticalSectionTraits：： Unlock](#unlock)                   | 专用化 `CriticalSection` 模板，使其支持释放指定的关键部分对象的所有权。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CriticalSectionTraits`

## <a name="requirements"></a>要求

**标头：** corewrappers。h

**命名空间：** Microsoft：： WRL：：包装：： HandleTraits

## <a name="criticalsectiontraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>CriticalSectionTraits：： GetInvalidValue

专用化 `CriticalSection` 模板，使模板始终无效。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>返回值

始终返回指向无效关键部分的指针。

### <a name="remarks"></a>备注

`Type`修饰符定义为 `typedef CRITICAL_SECTION* Type;` 。

## <a name="criticalsectiontraitsunlock"></a><a name="unlock"></a>CriticalSectionTraits：： Unlock

专用化 `CriticalSection` 模板，使其支持释放指定的关键部分对象的所有权。

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>参数

*站*<br/>
指向关键节对象的指针。

### <a name="remarks"></a>备注

`Type`修饰符定义为 `typedef CRITICAL_SECTION* Type;` 。

有关详细信息，请参阅 Windows API 文档的**同步函数**部分中的**LeaveCriticalSection 函数**。
