---
title: Module 类
ms.date: 10/18/2018
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
ms.openlocfilehash: afd2edacefdf5d62b50a03c0a8c37f13ee5d9c9f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371321"
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

*模块类型*<br/>
一个或多个[模块类型](moduletype-enumeration.md)枚举值的组合。

## <a name="members"></a>成员

### <a name="protected-classes"></a>受保护类

名称                                                                                | 说明
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[模块：：通用释放程序](module-genericreleasenotifier-class.md) | 在释放当前模块中的最后一个对象时调用事件处理程序。 事件处理程序由 lambda、functor 或 pointer-to-function 指定。
[模块：：方法释放器](module-methodreleasenotifier-class.md)   | 在释放当前模块中的最后一个对象时调用事件处理程序。 事件处理程序由对象及其指向方法的成员指定。
[模块：：释放器](module-releasenotifier-class.md)               | 在释放模块中的最后一个对象时调用事件处理程序。

### <a name="public-constructors"></a>公共构造函数

名称                             | 说明
-------------------------------- | -----------------------------------------------------------
[模块：：*模块](#tilde-module) | 取消初始化类的`Module`当前实例。

### <a name="protected-constructors"></a>受保护的构造函数

名称                      | 说明
------------------------- | ---------------------------------------------------
[模块：：模块](#module) | 初始化 `Module` 类的新实例。

### <a name="public-methods"></a>公共方法

名称                                                    | 说明
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[模块：：创建](#create)                               | 创建模块的实例。
[模块：:D对象计数](#decrementobjectcount)   | 递减模块所跟踪对象的数量。
[模块：：获取激活工厂](#getactivationfactory)   | 获取模块的激活工厂。
[模块：：获取类对象](#getclassobject)               | 检索类工厂的缓存。
[模块：：获取模块](#getmodule)                         | 创建模块的实例。
[模块：：获取对象计数](#getobjectcount)               | 检索此模块管理的对象数量。
[模块：：增量对象计数](#incrementobjectcount)   | 递增模块所跟踪对象的数量。
[模块：：注册COM对象](#registercomobject)         | 注册一个或多个 COM 对象，以便其他应用程序可连接到它们。
[模块：：注册对象](#registerobjects)             | 注册 COM 或 Windows 运行时对象，以便其他应用程序可以连接到它们。
[模块：：注册WinRT对象](#registerwinrtobject)     | 注册一个或多个 Windows 运行时对象，以便其他应用程序可以连接到它们。
[模块：：终止](#terminate)                         | 导致关闭模块实例化的所有工厂。
[模块：：未注册COM对象](#unregistercomobject)     | 注销一个或多个 COM 对象，以阻止其他应用程序连接到它们。
[模块：：取消注册对象](#unregisterobjects)         | 取消指定模块中的对象，以便其他应用程序无法连接到它们。
[模块：：未注册WinRT对象](#unregisterwinrtobject) | 取消注册一个或多个 Windows 运行时对象，以便其他应用程序无法连接到它们。

### <a name="protected-methods"></a>受保护的方法

名称                      | 说明
------------------------- | --------------------------------
[模块：：创建](#create) | 创建模块的实例。

### <a name="protected-data-members"></a>受保护的数据成员

名称                                         | 说明
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[模块：：objectCount_](#objectcount)         | 跟踪使用[Make](make-function.md)函数创建的类数。
[模块：：releaseNotifier_](#releasenotifier) | 保存指向`ReleaseNotifier`对象的指针。

### <a name="macros"></a>宏

名称                                                                   | 说明
---------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ActivatableClass](activatableclass-macros.md)              | 填充包含可以创建指定类实例的工厂的内部缓存。 此宏指定默认工厂和组 ID 参数。
[ActivatableClassWithFactory](activatableclass-macros.md)   | 填充包含可以创建指定类实例的工厂的内部缓存。 此宏使您能够指定特定的工厂参数。
[ActivatableClassWithFactoryEx](activatableclass-macros.md) | 填充包含可以创建指定类实例的工厂的内部缓存。 此宏使您能够指定特定的工厂和组 ID 参数。

## <a name="inheritance-hierarchy"></a>继承层次结构

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>要求

**标题：** 模块.h

**命名空间：** Microsoft::WRL

## <a name="modulemodule"></a><a name="tilde-module"></a>模块：：*模块

取消初始化类的`Module`当前实例。

```cpp
virtual ~Module();
```

## <a name="modulecreate"></a><a name="create"></a>模块：：创建

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

*回调 (callback)*<br/>
释放模块的最后一个实例对象时调用。

*对象*<br/>
*对象**和方法*参数是组合使用的。 释放模块中的最后一个实例对象时，指向最后一个实例对象。

*method*<br/>
*对象**和方法*参数是组合使用的。 在释放模块中的最后一个实例对象时，指向最后一个实例对象的方法。

### <a name="return-value"></a>返回值

参考模块。

## <a name="moduledecrementobjectcount"></a><a name="decrementobjectcount"></a>模块：:D对象计数

递减模块所跟踪对象的数量。

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>返回值

递减操作之前的计数。

## <a name="modulegetactivationfactory"></a><a name="getactivationfactory"></a>模块：：获取激活工厂

获取模块的激活工厂。

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>参数

*p 可激活类 Id*<br/>
运行时类的 IID。

*ppIFactory*<br/>
指定运行时类的 IActivationFactory。

*服务器名称*<br/>
当前模块中类工厂的子集名称。 指定[可激活类与FactoryEx](activatableclass-macros.md)宏中使用的服务器名称，或指定`nullptr`获取默认服务器名称。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为 GetActivationFactory 返回的 HRESULT。

## <a name="modulegetclassobject"></a><a name="getclassobject"></a>模块：：获取类对象

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

*Clsid*<br/>
类 ID。

*riid*<br/>
您请求的接口 ID。

*Ppv*<br/>
指向返回对象的指针。

*服务器名称*<br/>
在 `ActivatableClassWithFactory`、`ActivatableClassWithFactoryEx` 或 `ActivatableClass` 宏中指定的服务器名称；或用于获取默认服务器名称的 `nullptr`。

### <a name="return-value"></a>返回值

### <a name="remarks"></a>备注

此方法仅适用于 COM，而不是 Windows 运行时。 此方法仅`IClassFactory`公开方法。

## <a name="modulegetmodule"></a><a name="getmodule"></a>模块：：获取模块

创建模块的实例。

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>返回值

对模块的引用。

## <a name="modulegetobjectcount"></a><a name="getobjectcount"></a>模块：：获取对象计数

检索此模块管理的对象数量。

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>返回值

此模块管理的当前对象数量。

## <a name="moduleincrementobjectcount"></a><a name="incrementobjectcount"></a>模块：：增量对象计数

递增模块所跟踪对象的数量。

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>返回值

递增操作之前的计数。

## <a name="modulemodule"></a><a name="module"></a>模块：：模块

初始化 `Module` 类的新实例。

```cpp
Module();
```

### <a name="remarks"></a>备注

此构造函数受保护，不能使用 `new` 关键字进行调用。 相反，调用[模块：获取模块](#getmodule)或[模块：：创建](#create)。

## <a name="moduleobjectcount_"></a><a name="objectcount"></a>模块：：objectCount_

跟踪使用[Make](make-function.md)函数创建的类数。

```cpp
volatile long objectCount_;
```

## <a name="moduleregistercomobject"></a><a name="registercomobject"></a>模块：：注册COM对象

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

*克拉西德斯*<br/>
要注册的 CLSID 的数组。

*factories*<br/>
其可用性正发布的类对象的 IUnknown 接口的数组。

*饼干*<br/>
完成此操作后，指向标识已注册类对象的值的指针数组。 以后将使用这些值来撤销注册。

*count*<br/>
要注册的 CLSID 的数量。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示操作失败原因的 HRESULT（如 CO_E_OBJISREG）。

### <a name="remarks"></a>备注

COM 对象是使用 CLSCTX 枚举的 CLSCTX_LOCAL_SERVER 枚举器注册的。

与已注册对象的连接类型由当前*标志*模板参数和 REGCLS 枚举的REGCLS_SUSPENDED枚举器的组合指定。

## <a name="moduleregisterobjects"></a><a name="registerobjects"></a>模块：：注册对象

注册 COM 或 Windows 运行时对象，以便其他应用程序可以连接到它们。

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>参数

*模块*<br/>
COM 或 Windows 运行时对象的数组。

*服务器名称*<br/>
创建对象的服务器的名称。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示操作失败原因的 HRESULT。

## <a name="moduleregisterwinrtobject"></a><a name="registerwinrtobject"></a>模块：：注册WinRT对象

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

*可激活类标识*<br/>
要注册的可激活 CLSID 的数组。

*饼干*<br/>
标识已注册类对象的值。 此值以后将用于撤销注册。

*count*<br/>
要注册的对象的数量。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示操作失败原因的 HRESULT（如 CO_E_OBJISREG）。

## <a name="modulereleasenotifier_"></a><a name="releasenotifier"></a>模块：：releaseNotifier_

保存指向`ReleaseNotifier`对象的指针。

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="moduleterminate"></a><a name="terminate"></a>模块：：终止

导致关闭模块实例化的所有工厂。

```cpp
void Terminate();
```

### <a name="remarks"></a>备注

释放缓存中的工厂。

## <a name="moduleunregistercomobject"></a><a name="unregistercomobject"></a>模块：：未注册COM对象

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

*饼干*<br/>
指针的数组，其指向标识要注销的类对象的值。 数组由[注册COMObject](#registercomobject)方法创建。

*count*<br/>
要注销的类的数量。

### <a name="return-value"></a>返回值

如果此操作成功，则为 S_OK；否则为指示此操作失败原因的错误 HRESULT。

## <a name="moduleunregisterobjects"></a><a name="unregisterobjects"></a>模块：：取消注册对象

取消指定模块中的对象，以便其他应用程序无法连接到它们。

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>参数

*模块*<br/>
指向模块的指针。

*服务器名称*<br/>
指定受此操作影响的对象子集的限定名。

### <a name="return-value"></a>返回值

如果此操作成功，则为 S_OK；否则为指示此操作失败原因的错误 HRESULT。

## <a name="moduleunregisterwinrtobject"></a><a name="unregisterwinrtobject"></a>模块：：未注册WinRT对象

取消注册一个或多个 Windows 运行时对象，以便其他应用程序无法连接到它们。

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>参数

*饼干*<br/>
指针，其指向标识将撤销其注册的类对象的值。
