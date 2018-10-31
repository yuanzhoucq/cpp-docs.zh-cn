---
title: HANDLETraits 结构 |Microsoft Docs
ms.custom: ''
ms.date: 09/27/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits structure
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::Close method
- Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue method
ms.assetid: 22963e88-d857-4624-9182-7c986daff722
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e670dca205f07d1e13a93f8acd0df5965b45109
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161705"
---
# <a name="handletraits-structure"></a>HANDLETraits 结构

定义句柄的共同特征。

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

名称                                              | 描述
------------------------------------------------- | -----------------------------
[Handletraits:: Close](#close)                     | 关闭指定的句柄。
[Handletraits:: Getinvalidvalue](#getinvalidvalue) | 表示无效句柄。

## <a name="inheritance-hierarchy"></a>继承层次结构

`HANDLETraits`

## <a name="requirements"></a>要求

**标头：** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers::HandleTraits

## <a name="close"></a>Handletraits:: Close

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

## <a name="getinvalidvalue"></a>Handletraits:: Getinvalidvalue

表示无效句柄。

```cpp
inline static HANDLE GetInvalidValue();
```

### <a name="return-value"></a>返回值

始终返回 INVALID_HANDLE_VALUE。 （INVALID_HANDLE_VALUE 定义由 Windows 中）。
