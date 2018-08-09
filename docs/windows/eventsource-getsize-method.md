---
title: 'Eventsource:: Getsize 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::GetSize
dev_langs:
- C++
helpviewer_keywords:
- GetSize method
ms.assetid: 7825aab5-1a6b-465f-9159-3a6684142d1f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 49497c8b33641521a66c3e84dc2dae3dbd993699
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645043"
---
# <a name="eventsourcegetsize-method"></a>EventSource::GetSize 方法
检索与当前相关联的事件处理程序数**EventSource**对象  
  
## <a name="syntax"></a>语法  
  
```cpp  
size_t GetSize() const;  
```  
  
## <a name="return-value"></a>返回值  
 中的事件处理程序数量[targets_](../windows/eventsource-targets-data-member.md)。  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [EventSource 类](../windows/eventsource-class.md)