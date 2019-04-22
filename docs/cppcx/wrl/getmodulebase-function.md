---
title: GetModuleBase 函数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 4d8c8467b7aeb9c21bf5f4ee19c60e6e60880688
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58784039"
---
# <a name="getmodulebase-function"></a>GetModuleBase 函数

检索[ModuleBase](modulebase-class.md)允许递增和递减引用数的指针[RuntimeClass](runtimeclass-class.md)对象。

## <a name="syntax"></a>语法

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>返回值

指向 `ModuleBase` 对象的指针。

## <a name="remarks"></a>备注

在内部使用此函数进行递增和递减对象的引用计数。

可以使用此函数通过调用控制引用计数[modulebase:: Incrementobjectcount](modulebase-class.md#incrementobjectcount)并[modulebase:: Decrementobjectcount](modulebase-class.md#decrementobjectcount)。

## <a name="requirements"></a>要求

**标头：** implements.h

**命名空间：** Microsoft:: wrl

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)