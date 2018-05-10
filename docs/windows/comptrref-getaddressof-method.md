---
title: 'Comptrref:: Getaddressof 方法 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRef::GetAddressOf
dev_langs:
- C++
helpviewer_keywords:
- GetAddressOf method
ms.assetid: 797df323-a2fa-412b-ab60-32cce3721096
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5dc8e80fe97bc0a4ace0cb53e43f306ad2b85309
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="comptrrefgetaddressof-method"></a>ComPtrRef::GetAddressOf 方法
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
InterfaceType* const * GetAddressOf() const;  
```  
  
## <a name="return-value"></a>返回值  
 由当前 ComPtrRef 对象表示的接口的指针的地址。  
  
## <a name="remarks"></a>备注  
 检索用当前 ComPtrRef 对象表示的接口的指针的地址。  
  
## <a name="requirements"></a>要求  
 **标头：** client.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [ComPtrRef 类](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)