---
title: "EventSource::targetsPointerLock_ 数据成员 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource::targetsPointerLock_"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "targetsPointerLock_ 数据成员"
ms.assetid: 8f08409f-5262-4be7-9cf1-2ed15f19684a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# EventSource::targetsPointerLock_ 数据成员
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

同步对内部数据成员的访问，即使在添加、删除或调用此 EventSource 的事件处理程序时也是如此。  
  
## <a name="syntax"></a>语法  
  
```  
Wrappers::SRWLock targetsPointerLock_;  
```  
  
## <a name="requirements"></a>要求  
 **标头︰** event.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>另请参阅
 [EventSource 类](../windows/eventsource-class.md)