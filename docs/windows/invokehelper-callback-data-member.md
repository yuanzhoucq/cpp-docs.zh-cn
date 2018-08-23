---
title: 'Invokehelper:: Callback_ 数据成员 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper::callback_
dev_langs:
- C++
helpviewer_keywords:
- callback_ data member
ms.assetid: 6f0cbf6d-0448-46f8-ba71-bd6fd8702e3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e602a8d2eef8e495ad732dcd61d0e8aa0b242130
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600995"
---
# <a name="invokehelpercallback-data-member"></a>InvokeHelper::callback_ 数据成员

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
TCallback callback_;
```

## <a name="remarks"></a>备注

表示事件发生时要调用的事件处理程序。

`TCallback`模板参数指定的事件处理程序的类型。

## <a name="requirements"></a>要求

**标头：** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[InvokeHelper 结构](../windows/invokehelper-structure.md)  
[Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)