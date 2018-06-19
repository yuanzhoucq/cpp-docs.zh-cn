---
title: 'Deferrableeventargs:: Invokeallfinished 方法 |Microsoft 文档'
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
ms.openlocfilehash: 1aaaf8c6849b30e26463810ff353234319960048
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883363"
---
# <a name="deferrableeventargsinvokeallfinished-method"></a>DeferrableEventArgs::InvokeAllFinished 方法
调用以指示处理延迟事件的全部过程都已完成。  
  
## <a name="syntax"></a>语法  
  
```cpp  
void InvokeAllFinished()  
```  
  
## <a name="remarks"></a>备注  
 你应调用此方法后的事件源调用[InvokeAll](../windows/eventsource-invokeall-method.md)。 调用此方法将阻止发生进一步的延迟，并且如果没有发生延迟将强制完成处理程序来执行。  
  
 有关代码示例，请参阅[DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [DeferrableEventArgs 类](../windows/deferrableeventargs-class.md)   
 [EventSource::InvokeAll 方法](../windows/eventsource-invokeall-method.md)