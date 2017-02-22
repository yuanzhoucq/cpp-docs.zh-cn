---
title: "EventSource::addRemoveLock_ 数据成员 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource::addRemoveLock_"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "addRemoveLock_ 数据成员"
ms.assetid: e2d69256-4891-4aad-ad0b-76479c0bb076
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# EventSource::addRemoveLock_ 数据成员
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

同步访问 [targets_](../windows/eventsource-targets-data-member.md) 数组时添加、 删除或调用事件处理程序。  
  
## <a name="syntax"></a>语法  
  
```  
Wrappers::SRWLock addRemoveLock_;  
```  
  
## <a name="requirements"></a>要求  
 **标头︰** event.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>另请参阅
 [EventSource 类](../windows/eventsource-class.md)