---
title: "ImplementsHelper 结构 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
dev_langs:
- C++
helpviewer_keywords:
- ImplementsHelper structure
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a51de59278e476be1e99b60ef1b0ab8a6e3f3cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="implementshelper-structure"></a>ImplementsHelper 结构
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   typename RuntimeClassFlagsT,  
   typename ILst,  
   bool IsDelegateToClass  
>  
friend struct Details::ImplementsHelper;  
```  
  
#### <a name="parameters"></a>参数  
 `RuntimeClassFlagsT`  
 指定一个或多个标志的字段[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举器。  
  
 `ILst`  
 接口 Id 的列表。  
  
 `IsDelegateToClass`  
 指定`true`中的第一个接口 ID 的基类实现的当前实例是否`ILst`; 否则为`false`。  
  
## <a name="remarks"></a>备注  
 可帮助实现[实现](../windows/implements-structure.md)结构。  
  
 此模板遍历接口的列表，并将它们添加用作基类，这些类，以及启用 QueryInterface 所需的信息。  
  
## <a name="members"></a>成员  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ImplementsHelper`  
  
## <a name="requirements"></a>惠?  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [参考 （Windows 运行时库）](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)