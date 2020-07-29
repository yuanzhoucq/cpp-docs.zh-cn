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
ms.openlocfilehash: c04e53789fd737b12ca10ef2c279a05fb43f5925
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212990"
---
# <a name="handletraits-structure"></a>HANDLETraits 结构

定义句柄的常见特性。

## <a name="syntax"></a>语法

```cpp
struct HANDLETraits;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称   | 描述
------ | ---------------------
`Type` | 句柄的同义词。

### <a name="public-methods"></a>公共方法

“属性”                                              | 描述
------------------------------------------------- | -----------------------------
[HANDLETraits：： Close](#close)                     | 关闭指定的句柄。
[HANDLETraits：： GetInvalidValue](#getinvalidvalue) | 表示无效的句柄。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HANDLETraits`

## <a name="requirements"></a>要求

**标头：** corewrappers。h

**命名空间：** Microsoft：： WRL：：包装：： HandleTraits

## <a name="handletraitsclose"></a><a name="close"></a>HANDLETraits：： Close

关闭指定的句柄。

```cpp
inline static bool Close(
   _In_ Type h
);
```

### <a name="parameters"></a>参数

*h*<br/>
要关闭的句柄。

### <a name="return-value"></a>返回值

**`true`** 如果 handle *h*成功关闭，则为;否则为 **`false`** 。

## <a name="handletraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>HANDLETraits：： GetInvalidValue

表示无效的句柄。

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>返回值

始终返回 INVALID_HANDLE_VALUE。 （INVALID_HANDLE_VALUE 由 Windows 定义。）
