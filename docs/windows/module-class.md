---
title: "Module 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Module"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Module 类"
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Module 类
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

模块表示一组相关的对象。  
  
## 语法  
  
```  
  
template<  
   ModuleType moduleType  
>  
class Module;  
  
template<>  
class Module<InProc> : public Details::ModuleBase;  
  
template<>  
class Module<OutOfProc> : public Module<InProc>;  
```  
  
#### 参数  
 `moduleType`  
 一个或多个 [ModuleType](../windows/moduletype-enumeration.md) 枚举值的组合。  
  
## 成员  
  
### 受保护的类  
  
|名称|说明|  
|--------|--------|  
|[Module::GenericReleaseNotifier 类](../windows/module-genericreleasenotifier-class.md)|在当前模块的最后一个对象解锁时，将调用事件处理程序。  事件处理程序在 lambda、functor 或函数指针。|  
|[Module::MethodReleaseNotifier 类](../windows/module-methodreleasenotifier-class.md)|在当前模块的最后一个对象解锁时，将调用事件处理程序。  事件处理程序是由对象及其方法指定指针成员。|  
|[Module::ReleaseNotifier 类](../windows/module-releasenotifier-class.md)|在当前模块的最后一个对象解锁时，将调用事件处理程序。|  
  
### 公共构造函数  
  
|名称|说明|  
|--------|--------|  
|[Module::~Module 析构函数](../windows/module-tilde-module-destructor.md)|取消初始化 RuntimeClass 类的当前实例。|  
  
### 受保护的构造函数  
  
|名称|说明|  
|--------|--------|  
|[Module::Module 构造函数](../windows/module-module-constructor.md)|初始化 Module 类的新实例。|  
  
### 公共方法  
  
|名称|说明|  
|--------|--------|  
|[Module::Create 方法](../windows/module-create-method.md)|创建模块的实例。|  
|[Module::DecrementObjectCount 方法](../windows/module-decrementobjectcount-method.md)|递增模块跟踪的对象的数量。|  
|[Module::GetActivationFactory 方法](../windows/module-getactivationfactory-method.md)|获取模块的一个活动工厂|  
|[Module::GetClassObject 方法](../windows/module-getclassobject-method.md)|检索缓存类工厂。|  
|[Module::GetModule 方法](../windows/module-getmodule-method.md)|创建模块的实例。|  
|[Module::GetObjectCount 方法](../windows/module-getobjectcount-method.md)|检索此模块管理对象的数量。|  
|[Module::IncrementObjectCount 方法](../windows/module-incrementobjectcount-method.md)|递增模块跟踪的对象的数量。|  
|[Module::RegisterCOMObject 方法](../windows/module-registercomobject-method.md)|注册取消一个或多个对象，以便在其他应用程序无法连接到它们。|  
|[Module::RegisterObjects 方法](../windows/module-registerobjects-method.md)|注册 COM 对象或 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]，因此其他应用程序可以连接到它们。|  
|[Module::RegisterWinRTObject 方法](../windows/module-registerwinrtobject-method.md)|注册取消一个或多个对象[!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]，以便在其他应用程序无法连接到它们。|  
|[Module::Terminate 方法](../windows/module-terminate-method.md)|生成模块实例化的任何工厂关闭。|  
|[Module::UnregisterCOMObject 方法](../windows/module-unregistercomobject-method.md)|取消一个或多个 COM 对象，阻止其他应用程序连接到它们。|  
|[Module::UnregisterObjects 方法](../windows/module-unregisterobjects-method.md)|取消在指定模块的对象，以便在其他应用程序无法连接到它们。|  
|[Module::UnregisterWinRTObject 方法](../windows/module-unregisterwinrtobject-method.md)|取消一个或多个 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 对象，以便在其他应用程序无法连接到它们。|  
  
### 受保护的方法  
  
|名称|说明|  
|--------|--------|  
|[Module::Create 方法](../windows/module-create-method.md)|创建模块的实例。|  
  
### 受保护的数据成员  
  
|名称|说明|  
|--------|--------|  
|[Module::objectCount\_ 数据成员](../windows/module-objectcount-data-member.md)|记录的类创建的函数 [生成](../windows/make-function.md)。|  
|[Module::releaseNotifier\_ 数据成员](../windows/module-releasenotifier-data-member.md)|包含指向 ReleaseNotifier 对象。|  
  
### 宏  
  
|||  
|-|-|  
|[ActivatableClass](../windows/activatableclass-macros.md)|填充：，填充包含创建工厂可以指定类的实例的内部缓存。  该宏指定工厂和默认组标识参数。|  
|[ActivatableClassWithFactory](../windows/activatableclass-macros.md)|填充：，填充包含创建工厂可以指定类的实例的内部缓存。  此宏可以指定特定参数工厂。|  
|[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)|填充：，填充包含创建工厂可以指定类的实例的内部缓存。  此宏可以指定特殊工厂和组标识参数。|  
  
## 继承层次结构  
 `ModuleBase`  
  
 `Module`  
  
 `Module`  
  
## 要求  
 **标头:** module.h  
  
 **命名空间:** Microsoft::WRL  
  
## 请参阅  
 [Microsoft::WRL 命名空间](../windows/microsoft-wrl-namespace.md)