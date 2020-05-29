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
ms.openlocfilehash: e820b3fffb4a00e95a1210a5c0beb3229c6d1657
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214118"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy 枚举

指示异步操作尝试转换为已完成或错误的终端状态的方式应与客户端请求的已取消状态的行为有关。

## <a name="syntax"></a>语法

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>成员

### <a name="values"></a>值

|名称|说明|
|----------|-----------------|
|`RemainCanceled`|如果异步操作当前处于客户端请求的已取消状态，这表示它将保持为 "已取消" 状态，而不是转换为 "已完成" 或 "错误" 状态。|
|`TransitionFromCanceled`|如果异步操作当前处于客户端请求的已取消状态，则指示状态应从该取消状态转换为已完成或错误的结束状态，这取决于利用此标志的调用。|

## <a name="requirements"></a>要求

**标头：** async。h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>另请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)
