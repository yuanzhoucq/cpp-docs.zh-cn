---
title: 'Weakreference:: Incrementstrongreference 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- IncrementStrongReference method
ms.assetid: d0232426-a8cb-48b4-99d4-165de2d66cb9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee53e068c13f52c01e997680b57915051a8efad8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="weakreferenceincrementstrongreference-method"></a>WeakReference::IncrementStrongReference 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
ULONG IncrementStrongReference();  
```  
  
## <a name="return-value"></a>返回值  
 递增的强引用计数。  
  
## <a name="remarks"></a>备注  
 递增当前 WeakReference 对象的强引用计数。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
[WeakReference 类](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)