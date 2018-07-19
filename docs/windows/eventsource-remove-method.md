---
title: 'Eventsource:: Remove 方法 |Microsoft 文档'
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
ms.openlocfilehash: bbf0480252fca342b8a690e93f92ae14ca5e84c0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874377"
---
# <a name="eventsourceremove-method"></a>EventSource::Remove 方法
删除从与当前 EventSource 对象关联的事件处理程序集中指定的事件注册标记所表示的事件处理程序。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT Remove(  
   EventRegistrationToken token  
);  
```  
  
#### <a name="parameters"></a>参数  
 `token`  
 表示一个事件处理程序的句柄。 事件处理程序已由注册时返回此令牌[add （)](../windows/eventsource-add-method.md)方法。  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示错误的 HRESULT。  
  
## <a name="remarks"></a>备注  
 有关的 EventRegistrationToken 结构的详细信息，请参阅中的 Windows 运行时参考文档的 Windows::Foundation::EventRegistrationToken 结构主题。  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **命名空间：** Microsoft::WRL
 
 ## <a name="see-also"></a>请参阅
 [EventSource 类](../windows/eventsource-class.md)