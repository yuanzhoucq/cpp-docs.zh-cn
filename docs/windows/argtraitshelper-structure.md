---
title: "ArgTraitsHelper 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::ArgTraitsHelper
dev_langs: C++
helpviewer_keywords: ArgTraitsHelper structure
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 31d9072ebf8c36453a74c75ff4a8997805d0973f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper 结构
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
template<  
   typename TDelegateInterface  
>  
struct ArgTraitsHelper;  
```  
  
#### <a name="parameters"></a>参数  
 `TDelegateInterface`  
 一种委托接口。  
  
## <a name="remarks"></a>备注  
 可帮助定义委托自变量的共同的特征。  
  
## <a name="members"></a>成员  
  
### <a name="public-typedefs"></a>公共 Typedef  
  
|名称|描述|  
|----------|-----------------|  
|`methodType`|`decltype(&TDelegateInterface::Invoke)` 的同义词。|  
|`Traits`|`ArgTraits<methodType>` 的同义词。|  
  
### <a name="public-constants"></a>公共常量  
  
|name|描述|  
|----------|-----------------|  
|[ArgTraitsHelper::args 常量](../windows/argtraitshelper-args-constant.md)|可帮助[argtraits:: Args](../windows/argtraits-args-constant.md)上调用方法的委托接口中保留的参数数目的计数。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ArgTraitsHelper`  
  
## <a name="requirements"></a>惠?  
 **标头：** event.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)