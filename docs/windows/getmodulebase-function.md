---
title: GetModuleBase 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 40289903eba2ce7ac35d4d0b208c3b609efb09f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50650809"
---
# <a name="getmodulebase-function"></a>GetModuleBase 函数
检索[ModuleBase](../windows/modulebase-class.md)允许递增和递减引用数的指针[RuntimeClass](../windows/runtimeclass-class.md)对象。

## <a name="syntax"></a>语法

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>返回值

指向 `ModuleBase` 对象的指针。

## <a name="remarks"></a>备注

在内部使用此函数进行递增和递减对象的引用计数。

可以使用此函数通过调用控制引用计数[modulebase:: Incrementobjectcount](../windows/modulebase-incrementobjectcount-method.md)并[modulebase:: Decrementobjectcount](../windows/modulebase-decrementobjectcount-method.md)。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)