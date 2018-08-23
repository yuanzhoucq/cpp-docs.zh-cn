---
title: 'Makeallocator:: Allocate 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
dev_langs:
- C++
helpviewer_keywords:
- Allocate method
ms.assetid: a01997bc-4ff1-4ed0-9def-e4aaa15b0598
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4422dea0b0bfb07904d0c4defad8f33281a51bec
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609857"
---
# <a name="makeallocatorallocate-method"></a>MakeAllocator::Allocate 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
__forceinline void* Allocate();
```

## <a name="return-value"></a>返回值

如果成功，指向已分配的内存中;否则为**nullptr**。

## <a name="remarks"></a>备注

分配内存，并将其与当前相关联**MakeAllocator**对象。

已分配内存的大小是由当前指定的类型的大小**MakeAllocator**模板参数。

开发人员需要仅重写**Allocate()** 方法来实现不同的内存分配模型。

## <a name="requirements"></a>要求

**标头：** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[MakeAllocator 类](../windows/makeallocator-class.md)  
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)