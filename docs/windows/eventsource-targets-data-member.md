---
title: 'Eventsource:: Targets_ 数据成员 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::targets_
dev_langs:
- C++
helpviewer_keywords:
- targets_ data member
ms.assetid: 5d5cee05-3315-4514-bce2-19173c923c7d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a35992a5579bf852323f4c01396fab56542f40cd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="eventsourcetargets-data-member"></a>EventSource::targets_ 数据成员
包含一个或多个事件处理程序的数组。  
  
## <a name="syntax"></a>语法  
  
```  
ComPtr<Details::EventTargetArray> targets_;  
```  
  
## <a name="remarks"></a>备注  
 如果发生当前 EventSource 对象表示的事件，则将调用这些事件处理程序。  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>请参阅
 [EventSource 类](../windows/eventsource-class.md)