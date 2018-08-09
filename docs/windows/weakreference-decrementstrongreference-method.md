---
title: 'Weakreference:: Decrementstrongreference 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
dev_langs:
- C++
helpviewer_keywords:
- DecrementStrongReference method
ms.assetid: 97d70d9f-41b8-4f8d-a6fa-4137cc4f9029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19dcb3e90faef86fd291381a7082e8b5bfa89069
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013452"
---
# <a name="weakreferencedecrementstrongreference-method"></a>WeakReference::DecrementStrongReference 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```cpp  
ULONG DecrementStrongReference();  
```  
  
## <a name="remarks"></a>备注  
 当前的强引用计数的递减**WeakReference**对象。  
  
 当强引用计数变为零时，强引用设置为**nullptr**。  
  
## <a name="return-value"></a>返回值  
 递减的强引用计数。  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [WeakReference 类](../windows/weakreference-class1.md)  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)