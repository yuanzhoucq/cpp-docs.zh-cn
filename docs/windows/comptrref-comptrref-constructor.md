---
title: 'Comptrref:: Comptrref 构造函数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::ComPtrRef
dev_langs:
- C++
helpviewer_keywords:
- ComPtrRef, constructor
ms.assetid: ce2d2533-fef6-4b2d-b088-6f3db01df5a5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 621f852728cb40ea88a916b37147c28d8bb0db38
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644457"
---
# <a name="comptrrefcomptrref-constructor"></a>ComPtrRef::ComPtrRef 构造函数
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
ComPtrRef(  
   _In_opt_ T* ptr  
);  
```  
  
### <a name="parameters"></a>参数  
 *ptr*  
 基础值的另一个**ComPtrRef**对象。  
  
## <a name="remarks"></a>备注  
 初始化的新实例**ComPtrRef**到另一个类从指定的指针**ComPtrRef**对象。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [ComPtrRef 类](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)