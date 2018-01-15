---
title: "Argtraits:: Args 常量 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::ArgTraits::args
dev_langs: C++
helpviewer_keywords: args constant
ms.assetid: a68100ab-254b-4571-a0bc-946f1633a46b
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: baf5f0fa0e95498f677615802b250b56fd94afec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
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
  
## <a name="requirements"></a>惠?  
 **标头：** event.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [ArgTraits 结构](../windows/argtraits-structure.md)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)