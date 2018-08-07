---
title: 'Eventtargetarray:: Eventtargetarray 构造函数 |Microsoft Docs'
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
ms.openlocfilehash: 831c9a524f8120c855382d198a5f53ac312cada6
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569783"
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
  
### <a name="parameters"></a>参数  
 *hr*  
 此构造函数的操作之后, 参数*hr*指示数组的分配是成功还是失败。 下表列出了可能的值为*hr*。  
  
 S_OK  
 操作成功。  
  
 E_OUTOFMEMORY  
 无法为数组分配内存。  
  
 S_FALSE  
 参数*项*小于或等于零。  
  
 *项*  
 要分配的数组元素数。  
  
## <a name="remarks"></a>备注  
 初始化的新实例**EventTargetArray**类。  
  
 **EventTargetArray**用于将数组中的事件处理程序`EventSource`对象。  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [EventTargetArray 类](../windows/eventtargetarray-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)