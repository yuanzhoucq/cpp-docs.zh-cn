---
title: Microsoft::WRL 命名空间
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL
- module/Microsoft::WRL
- async/Microsoft::WRL
- internal/Microsoft::WRL
- event/Microsoft::WRL
- ftm/Microsoft::WRL
- client/Microsoft::WRL
- corewrappers/Microsoft::WRL
helpviewer_keywords:
- WRL namespace
ms.assetid: 01118a8f-f564-4859-b87e-9444848585a1
ms.openlocfilehash: 749469c7ae2acf3a0da92d24a51bbfca9b68971d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033516"
---
# <a name="microsoftwrl-namespace"></a>Microsoft::WRL 命名空间

定义构成了 Windows 运行时的基础类型C++模板库。

## <a name="syntax"></a>语法

```cpp
namespace Microsoft::WRL;
```

## <a name="members"></a>成员

### <a name="typedefs"></a>Typedef

|名称|描述|
|----------|-----------------|
|`InhibitWeakReferencePolicy`|`RuntimeClassFlags<WinRt | InhibitWeakReference>`|

### <a name="classes"></a>类

|名称|描述|
|----------|-----------------|
|[ActivationFactory 类](activationfactory-class.md)|启用 Windows 运行时将激活的一个或多个类。|
|[AsyncBase 类](asyncbase-class.md)|实现 Windows 运行时异步状态机。|
|[ClassFactory 类](classfactory-class.md)|实现 `IClassFactory` 接口的基本功能。|
|[ComPtr 类](comptr-class.md)|创建表示模板参数指定的接口的 *智能指针* 类型。 ComPtr 会自动维护基础接口指针的引用计数，并在引用计数变为零时释放接口。|
|[DeferrableEventArgs 类](deferrableeventargs-class.md)|一种用于延迟事件的事件参数类型的模板类。|
|[EventSource 类](eventsource-class.md)|表示一个事件。 `EventSource` 成员函数将添加、删除和调用事件处理程序。|
|[FtmBase 类](ftmbase-class.md)|表示自由线程封送拆收器对象。|
|[Module 类](module-class.md)|表示相关对象的集合。|
|[RuntimeClass 类](runtimeclass-class.md)|表示继承指定数量的接口的实例化类，并提供指定 Windows 运行时、经典 COM 和弱引用支持。|
|[SimpleActivationFactory 类](simpleactivationfactory-class.md)|提供创建 Windows 运行时或经典 COM 基类的基础机制。|
|[SimpleClassFactory 类](simpleclassfactory-class.md)|提供创建基类的基本机制。|
|[WeakRef 类](weakref-class.md)|表示只能由 Windows 运行时而不是经典 COM 使用的 *弱引用* 。 弱引用表示可能可访问或可能不可访问的对象。|

### <a name="structures"></a>结构

|名称|描述|
|----------|-----------------|
|[ChainInterfaces 结构](chaininterfaces-structure.md)|指定可应用于一组接口 ID 的验证和初始化函数。|
|[CloakedIid 结构](cloakediid-structure.md)|指示对`RuntimeClass`，`Implements`和`ChainInterfaces`： 指定的接口是无法访问 IID 列表中的模板。|
|[Implements 结构](implements-structure.md)|实现`QueryInterface`和`GetIid`指定接口。|
|[MixIn 结构](mixin-structure.md)|确保运行时类先后派生自 Windows 运行时接口（如果有）和经典 COM 接口。|
|[RuntimeClassFlags 结构](runtimeclassflags-structure.md)|包含的类型的实例[RuntimeClass](runtimeclass-class.md)。|

### <a name="enumerations"></a>枚举

|名称|描述|
|----------|-----------------|
|[AsyncResultType 枚举](asyncresulttype-enumeration.md)|指定返回的结果类型`GetResults()`方法。|
|[ModuleType 枚举](moduletype-enumeration.md)|指定模块是否应支持进程内服务器或进程外服务器。|
|[RuntimeClassType 枚举](runtimeclasstype-enumeration.md)|指定的类型[RuntimeClass](runtimeclass-class.md)支持实例。|

### <a name="functions"></a>函数

|名称|描述|
|----------|-----------------|
|[AsWeak 函数](asweak-function.md)|检索对指定实例的弱引用。|
|[回调函数 (WRL)](callback-function-wrl.md)|创建一个对象，该对象的成员函数是一个回调方法。|
|[CreateActivationFactory 函数](createactivationfactory-function.md)|创建为可由 Windows 运行时激活的指定类生成实例的工厂。|
|[CreateClassFactory 函数](createclassfactory-function.md)|创建为指定类生成实例的工厂。|
|[Make 函数](make-function.md)|初始化指定的 Windows 运行时类。|

## <a name="requirements"></a>要求

**标头：** async.h、 client.h、 corewrappers.h、 event.h、 ftm.h、 implements.h、 internal.h、 module.h

**命名空间：** Microsoft:: wrl

## <a name="see-also"></a>请参阅

[Microsoft::WRL::Wrappers 命名空间](microsoft-wrl-wrappers-namespace.md)