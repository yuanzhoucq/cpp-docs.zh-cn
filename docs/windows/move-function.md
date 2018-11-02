---
title: Move 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
ms.openlocfilehash: a53dbbe54cef2ac2557648e66e5d8dafc4fb4768
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591355"
---
# <a name="move-function"></a>Move 函数

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
template<class T>
inline typename RemoveReference<T>::Type&& Move(
   _Inout_ T&& arg
);
```

### <a name="parameters"></a>参数

*T*<br/>
自变量类型。

*arg*<br/>
要移动的参数。

## <a name="return-value"></a>返回值

参数*arg*后引用或右值引用的特点，如果有，已删除。

## <a name="remarks"></a>备注

将指定的参数从一个位置移动到另一个。

有关详细信息，请参阅**移动语义**一部分[右值引用声明符： & &](../cpp/rvalue-reference-declarator-amp-amp.md)。

## <a name="requirements"></a>要求

**标头：** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)