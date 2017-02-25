---
title: "EventSource::Remove 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource::Remove"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Remove 方法"
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# EventSource::Remove 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

删除指定的事件注册标记从与当前 EventSource 对象关联的事件处理程序集中所表示的事件处理程序。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Remove(  
   EventRegistrationToken token  
);  
```  
  
#### <a name="parameters"></a>参数  
 `token`  
 一个表示事件处理程序的句柄。 通过注册事件处理程序时返回此令牌 [add （)](../windows/eventsource-add-method.md) 方法。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示错误的 HRESULT。  
  
## <a name="remarks"></a>备注  
 有关 EventRegistrationToken 结构的详细信息，请参阅 Windows 运行时参考文档中的 Windows::Foundation::EventRegistrationToken 结构主题。  
  
## <a name="requirements"></a>要求  
 **标头︰** event.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>另请参阅
 [EventSource 类](../windows/eventsource-class.md)