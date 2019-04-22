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
ms.openlocfilehash: d70425f414b998eb67e3937c2c126dd3eda0c00d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784091"
---
# <a name="handlenulltraits-structure"></a>HANDLENullTraits 结构

定义未初始化句柄的共同特征。

## <a name="syntax"></a>语法

```cpp
struct HANDLENullTraits;
```

## <a name="members"></a>成员

### <a name="public-typedefs"></a>公共 Typedef

名称   | 描述
------ | ---------------------
`Type` | 句柄的同义词。

### <a name="public-methods"></a>公共方法

名称                                                  | 描述
----------------------------------------------------- | -----------------------------
[HANDLENullTraits::Close](#close)                     | 关闭指定的句柄。
[HANDLENullTraits::GetInvalidValue](#getinvalidvalue) | 表示无效句柄。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HANDLENullTraits`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**命名空间：** Microsoft::WRL::Wrappers::HandleTraits

## <a name="close"></a>HANDLENullTraits::Close

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

**true**如果处理*h*关闭成功; 否则为**false**。

## <a name="getinvalidvalue"></a>HANDLENullTraits::GetInvalidValue

表示无效句柄。

```cpp
inline static Type GetInvalidValue();
```

### <a name="return-value"></a>返回值

始终返回 `nullptr`。
