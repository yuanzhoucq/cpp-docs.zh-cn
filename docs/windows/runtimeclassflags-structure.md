---
title: "RuntimeClassFlags 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClassFlags
dev_langs: C++
helpviewer_keywords: RuntimeClassFlags structure
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 85eb42c537845d86ce8cf3b1f20db7e9eeffe76f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags 结构
包含的实例类型[RuntimeClass](../windows/runtimeclass-class.md)。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   unsigned int flags  
>  
struct RuntimeClassFlags;  
```  
  
#### <a name="parameters"></a>参数  
 `flags`  
 A [RuntimeClassType 枚举](../windows/runtimeclasstype-enumeration.md)值。  
  
## <a name="members"></a>成员  
  
### <a name="public-constants"></a>公共常量  
  
|name|描述|  
|----------|-----------------|  
|[RuntimeClassFlags::value 常量](../windows/runtimeclassflags-value-constant.md)|包含[RuntimeClassType 枚举](../windows/runtimeclasstype-enumeration.md)值。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `RuntimeClassFlags`  
  
## <a name="requirements"></a>惠?  
 **标头：** implements.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)