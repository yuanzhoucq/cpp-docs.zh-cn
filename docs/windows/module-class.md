---
title: Module 类 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module
dev_langs:
- C++
helpviewer_keywords:
- Module class
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a4c437035713634736a02afbce1325d14ba18229
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604406"
---
# <a name="module-class"></a>Module 类
表示相关对象的集合。  
  
## <a name="syntax"></a>语法  
  
```  
template<ModuleType moduleType>  
class Module;  
  
template<>  
class Module<InProc> : public Details::ModuleBase;  
  
template<>  
class Module<OutOfProc> : public Module<InProc>;  
```  
  
### <a name="parameters"></a>参数  
 *moduleType*  
 一个或多个组合[ModuleType](../windows/moduletype-enumeration.md)枚举值。  
  
## <a name="members"></a>成员  
  
### <a name="protected-classes"></a>受保护的类  
  
|name|描述|  
|----------|-----------------|  
|[Module::GenericReleaseNotifier 类](../windows/module-genericreleasenotifier-class.md)|在释放当前模块中的最后一个对象时调用事件处理程序。 事件处理程序由 lambda、functor 或 pointer-to-function 指定。|  
|[Module::MethodReleaseNotifier 类](../windows/module-methodreleasenotifier-class.md)|在释放当前模块中的最后一个对象时调用事件处理程序。 对象并将其指针到方法成员由指定的事件处理程序。|  
|[Module::ReleaseNotifier 类](../windows/module-releasenotifier-class.md)|在释放模块中的最后一个对象时调用事件处理程序。|  
  
### <a name="public-constructors"></a>公共构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[Module::~Module 析构函数](../windows/module-tilde-module-destructor.md)|取消初始化的当前实例**模块**类。|  
  
### <a name="protected-constructors"></a>受保护的构造函数  
  
|名称|描述|  
|----------|-----------------|  
|[Module::Module 构造函数](../windows/module-module-constructor.md)|初始化的新实例**模块**类。|  
  
### <a name="public-methods"></a>公共方法  
  
|名称|描述|  
|----------|-----------------|  
|[Module::Create 方法](../windows/module-create-method.md)|创建模块的实例。|  
|[Module::DecrementObjectCount 方法](../windows/module-decrementobjectcount-method.md)|递减模块所跟踪对象的数量。|  
|[Module::GetActivationFactory 方法](../windows/module-getactivationfactory-method.md)|获取模块的激活工厂。|  
|[Module::GetClassObject 方法](../windows/module-getclassobject-method.md)|检索类工厂的缓存。|  
|[Module::GetModule 方法](../windows/module-getmodule-method.md)|创建模块的实例。|  
|[Module::GetObjectCount 方法](../windows/module-getobjectcount-method.md)|检索此模块管理的对象数量。|  
|[Module::IncrementObjectCount 方法](../windows/module-incrementobjectcount-method.md)|递增模块所跟踪对象的数量。|  
|[Module::RegisterCOMObject 方法](../windows/module-registercomobject-method.md)|注册一个或多个 COM 对象，以便其他应用程序可连接到它们。|  
|[Module::RegisterObjects 方法](../windows/module-registerobjects-method.md)|注册 COM 或 Windows 运行时对象，以便其他应用程序可以连接到它们。|  
|[Module::RegisterWinRTObject 方法](../windows/module-registerwinrtobject-method.md)|注册一个或多个 Windows 运行时对象，以便其他应用程序可以连接到它们。|  
|[Module::Terminate 方法](../windows/module-terminate-method.md)|导致关闭模块实例化的所有工厂。|  
|[Module::UnregisterCOMObject 方法](../windows/module-unregistercomobject-method.md)|注销一个或多个 COM 对象，以阻止其他应用程序连接到它们。|  
|[Module::UnregisterObjects 方法](../windows/module-unregisterobjects-method.md)|取消指定模块中的对象，以便其他应用程序无法连接到它们。|  
|[Module::UnregisterWinRTObject 方法](../windows/module-unregisterwinrtobject-method.md)|注销一个或多个 Windows 运行时对象，以便其他应用程序无法连接到它们。|  
  
### <a name="protected-methods"></a>受保护的方法  
  
|名称|描述|  
|----------|-----------------|  
|[Module::Create 方法](../windows/module-create-method.md)|创建模块的实例。|  
  
### <a name="protected-data-members"></a>受保护的数据成员  
  
|name|描述|  
|----------|-----------------|  
|[Module::objectCount_ 数据成员](../windows/module-objectcount-data-member.md)|跟踪已使用创建多少个类的[使](../windows/make-function.md)函数。|  
|[Module::releaseNotifier_ 数据成员](../windows/module-releasenotifier-data-member.md)|包含指向 ReleaseNotifier 对象的指针。|  
  
### <a name="macros"></a>宏  
  
|||  
|-|-|  
|[ActivatableClass](../windows/activatableclass-macros.md)|填充内部缓存，其中包含一个工厂，它可以创建指定类的实例。 此宏指定默认工厂和组 ID 参数。|  
|[ActivatableClassWithFactory](../windows/activatableclass-macros.md)|填充内部缓存，其中包含一个工厂，它可以创建指定类的实例。 此宏可用于指定特定工厂参数。|  
|[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)|填充内部缓存，其中包含一个工厂，它可以创建指定类的实例。 此宏可用于指定特定工厂和组 ID 参数。|  
  
## <a name="inheritance-hierarchy"></a>继承层次结构  
 `ModuleBase`  
  
 `Module`  
  
 `Module`  
  
## <a name="requirements"></a>要求  
 **标头：** module.h  
  
 **命名空间：** Microsoft::WRL  
  
## <a name="see-also"></a>请参阅  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)