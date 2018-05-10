---
title: 'Argtraits:: Args 常量 |Microsoft 文档'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits::args
dev_langs:
- C++
helpviewer_keywords:
- args constant
ms.assetid: a68100ab-254b-4571-a0bc-946f1633a46b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f87b29634d5b9acef2e2ccb3f7b4d5f227433d38
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="argtraitsargs-constant"></a>ArgTraits::args 常量
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
static const int args = -1; ;  
```  
  
## <a name="remarks"></a>备注  
 保留的调用方法的委托接口上的参数数目的计数。  
  
## <a name="remarks"></a>备注  
 当`args`等于-1 指示可以 Invoke 方法签名没有匹配项。  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [ArgTraits 结构](../windows/argtraits-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)