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
ms.openlocfilehash: 41e06cc50f36a077a34d992c416a543e5bf9b593
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371474"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits 结构

定义未初始化句柄的常见特征。

## <a name="syntax"></a>语法

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称   | 说明
------ | ---------------------
`Type` | HANDLE 的同义词。

### <a name="public-methods"></a>公共方法

名称                                                  | 说明
----------------------------------------------------- | -----------------------------
[操作无效：关闭](#close)                     | 关闭指定的句柄。
[操作无效：获取无效值](#getinvalidvalue) | 表示无效的句柄。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HANDLENullTraits`

## <a name="requirements"></a>要求

**标题：** 核心包装.h

**命名空间：** 微软：：WRL：包装：：处理特征

## <a name="handlenulltraitsclose"></a><a name="close"></a>操作无效：关闭

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

## <a name="handlenulltraitsgetinvalidvalue"></a><a name="getinvalidvalue"></a>操作无效：获取无效值

表示无效的句柄。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>返回值

始终返回 `nullptr`。
