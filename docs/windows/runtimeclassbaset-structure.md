---
title: RuntimeClassBaseT 结构 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::RuntimeClassBaseT
dev_langs:
- C++
ms.assetid: a62775fb-3359-4f45-9ff1-c07fa8da464b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3ea147ebddff03401f6151bcdc44d96efb233f90
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33888978"
---
# <a name="runtimeclassbaset-structure"></a>RuntimeClassBaseT 结构
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   unsigned int RuntimeClassTypeT  
>  
friend struct Details::RuntimeClassBaseT;  
```  
  
#### <a name="parameters"></a>参数  
 `RuntimeClassTypeT`  
 指定一个或多个标志的字段[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举器。  
  
## <a name="remarks"></a>备注  
 提供用于 helper 方法`QueryInterface`操作和获取的接口 Id。  
  
## <a name="members"></a>成员  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `RuntimeClassBaseT`  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [参考 （Windows 运行时库）](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)