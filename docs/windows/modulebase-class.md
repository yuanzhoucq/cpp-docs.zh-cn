---
title: "ModuleBase 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::ModuleBase
dev_langs: C++
helpviewer_keywords: ModuleBase class
ms.assetid: edce7591-6893-46f7-94a7-382827775548
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b02efe3ee61234b2439c1cbbae07827d6a879b2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="modulebase-class"></a>ModuleBase 类
支持 WRL 基础结构，不应在代码中直接使用。  
  
## <a name="syntax"></a>语法  
  
```  
class ModuleBase;  
```  
  
## <a name="remarks"></a>备注  
 表示类的基类[模块](../windows/module-class.md)类。  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[ModuleBase::ModuleBase 构造函数](../windows/modulebase-modulebase-constructor.md)|初始化 Module 类的实例。|  
|[ModuleBase::~ModuleBase 析构函数](../windows/modulebase-tilde-modulebase-destructor.md)|取消初始化 Module 类的当前实例。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[ModuleBase::DecrementObjectCount 方法](../windows/modulebase-decrementobjectcount-method.md)|在实现时，递减的对象数模块所跟踪。|  
|[ModuleBase::IncrementObjectCount 方法](../windows/modulebase-incrementobjectcount-method.md)|在实现时，递增模块所跟踪的对象数。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ModuleBase`  
  
## <a name="requirements"></a>惠?  
 **标头：** implements.h  
  
 **Namespace:** Microsoft::WRL::Details  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL::Details 命名空间](../windows/microsoft-wrl-details-namespace.md)