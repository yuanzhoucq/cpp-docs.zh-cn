---
title: 'Mutextraits:: Unlock 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits::Unlock
dev_langs:
- C++
helpviewer_keywords:
- Unlock method
ms.assetid: 7c4e5664-6d95-498a-95bb-d30b5e866c2c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1925755ca663ba82526fb8b8dae626165f1e4862
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606678"
---
# <a name="mutextraitsunlock-method"></a>MutexTraits::Unlock 方法
释放全权控制共享资源。  
  
## <a name="syntax"></a>语法  
  
```  
inline static void Unlock(  
   _In_ Type h  
);  
```  
  
### <a name="parameters"></a>参数  
 *h*  
 互斥体对象的句柄。  
  
## <a name="return-value"></a>返回值  
  
## <a name="requirements"></a>要求  
 **标头：** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::HandleTraits  
  
## <a name="see-also"></a>请参阅  
 [MutexTraits 结构](../windows/mutextraits-structure.md)