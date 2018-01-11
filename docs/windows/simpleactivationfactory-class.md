---
title: "SimpleActivationFactory 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::SimpleActivationFactory
dev_langs: C++
helpviewer_keywords: SimpleActivationFactory class
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 991d428e90654fd29cfbb9c5c7e110708a05de01
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory 类
提供创建 Windows 运行时或经典 COM 基类的基础机制。  
  
## <a name="syntax"></a>语法  
  
```  
template<  
   typename Base  
>  
class SimpleActivationFactory : public ActivationFactory<>;  
```  
  
#### <a name="parameters"></a>参数  
 `Base`  
 基类。  
  
## <a name="remarks"></a>备注  
 基类必须提供一个默认构造函数。  
  
 下面的代码示例演示如何使用与 SimpleActivationFactory [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)宏。  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[SimpleActivationFactory::ActivateInstance 方法](../windows/simpleactivationfactory-activateinstance-method.md)|创建指定的接口的实例。|  
|[SimpleActivationFactory::GetRuntimeClassName 方法](../windows/simpleactivationfactory-getruntimeclassname-method.md)|获取指定的类的实例的运行时类名称`Base`类模板参数。|  
|[SimpleActivationFactory::GetTrustLevel 方法](../windows/simpleactivationfactory-gettrustlevel-method.md)|获取指定的类的实例的信任级别`Base`类模板参数。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `I0`  
  
 `ChainInterfaces`  
  
 `I0`  
  
 `RuntimeClassBase`  
  
 `ImplementsHelper`  
  
 `DontUseNewUseMake`  
  
 `RuntimeClassFlags`  
  
 `RuntimeClassBaseT`  
  
 `RuntimeClass`  
  
 `ActivationFactory`  
  
 `SimpleActivationFactory`  
  
## <a name="requirements"></a>惠?  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)