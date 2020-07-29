---
title: HANDLENullTraits 结构
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLENullTraits::GetInvalidValue method
ms.assetid: 88a29a14-c516-40cb-a0ca-ee897a668623
ms.openlocfilehash: a7ce730b8d723a839c5b509c825cff84111ca613
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226914"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits 结构

定义未初始化的句柄的常见特性。

## <a name="syntax"></a>语法

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称   | 说明
------ | ---------------------
`Type` | 句柄的同义词。

### <a name="public-methods"></a>公共方法

“属性”                                                  | 说明
----------------------------------------------------- | -----------------------------
[HANDLENullTraits：： Close](#close)                     | 关闭指定的句柄。
[HANDLENullTraits：： GetInvalidValue](#getinvalidvalue) | 表示无效的句柄。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HANDLENullTraits`

## <a name="requirements"></a>要求

**标头：** corewrappers。h

**命名空间：** Microsoft：： WRL：：包装：： HandleTraits

## <a name="handlenulltraitsclose"></a><a name="close"></a>HANDLENullTraits：： Close

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

## <a name="handlenulltraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>HANDLENullTraits：： GetInvalidValue

表示无效的句柄。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>返回值

始终返回 **`nullptr`** 。
