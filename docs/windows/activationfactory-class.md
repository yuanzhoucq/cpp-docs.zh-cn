---
title: "ActivationFactory 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::ActivationFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActivationFactory 类"
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActivationFactory 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

启用 Windows 运行时将激活的一个或多个类。  
  
## 语法  
  
```  
template <  
   typename I0 = Details::Nil,  
   typename I1 = Details::Nil,  
   typename I2 = Details::Nil  
>  
class ActivationFactory : public Details::RuntimeClass<typename Details::InterfaceListHelper<IActivationFactory, I0, I1, I2, Details::Nil>::TypeT, RuntimeClassFlags<WinRt | InhibitWeakReference>, false>;  
```  
  
#### 参数  
 `I0`  
 第零个接口。  
  
 `I1`  
 第一个接口 ID。  
  
 `I2`  
 第二个接口 ID。  
  
## 备注  
 ActivationFactory 为 IActivationFactory 注册接口提供方法和基本功能。  ActivationFactory 还可以提供自为工厂定义实现。  
  
 下面的代码片段演示如何使用标记 ActivationFactory。  
  
 [!code-cpp[wrl-microsoft__wrl__activationfactory#1](../windows/codesnippet/CPP/activationfactory-class_1.cpp)]  
  
 下面的代码片段演示如何使用 [实现](../windows/implements-structure.md) 结构指定多三个接口 ID。  
  
 `struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`  
  
## 成员  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[ActivationFactory::ActivationFactory 构造函数](../windows/activationfactory-activationfactory-constructor.md)|初始化类工厂的实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[ActivationFactory::AddRef 方法](../windows/activationfactory-addref-method.md)|递增ActivationFactory 当前对象的引用计数。|  
|[ActivationFactory::GetIids 方法](../windows/activationfactory-getiids-method.md)|检索数组实现的接口 ID。|  
|[ActivationFactory::GetRuntimeClassName 方法](../windows/activationfactory-getruntimeclassname-method.md)|获取当前 ActivationFactory 实例化对象的运行时类名。|  
|[ActivationFactory::GetTrustLevel 方法](../windows/activationfactory-gettrustlevel-method.md)|获取当前 ActivationFactory 实例化对象的信任级别。|  
|[ActivationFactory::QueryInterface 方法](../windows/activationfactory-queryinterface-method.md)|检索特定接口的指针。|  
|[ActivationFactory::Release 方法](../windows/activationfactory-release-method.md)|递减 ActivationFactory 当前对象的引用计数。|  
  
## 继承层次结构  
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
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)