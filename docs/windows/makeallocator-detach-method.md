---
title: 'Makeallocator:: Detach 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
dev_langs:
- C++
helpviewer_keywords:
- Detach method
ms.assetid: 78012634-2dda-4ea2-9ffe-40f105d2fe47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3ef07b3de2125c38064bc2a0f15559e8ef6084d4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443379"
---
# <a name="makeallocatordetach-method"></a>MakeAllocator::Detach 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
__forceinline void Detach();
```

## <a name="remarks"></a>备注

解除分配的内存之间的关联[分配](../windows/makeallocator-allocate-method.md)方法从当前**MakeAllocator**对象。

如果您调用**Detach()**，你需要负责删除提供的内存`Allocate`方法。

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[MakeAllocator 类](../windows/makeallocator-class.md)<br/>
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)