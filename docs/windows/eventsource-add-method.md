---
title: "EventSource::Add 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource::Add"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Add 方法"
ms.assetid: 8bded85b-929e-4425-a464-e5de67bb774c
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# EventSource::Add 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将追加到集中的事件处理程序当前 EventSource 对象表示由指定的委托接口的事件处理程序。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Add(  
   _In_ TDelegateInterface* delegateInterface,  
   _Out_ EventRegistrationToken* token  
);  
```  
  
#### <a name="parameters"></a>参数  
 `delegateInterface`  
 指向委托的对象，它表示一个事件处理程序接口。  
  
 `token`  
 此操作完成后，表示的事件的句柄。 使用此令牌的参数的 [remove （)](../windows/eventsource-remove-method.md) 方法，丢弃事件处理程序。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示错误的 HRESULT。  
  
## <a name="requirements"></a>要求  
 **标头︰** event.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>另请参阅
 [EventSource 类](../windows/eventsource-class.md)