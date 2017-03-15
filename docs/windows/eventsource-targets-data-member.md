---
title: "EventSource::targets_ 数据成员 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource::targets_"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "targets_ 数据成员"
ms.assetid: 5d5cee05-3315-4514-bce2-19173c923c7d
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# EventSource::targets_ 数据成员
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

包含一个或多个事件处理程序的数组。  
  
## <a name="syntax"></a>语法  
  
```  
ComPtr<Details::EventTargetArray> targets_;  
```  
  
## <a name="remarks"></a>备注  
 如果发生当前 EventSource 对象表示的事件，则将调用这些事件处理程序。  
  
## <a name="requirements"></a>要求  
 **标头︰** event.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>另请参阅
 [EventSource 类](../windows/eventsource-class.md)