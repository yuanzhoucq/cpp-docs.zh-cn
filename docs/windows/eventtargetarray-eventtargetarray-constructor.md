---
title: 'Eventtargetarray:: Eventtargetarray 构造函数 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray, constructor
ms.assetid: 6c6d3737-3cd3-4515-a8f6-d27901bb8ed2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fbfd12ea513044f1062e60f5c73f5089683f043d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33872710"
---
# <a name="eventtargetarrayeventtargetarray-constructor"></a>EventTargetArray::EventTargetArray 构造函数
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
EventTargetArray(  
   _Out_ HRESULT* hr,  
   size_t items  
);  
```  
  
#### <a name="parameters"></a>参数  
 `hr`  
 此构造函数操作后, 参数`hr`指示数组分配是否成功。 下表列出的可能值`hr`。  
  
 S_OK  
 操作成功。  
  
 E_OUTOFMEMORY  
 无法为数组分配内存。  
  
 S_FALSE  
 参数`items`小于或等于零。  
  
 `items`  
 分配的数组元素的数目。  
  
## <a name="remarks"></a>备注  
 初始化 EventTargetArray 类的新实例。  
  
 EventTargetArray 用于保留 EventSource 对象中的事件处理程序的数组。  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [EventTargetArray 类](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)