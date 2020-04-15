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
ms.openlocfilehash: 05c93bf6a2765bd11489075067c627ab3c3ab691
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372582"
---
# <a name="criticalsectiontraits-structure"></a>CriticalSectionTraits 结构

专门化`CriticalSection`对象以支持无效的关键部分或释放关键部分的函数。

## <a name="syntax"></a>语法

```
struct CriticalSectionTraits;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称   | 说明
------ | -----------------------------------------------------------------------------------------------------------------
`Type` | 定义`typedef`指向关键节的指针的 。 `Type` 定义为 `typedef CRITICAL_SECTION* Type;`。

### <a name="public-methods"></a>公共方法

名称                                                       | 说明
---------------------------------------------------------- | -----------------
[关键节特征：：获取无效值](#getinvalidvalue) | 专门化`CriticalSection`模板，以便模板始终无效。
[临界截面：解锁](#unlock)                   | 专门化`CriticalSection`模板，以便它支持释放指定关键节对象的所有权。

## <a name="inheritance-hierarchy"></a>继承层次结构

`CriticalSectionTraits`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装：：处理特征

## <a name="criticalsectiontraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>关键节特征：：获取无效值

专门化`CriticalSection`模板，以便模板始终无效。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>返回值

始终返回指向无效关键部分的指针。

### <a name="remarks"></a>备注

修饰`Type`符定义为`typedef CRITICAL_SECTION* Type;`。

## <a name="criticalsectiontraitsunlock"></a><a name="unlock"></a>临界截面：解锁

专门化`CriticalSection`模板，以便它支持释放指定关键节对象的所有权。

```cpp
inline static void Unlock(
   _In_ Type cs
);
```

### <a name="parameters"></a>参数

*cs*<br/>
指向关键截面对象的指针。

### <a name="remarks"></a>备注

修饰`Type`符定义为`typedef CRITICAL_SECTION* Type;`。

有关详细信息，请参阅 Windows API 文档的**同步函数**部分中的 **"Leave关键"节功能**。
