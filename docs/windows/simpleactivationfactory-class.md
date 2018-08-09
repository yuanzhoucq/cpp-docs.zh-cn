---
title: SimpleActivationFactory 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- SimpleActivationFactory class
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: adbc7b6bbeafff277f32170627d6804526900049
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019012"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory 类
提供创建 Windows 运行时或经典 COM 基类的基础机制。  
  
## <a name="syntax"></a>语法  
  
```cpp  
template<typename Base>  
class SimpleActivationFactory : public ActivationFactory<>;  
```  
  
### <a name="parameters"></a>参数  
 *基本*  
 基类。  
  
## <a name="remarks"></a>备注  
 类的基类必须提供默认构造函数。  
  
 下面的代码示例演示如何使用与 SimpleActivationFactory [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)宏。  
  
 `ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`  
  
## <a name="members"></a>成员  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[SimpleActivationFactory::ActivateInstance 方法](../windows/simpleactivationfactory-activateinstance-method.md)|创建指定接口的实例。|  
|[SimpleActivationFactory::GetRuntimeClassName 方法](../windows/simpleactivationfactory-getruntimeclassname-method.md)|获取指定的类的实例的运行时类名称*Base*类模板参数。|  
|[SimpleActivationFactory::GetTrustLevel 方法](../windows/simpleactivationfactory-gettrustlevel-method.md)|获取指定的类的实例的信任级别*Base*类模板参数。|  
  
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
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)