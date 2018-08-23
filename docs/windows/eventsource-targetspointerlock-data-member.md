---
title: 'Eventsource:: Targetspointerlock_ 数据成员 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::targetsPointerLock_
dev_langs:
- C++
helpviewer_keywords:
- targetsPointerLock_ data member
ms.assetid: 8f08409f-5262-4be7-9cf1-2ed15f19684a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 45c85502b7d0768f5fa3e275393a4071fd8649e4
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598860"
---
# <a name="eventsourcetargetspointerlock-data-member"></a>EventSource::targetsPointerLock_ 数据成员

此同步对内部数据成员，即使是事件处理程序的访问**EventSource**添加、 删除或被调用。

## <a name="syntax"></a>语法

```cpp
Wrappers::SRWLock targetsPointerLock_;
```

## <a name="requirements"></a>要求

**标头：** event.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅
[EventSource 类](../windows/eventsource-class.md)