---
title: 'Eventsource:: Remove 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::Remove
dev_langs:
- C++
helpviewer_keywords:
- Remove method
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 36a057bbad39e61576828c5a02f6863248b235cf
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641400"
---
# <a name="eventsourceremove-method"></a>EventSource::Remove 方法
删除指定的事件注册标记与当前相关联的事件处理程序集中所表示的事件处理程序**EventSource**对象。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT Remove(  
   EventRegistrationToken token  
);  
```  
  
### <a name="parameters"></a>参数  
 *令牌*  
 一个表示事件处理程序的句柄。 此令牌已由注册事件处理程序时返回[add （)](../windows/eventsource-add-method.md)方法。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示错误的 HRESULT。  
  
## <a name="remarks"></a>备注  
 有关详细信息`EventRegistrationToken`结构，请参阅**Windows::Foundation::EventRegistrationToken 结构**中的主题**Windows 运行时**参考文档。  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>请参阅
 [EventSource 类](../windows/eventsource-class.md)