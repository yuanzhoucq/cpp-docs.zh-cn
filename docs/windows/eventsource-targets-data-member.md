---
title: 'Eventsource:: Targets_ 数据成员 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::targets_
dev_langs:
- C++
helpviewer_keywords:
- targets_ data member
ms.assetid: 5d5cee05-3315-4514-bce2-19173c923c7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fcdcb759c90009410f76a4b10039a0d976ca0cc4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605110"
---
# <a name="eventsourcetargets-data-member"></a>EventSource::targets_ 数据成员

包含一个或多个事件处理程序的数组。

## <a name="syntax"></a>语法

```cpp
ComPtr<Details::EventTargetArray> targets_;
```

## <a name="remarks"></a>备注

当事件表示由当前**EventSource**对象发生，则调用事件处理程序。

## <a name="requirements"></a>要求

**标头：** event.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅
[EventSource 类](../windows/eventsource-class.md)