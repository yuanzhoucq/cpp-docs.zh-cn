---
title: 'Eventtargetarray:: Begin 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::Begin
dev_langs:
- C++
helpviewer_keywords:
- Begin method
ms.assetid: 1cc7fdfd-a2c4-4b28-93cf-1c82842294ba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 738ee52eb68cfbb03a380ffac52efdb4010b5205
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602126"
---
# <a name="eventtargetarraybegin-method"></a>EventTargetArray::Begin 方法

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
ComPtr<IUnknown>* Begin();
```

## <a name="return-value"></a>返回值

事件处理程序在内部数组的第一个元素的地址。

## <a name="remarks"></a>备注

获取事件处理程序的内部数组中的第一个元素的地址。

## <a name="requirements"></a>要求

**标头：** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[EventTargetArray 类](../windows/eventtargetarray-class.md)  
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)