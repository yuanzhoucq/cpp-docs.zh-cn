---
title: 'Eventsource:: Addremovelock_ 数据成员 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::addRemoveLock_
dev_langs:
- C++
helpviewer_keywords:
- addRemoveLock_ data member
ms.assetid: e2d69256-4891-4aad-ad0b-76479c0bb076
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 084a292ed5228f337deced74a87ee20acf0ee5ab
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611730"
---
# <a name="eventsourceaddremovelock-data-member"></a>EventSource::addRemoveLock_ 数据成员

同步对的访问[targets_](../windows/eventsource-targets-data-member.md)数组时添加、 删除或调用事件处理程序。

## <a name="syntax"></a>语法

```cpp
Wrappers::SRWLock addRemoveLock_;
```

## <a name="requirements"></a>要求

**标头：** event.h

**命名空间：** Microsoft::WRL

## <a name="see-also"></a>请参阅
[EventSource 类](../windows/eventsource-class.md)