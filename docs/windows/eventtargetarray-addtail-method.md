---
title: 'Eventtargetarray:: Addtail 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::AddTail
dev_langs:
- C++
helpviewer_keywords:
- AddTail method
ms.assetid: d0fafab9-049c-40e0-a40c-d126c9ee63e6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6609bba6d7adbddda152007e4db45c82f8039bc0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42603673"
---
# <a name="eventtargetarrayaddtail-method"></a>EventTargetArray::AddTail 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
void AddTail(
   _In_ IUnknown* element
);
```

### <a name="parameters"></a>参数

*元素*  
指向要追加的事件处理程序。

## <a name="remarks"></a>备注

将指定的事件处理程序附加到事件处理程序的内部数组的末尾。

**AddTail()** 应仅在内部使用`EventSource`类。

## <a name="requirements"></a>要求

**标头：** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[EventTargetArray 类](../windows/eventtargetarray-class.md)  
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)