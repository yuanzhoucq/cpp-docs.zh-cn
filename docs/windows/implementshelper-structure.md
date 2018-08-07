---
title: ImplementsHelper 结构 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
dev_langs:
- C++
helpviewer_keywords:
- ImplementsHelper structure
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5e5da95e6cfb276704b5cd6150e4abc2921a5701
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605612"
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
  
### <a name="parameters"></a>参数  
 *RuntimeClassFlagsT*  
 指定一个或多个标记的字段[RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举器。  
  
 *ILst*  
 接口 Id 的列表。  
  
 *IsDelegateToClass*  
 指定 **，则返回 true**如果的当前实例`Implements`是一个基类中的第一个接口 ID *ILst*; 否则为**false**。  
  
## <a name="remarks"></a>备注  
 可帮助实现[实现](../windows/implements-structure.md)结构。  
  
 此模板会遍历接口的列表，并将它们添加作为基类，这些类，以及启用 QueryInterface 所需的信息。  
  
## <a name="members"></a>成员  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ImplementsHelper`  
  
## <a name="requirements"></a>要求  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [参考 （Windows 运行时库）](http://msdn.microsoft.com/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)