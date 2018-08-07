---
title: 'Runtimeclass:: Release 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::Release
dev_langs:
- C++
helpviewer_keywords:
- Release method
ms.assetid: 0bd6f9e2-ad90-4de6-adef-a6286f458cb6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1c1f9500abc1c92ea5f9aca64e379adfdcf84a44
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607519"
---
# <a name="runtimeclassrelease-method"></a>RuntimeClass::Release 方法
执行 COM 释放操作对当前**RuntimeClass**对象。  
  
## <a name="syntax"></a>语法  
  
```  
STDMETHOD_(  
   ULONG,  
   Release  
)();  
```  
  
## <a name="return-value"></a>返回值  
 如果成功，则为 S_OK；否则为指示错误的 HRESULT。  
  
## <a name="remarks"></a>备注  
 如果引用计数变为零， **RuntimeClass**删除对象。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [RuntimeClass 类](../windows/runtimeclass-class.md)