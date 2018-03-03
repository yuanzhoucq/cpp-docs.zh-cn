---
title: "Eventsource:: Invokeall 方法 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::InvokeAll
dev_langs:
- C++
helpviewer_keywords:
- InvokeAll method
ms.assetid: 1506618f-0421-4428-a4d0-4ea2b10a3bf6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 45835b6929ae73559c427d374430b64e7ff21a61
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="eventsourceinvokeall-method"></a>EventSource::InvokeAll 方法
调用与当前关联的每个事件处理程序[EventSource](../windows/eventsource-class.md)对象使用指定的自变量类型和参数。  
  
## <a name="syntax"></a>语法  
  
```  
void InvokeAll();  
template <  
   typename T0  
>  
void InvokeAll(  
   T0arg0  
);  
template <  
   typename T0,  
   typename T1  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6,  
   typename T7  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6,  
   T7arg7  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6,  
   typename T7,  
   typename T8  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6,  
   T7arg7,  
   T8arg8  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6,  
   typename T7,  
   typename T8,  
   typename T9  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6,  
   T7arg7,  
   T8arg8,  
   T9arg9  
);  
```  
  
#### <a name="parameters"></a>参数  
 `T0`  
 第零个事件处理程序自变量的类型。  
  
 `T1`  
 第一个事件处理程序自变量的类型。  
  
 `T2`  
 第二个事件处理程序自变量的类型。  
  
 `T3`  
 第三个事件处理程序自变量的类型。  
  
 `T4`  
 第四个事件处理程序自变量的类型。  
  
 `T5`  
 第五个事件处理程序自变量的类型。  
  
 `T6`  
 第六个事件处理程序自变量的类型。  
  
 `T7`  
 第七个事件处理程序自变量的类型。  
  
 `T8`  
 第八个事件处理程序自变量的类型。  
  
 `T9`  
 第九个事件处理程序自变量的类型。  
  
 `arg0`  
 第零个事件处理程序自变量。  
  
 `arg1`  
 第一个事件处理程序自变量。  
  
 `arg2`  
 第二个事件处理程序自变量。  
  
 `arg3`  
 第三个事件处理程序自变量。  
  
 `arg4`  
 第四个事件处理程序自变量。  
  
 `arg5`  
 第五个事件处理程序自变量。  
  
 `arg6`  
 第六个事件处理程序自变量。  
  
 `arg7`  
 第七事件处理程序自变量。  
  
 `arg8`  
 第八个事件处理程序自变量。  
  
 `arg9`  
 第九个事件处理程序自变量。  
  
## <a name="requirements"></a>惠?  
 **标头：** event.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>请参阅
 [EventSource 类](../windows/eventsource-class.md)