---
title: HANDLETraits 结构
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue method
ms.assetid: 22963e88-d857-4624-9182-7c986daff722
ms.openlocfilehash: 604098cd3289722767117910d6e44e272dcb8b77
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371450"
---
# <a name="handletraits-structure"></a>HANDLETraits 结构

定义句柄的常见特征。

## <a name="syntax"></a>语法

```cpp
struct HANDLETraits;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称   | 说明
------ | ---------------------
`Type` | HANDLE 的同义词。

### <a name="public-methods"></a>公共方法

名称                                              | 说明
------------------------------------------------- | -----------------------------
[操作：关闭](#close)                     | 关闭指定的句柄。
[操作：获取无效值](#getinvalidvalue) | 表示无效的句柄。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HANDLETraits`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装：：处理特征

## <a name="handletraitsclose"></a><a name="close"></a>操作：关闭

关闭指定的句柄。

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>参数

*H*<br/>
要关闭的句柄。

### <a name="return-value"></a>返回值

如果句柄*h*成功关闭，**则为 true;** 否则，**假**。

## <a name="handletraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>操作：获取无效值

表示无效的句柄。

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>返回值

始终返回INVALID_HANDLE_VALUE。 （INVALID_HANDLE_VALUE由 Windows 定义。
