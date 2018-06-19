---
title: 'Eventtargetarray:: End 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::End
dev_langs:
- C++
helpviewer_keywords:
- End method
ms.assetid: 20c491b8-f355-4d8f-ad14-8f46121d9af6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 00827d42bb01263d6b4fd9b5aea3b0fc7f7c76e1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874260"
---
# <a name="eventtargetarrayend-method"></a>EventTargetArray::End 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
ComPtr<IUnknown>* End();  
```  
  
## <a name="return-value"></a>返回值  
 事件处理程序在内部数组的最后一个元素的地址。  
  
## <a name="remarks"></a>备注  
 获取事件处理程序在内部数组的最后一个元素的地址。  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [EventTargetArray 类](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)