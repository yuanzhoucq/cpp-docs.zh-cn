---
title: Module 类 |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module
- module/Microsoft::WRL::Module::Create
- module/Microsoft::WRL::Module::DecrementObjectCount
- module/Microsoft::WRL::Module::GetActivationFactory
- module/Microsoft::WRL::Module::GetClassObject
- module/Microsoft::WRL::Module::GetModule
- module/Microsoft::WRL::Module::GetObjectCount
- module/Microsoft::WRL::Module::IncrementObjectCount
- module/Microsoft::WRL::Module::Module
- module/Microsoft::WRL::Module::objectCount_Data
- module/Microsoft::WRL::Module::RegisterCOMObject
- module/Microsoft::WRL::Module::RegisterObjects
- module/Microsoft::WRL::Module::RegisterWinRTObject
- module/Microsoft::WRL::Module::releaseNotifier_
- module/Microsoft::WRL::Module::Terminate
- module/Microsoft::WRL::Module::~Module
- module/Microsoft::WRL::Module::UnregisterCOMObject
- module/Microsoft::WRL::Module::UnregisterObjects
- module/Microsoft::WRL::Module::UnregisterWinRTObject
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Module class
- Microsoft::WRL::Module::Create method
- Microsoft::WRL::Module::DecrementObjectCount method
- Microsoft::WRL::Module::GetActivationFactory method
- Microsoft::WRL::Module::GetClassObject method
- Microsoft::WRL::Module::GetModule method
- Microsoft::WRL::Module::GetObjectCount method
- Microsoft::WRL::Module::IncrementObjectCount method
- Microsoft::WRL::Module::Module, constructor
- Microsoft::WRL::Module::objectCount_ data member
- Microsoft::WRL::Module::RegisterCOMObject method
- Microsoft::WRL::Module::RegisterObjects method
- Microsoft::WRL::Module::RegisterWinRTObject method
- Microsoft::WRL::Module::releaseNotifier_ data member
- Microsoft::WRL::Module::Terminate method
- Microsoft::WRL::Module::~Module, destructor
- Microsoft::WRL::Module::UnregisterCOMObject method
- Microsoft::WRL::Module::UnregisterObjects method
- Microsoft::WRL::Module::UnregisterWinRTObject method
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2357790e3084c91011f16eb9f1f718948462f898
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/25/2018
ms.locfileid: "50059475"
---
# <a name="module-class"></a>Module 类

表示相关对象的集合。

## <a name="syntax"></a>语法

```cpp
template<ModuleType moduleType>
class Module;

template<>
class Module<InProc> : public Details::ModuleBase;

template<>
class Module<OutOfProc> : public Module<InProc>;
```

### <a name="parameters"></a>参数

*moduleType*<br/>
一个或多个组合[ModuleType](../windows/moduletype-enumeration.md)枚举值。

## <a name="members"></a>成员

### <a name="protected-classes"></a>受保护的类

name                                                                                | 描述
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Module:: genericreleasenotifier](../windows/module-genericreleasenotifier-class.md) | 在释放当前模块中的最后一个对象时调用事件处理程序。 事件处理程序由 lambda、functor 或 pointer-to-function 指定。
[Module:: methodreleasenotifier](../windows/module-methodreleasenotifier-class.md)   | 在释放当前模块中的最后一个对象时调用事件处理程序。 对象并将其指针到方法成员由指定的事件处理程序。
[Module:: releasenotifier](../windows/module-releasenotifier-class.md)               | 在释放模块中的最后一个对象时调用事件处理程序。

### <a name="public-constructors"></a>公共构造函数

名称                             | 描述
-------------------------------- | -----------------------------------------------------------
[模块:: ~ 模块](#tilde-module) | 取消初始化的当前实例`Module`类。

### <a name="protected-constructors"></a>受保护的构造函数

名称                      | 描述
------------------------- | ---------------------------------------------------
[Module:: module](#module) | 初始化 `Module` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                                                    | 描述
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Module:: create](#create)                               | 创建模块的实例。
[Module:: decrementobjectcount](#decrementobjectcount)   | 递减模块所跟踪对象的数量。
[Module:: getactivationfactory](#getactivationfactory)   | 获取模块的激活工厂。
[Module:: getclassobject](#getclassobject)               | 检索类工厂的缓存。
[Module:: getmodule](#getmodule)                         | 创建模块的实例。
[Module:: getobjectcount](#getobjectcount)               | 检索此模块管理的对象数量。
[Module:: incrementobjectcount](#incrementobjectcount)   | 递增模块所跟踪对象的数量。
[Module:: registercomobject](#registercomobject)         | 注册一个或多个 COM 对象，以便其他应用程序可连接到它们。
[Module:: registerobjects](#registerobjects)             | 注册 COM 或 Windows 运行时对象，以便其他应用程序可以连接到它们。
[Module:: registerwinrtobject](#registerwinrtobject)     | 注册一个或多个 Windows 运行时对象，以便其他应用程序可以连接到它们。
[Module:: terminate](#terminate)                         | 导致关闭模块实例化的所有工厂。
[Module:: unregistercomobject](#unregistercomobject)     | 注销一个或多个 COM 对象，以阻止其他应用程序连接到它们。
[Module:: unregisterobjects](#unregisterobjects)         | 取消指定模块中的对象，以便其他应用程序无法连接到它们。
[Module:: unregisterwinrtobject](#unregisterwinrtobject) | 注销一个或多个 Windows 运行时对象，以便其他应用程序无法连接到它们。

### <a name="protected-methods"></a>受保护的方法

名称                      | 描述
------------------------- | --------------------------------
[Module:: create](#create) | 创建模块的实例。

### <a name="protected-data-members"></a>受保护的数据成员

name                                         | 描述
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Module:: objectcount_](#objectcount)         | 跟踪已使用创建多少个类的[使](../windows/make-function.md)函数。
[Module:: releasenotifier_](#releasenotifier) | 包含一个指向`ReleaseNotifier`对象。

### <a name="macros"></a>宏

名称 |说明-----|---美元[ActivatableClass](../windows/activatableclass-macros.md) | 填充内部缓存，其中包含一个工厂，它可以创建指定类的实例。 此宏指定默认工厂和组 ID 参数。
[ActivatableClassWithFactory](../windows/activatableclass-macros.md) |填充内部缓存，其中包含一个工厂，它可以创建指定类的实例。 此宏可用于指定特定工厂参数。
[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md) |填充内部缓存，其中包含一个工厂，它可以创建指定类的实例。 此宏可用于指定特定工厂和组 ID 参数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>要求

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="tilde-module"></a>模块:: ~ 模块

取消初始化的当前实例`Module`类。

```cpp
virtual ~Module();
```

## <a name="create"></a>Module:: create

创建模块的实例。

```cpp
WRL_NOTHROW static Module& Create();
template<typename T>
WRL_NOTHROW static Module& Create(
   T callback
);
template<typename T>
WRL_NOTHROW static Module& Create(
   _In_ T* object,
   _In_ void (T::* method)()
);
```

### <a name="parameters"></a>参数

*T*<br/>
模块类型。

*回调*<br/>
释放该模块的最后一个实例对象时调用。

*object*<br/>
*对象*并*方法*结合使用的参数。 点到最后一个实例对象时释放模块中的最后一个实例对象。

*方法*<br/>
*对象*并*方法*结合使用的参数。 指向最后一个实例对象时释放模块中的最后一个实例对象的方法。

### <a name="return-value"></a>返回值

对模块引用。

## <a name="decrementobjectcount"></a>Module:: decrementobjectcount

递减模块所跟踪对象的数量。

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>返回值

递减操作之前的计数。

## <a name="getactivationfactory"></a>Module:: getactivationfactory

获取模块的激活工厂。

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>参数

*pActivatibleClassId*<br/>
运行时类的 IID。

*ppIFactory*<br/>
指定运行时类的 IActivationFactory。

*服务器名称*<br/>
当前模块中类工厂的子集名称。 指定中使用的服务器名称[ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)宏，或指定`nullptr`若要获取默认服务器名称。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为 GetActivationFactory 返回的 HRESULT。

## <a name="getclassobject"></a>Module:: getclassobject

检索类工厂的缓存。

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>参数

*clsid*<br/>
类 ID。

*riid*<br/>
您请求的接口 ID。

*ppv*<br/>
指向返回对象的指针。

*服务器名称*<br/>
在 `ActivatableClassWithFactory`、`ActivatableClassWithFactoryEx` 或 `ActivatableClass` 宏中指定的服务器名称；或用于获取默认服务器名称的 `nullptr`。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

仅对 COM 而不是 Windows 运行时使用此方法。 此方法仅公开`IClassFactory`方法。

## <a name="getmodule"></a>Module:: getmodule

创建模块的实例。

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>返回值

对模块的引用。

## <a name="getobjectcount"></a>Module:: getobjectcount

检索此模块管理的对象数量。

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>返回值

此模块管理的当前对象数量。

## <a name="incrementobjectcount"></a>Module:: incrementobjectcount

递增模块所跟踪对象的数量。

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>返回值

递增操作之前的计数。

## <a name="module"></a>Module:: module

初始化 `Module` 类的新实例。

```cpp
Module();
```

### <a name="remarks"></a>备注

此构造函数受保护，不能使用 `new` 关键字进行调用。 请调用[module:: getmodule](#getmodule)或[module:: create](#create)。

## <a name="objectcount"></a>Module:: objectcount_

跟踪已使用创建多少个类的[使](../windows/make-function.md)函数。

```cpp
volatile long objectCount_;
```

## <a name="registercomobject"></a>Module:: registercomobject

注册一个或多个 COM 对象，以便其他应用程序可连接到它们。

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);

```

### <a name="parameters"></a>参数

*服务器名称*<br/>
服务器的完全限定名。

*clsid*<br/>
要注册的 CLSID 的数组。

*工厂*<br/>
其可用性正发布的类对象的 IUnknown 接口的数组。

*Cookie*<br/>
完成此操作后，指向标识已注册类对象的值的指针数组。 以后将使用这些值来撤销注册。

*count*<br/>
要注册的 CLSID 的数量。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示操作失败原因的 HRESULT（如 CO_E_OBJISREG）。

### <a name="remarks"></a>备注

COM 对象是使用 CLSCTX 枚举的 CLSCTX_LOCAL_SERVER 枚举器注册的。

当前的组合来指定连接到已注册的对象的类型*comflag*模板参数，并结合枚举的 REGCLS_SUSPENDED 枚举器。

## <a name="registerobjects"></a>Module:: registerobjects

注册 COM 或 Windows 运行时对象，以便其他应用程序可以连接到它们。

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>参数

*module*<br/>
COM 或 Windows 运行时对象的数组。

*服务器名称*<br/>
创建对象的服务器的名称。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示操作失败原因的 HRESULT。

## <a name="registerwinrtobject"></a>Module:: registerwinrtobject

注册一个或多个 Windows 运行时对象，以便其他应用程序可以连接到它们。

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>参数

*服务器名称*<br/>
指定受此操作影响的对象子集的名称。

*activatableClassIds*<br/>
要注册的可激活 CLSID 的数组。

*Cookie*<br/>
标识已注册类对象的值。 此值以后将用于撤销注册。

*count*<br/>
要注册的对象的数量。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示操作失败原因的 HRESULT（如 CO_E_OBJISREG）。

## <a name="releasenotifier"></a>Module:: releasenotifier_

包含一个指向`ReleaseNotifier`对象。

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="terminate"></a>Module:: terminate

导致关闭模块实例化的所有工厂。

```cpp
void Terminate();
```

### <a name="remarks"></a>备注

释放缓存中的工厂。

## <a name="unregistercomobject"></a>Module:: unregistercomobject

注销一个或多个 COM 对象，以阻止其他应用程序连接到它们。

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>参数

*服务器名称*<br/>
（未使用）

*Cookie*<br/>
指针的数组，其指向标识要注销的类对象的值。 该数组通过创建[RegisterCOMObject](#registercomobject)方法。

*count*<br/>
要注销的类的数量。

### <a name="return-value"></a>返回值

如果此操作成功，则为 S_OK；否则为指示此操作失败原因的错误 HRESULT。

## <a name="unregisterobjects"></a>Module:: unregisterobjects

取消指定模块中的对象，以便其他应用程序无法连接到它们。

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>参数

*module*<br/>
指向模块的指针。

*服务器名称*<br/>
指定受此操作影响的对象子集的限定名。

### <a name="return-value"></a>返回值

如果此操作成功，则为 S_OK；否则为指示此操作失败原因的错误 HRESULT。

## <a name="unregisterwinrtobject"></a>Module:: unregisterwinrtobject

注销一个或多个 Windows 运行时对象，以便其他应用程序无法连接到它们。

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>参数

*Cookie*<br/>
指针，其指向标识将撤销其注册的类对象的值。
