---
title: 'Eventsource:: Add 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::Add
dev_langs:
- C++
helpviewer_keywords:
- Add method
ms.assetid: 8bded85b-929e-4425-a464-e5de67bb774c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a13c5b48a7e242f47903fda038331fd126832dcf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592226"
---
# <a name="eventsourceadd-method"></a>EventSource::Add 方法

将追加到当前的事件处理程序集由指定的委托接口表示的事件处理程序**EventSource**对象。

## <a name="syntax"></a>语法

```cpp
HRESULT Add(
   _In_ TDelegateInterface* delegateInterface,
   _Out_ EventRegistrationToken* token
);
```

### <a name="parameters"></a>参数

*delegateInterface*  
为委托对象，表示事件处理程序的接口。

*令牌*  
此操作完成后，表示该事件的句柄。 使用此令牌作为参数[Remove()](../windows/eventsource-remove-method.md)方法，丢弃的事件处理程序。

## <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

## <a name="requirements"></a>要求

**标头：** event.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅
[EventSource 类](../windows/eventsource-class.md)