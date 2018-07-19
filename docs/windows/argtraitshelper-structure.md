---
title: ArgTraitsHelper 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraitsHelper
dev_langs:
- C++
helpviewer_keywords:
- ArgTraitsHelper structure
ms.assetid: e3f798da-0aef-4a57-95d3-d38c34c47d72
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6205d69962d70d9da76c932fdd8b3f66f491ebc9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857696"
---
# <a name="argtraitshelper-structure"></a>ArgTraitsHelper 结构
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
template<typename TDelegateInterface>  
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
  
|名称|描述|  
|----------|-----------------|  
|[ArgTraitsHelper::args 常量](../windows/argtraitshelper-args-constant.md)|可帮助[argtraits:: Args](../windows/argtraits-args-constant.md)上调用方法的委托接口中保留的参数数目的计数。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ArgTraitsHelper`  
  
## <a name="requirements"></a>要求  
 **标头：** event.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)