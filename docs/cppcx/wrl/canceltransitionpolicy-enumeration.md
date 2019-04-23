---
title: CancelTransitionPolicy 枚举
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
helpviewer_keywords:
- CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
ms.openlocfilehash: cb07f28794d466dde08719057a21ebf62f989e85
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038049"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy 枚举

指示异步操作的尝试转换到的终端状态的方式完成或错误的行为根据客户端请求已取消状态。

## <a name="syntax"></a>语法

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>成员

### <a name="values"></a>值

|名称|描述|
|----------|-----------------|
|`RemainCanceled`|如果异步操作目前在客户端请求已取消状态，则表明它将处于已取消状态而不是转换为已完成的终端或错误状态。|
|`TransitionFromCanceled`|如果异步操作目前在客户端请求已取消状态，则表明状态应转换到的终端状态的已取消的状态完成的或由使用此标志的调用确定的错误。|

## <a name="requirements"></a>要求

**标头：** async.h

**命名空间：** Microsoft:: wrl

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)