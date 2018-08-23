---
title: 'Deferrableeventargs:: Invokeallfinished 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 23d521b8373969abdd739b6e4f48eb334284664d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605168"
---
# <a name="deferrableeventargsinvokeallfinished-method"></a>DeferrableEventArgs::InvokeAllFinished 方法
调用以指示处理延迟事件的全部过程都已完成。
  
## <a name="syntax"></a>语法
  
```cpp
void InvokeAllFinished()  
```
  
## <a name="remarks"></a>备注
 应在事件源调用后调用此方法[InvokeAll](../windows/eventsource-invokeall-method.md)。 调用此方法将阻止发生进一步的延迟，并且如果没有发生延迟将强制完成处理程序来执行。
  
 有关代码示例，请参阅[DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)。
  
## <a name="requirements"></a>要求
 **标头：** event.h
  
 **命名空间：** Microsoft::WRL
  
## <a name="see-also"></a>请参阅
 [DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)  
 [EventSource::InvokeAll 方法](../windows/eventsource-invokeall-method.md)