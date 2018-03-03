---
title: "ActivationFactory 类 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- ActivationFactory class
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 73690603b1be1dd74b7ae7626372e3ab6ff9101e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="activationfactory-class"></a>ActivationFactory 类
启用 Windows 运行时将激活的一个或多个类。  
  
## <a name="syntax"></a>语法  
  
```  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ActivationFactory : public Details::RuntimeClass<typename Details::InterfaceListHelper<IActivationFactory, I0, I1, I2, Details::Nil>::TypeT, RuntimeClassFlags<WinRt | InhibitWeakReference>, false>;  
```  
  
#### <a name="parameters"></a>参数  
 `I0`  
 第零个接口中。  
  
 `I1`  
 第一个接口。  
  
 `I2`  
 第二个接口。  
  
## <a name="remarks"></a>备注  
 ActivationFactory 提供注册方法和 IActivationFactory 接口的基本功能。 ActivationFactory 还使你能够提供的自定义工厂实现。  
  
 下面的代码段以符号方式说明了如何使用 ActivationFactory。  
  
 [!code-cpp[wrl-microsoft__wrl__activationfactory#1](../windows/codesnippet/CPP/activationfactory-class_1.cpp)]  
  
 下面的代码段演示如何使用[实现](../windows/implements-structure.md)结构，以指定超过三个接口 Id。  
  
 `struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`  
  
## <a name="members"></a>成员  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[ActivationFactory::ActivationFactory 构造函数](../windows/activationfactory-activationfactory-constructor.md)|初始化 ActivationFactory 类。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[ActivationFactory::AddRef 方法](../windows/activationfactory-addref-method.md)|递增当前 ActivationFactory 对象的引用计数。|  
|[ActivationFactory::GetIids 方法](../windows/activationfactory-getiids-method.md)|检索已实现接口 ID 的数组。|  
|[ActivationFactory::GetRuntimeClassName 方法](../windows/activationfactory-getruntimeclassname-method.md)|获取当前 ActivationFactory 实例化的对象的运行时类名称。|  
|[ActivationFactory::GetTrustLevel 方法](../windows/activationfactory-gettrustlevel-method.md)|获取当前 ActivationFactory 实例化的对象的信任级别。|  
|[ActivationFactory::QueryInterface 方法](../windows/activationfactory-queryinterface-method.md)|检索指向指定接口的指针。|  
|[ActivationFactory::Release 方法](../windows/activationfactory-release-method.md)|递减引用计数的当前 ActivationFactory 对象。|  
  
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
  
## <a name="requirements"></a>惠?  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)