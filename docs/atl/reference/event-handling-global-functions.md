---
title: 事件处理全局函数 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
dev_langs:
- C++
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cb2c7834e7d5475810973a42ef179ea4f5f0079f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358333"
---
# <a name="event-handling-global-functions"></a>事件处理全局函数
此函数提供了一个事件处理程序。  
  
> [!IMPORTANT]
>  下表中列出的函数不能在 Windows 运行时中执行的应用程序。  
  
|||  
|-|-|  
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|等待发出对象信号，同时根据需要调度窗口消息。|  

## <a name="requirements"></a>要求  
 **标头：** atlbase.h  

##  <a name="atlwaitwithmessageloop"></a>  AtlWaitWithMessageLoop  
 等待发出对象信号，同时根据需要调度窗口消息。  
  
> [!IMPORTANT]
>  此函数不能在 Windows 运行时中执行的应用程序。  
  
```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```  
  
### <a name="parameters"></a>参数  
 `hEvent`  
 [in]要等待的对象的句柄。  
  
### <a name="return-value"></a>返回值  
 返回**TRUE**如果尚未向该对象。  
  
### <a name="remarks"></a>备注  
 如果你想要等待的对象的事件发生这种情况，并通知的这种情况，但允许在等待时调度窗口消息，这非常有用。  
  
## <a name="see-also"></a>请参阅  
 [函数](../../atl/reference/atl-functions.md)
