---
title: Swap 函数 (WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Swap
ms.assetid: ed134a08-ceb7-4279-aa02-a183c3a426ea
ms.openlocfilehash: daa5ab94146866dfa8f1983afc1ad7b37cdb6b06
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476402"
---
# <a name="swap-function-wrl"></a>Swap 函数 (WRL)

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
WRL_NOTHROW inline void Swap(
   _Inout_ T& left,
   _Inout_ T& right
);
```

### <a name="parameters"></a>参数

*left*<br/>
第一个参数。

*right*<br/>
第二个参数。

## <a name="return-value"></a>返回值

## <a name="remarks"></a>备注

交换两个指定参数的值。

## <a name="requirements"></a>要求

**标头：** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)