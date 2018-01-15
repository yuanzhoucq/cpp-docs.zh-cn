---
title: "Eventsource:: Targetspointerlock_ 数据成员 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::EventSource::targetsPointerLock_
dev_langs: C++
helpviewer_keywords: targetsPointerLock_ data member
ms.assetid: 8f08409f-5262-4be7-9cf1-2ed15f19684a
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: be274d7bcf970795df69744324332d29f252363a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="eventsourcetargetspointerlock-data-member"></a>EventSource::targetsPointerLock_ 数据成员
同步对内部数据成员的访问，即使在添加、删除或调用此 EventSource 的事件处理程序时也是如此。  
  
## <a name="syntax"></a>语法  
  
```  
Wrappers::SRWLock targetsPointerLock_;  
```  
  
## <a name="requirements"></a>惠?  
 **标头：** event.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>请参阅
 [EventSource 类](../windows/eventsource-class.md)