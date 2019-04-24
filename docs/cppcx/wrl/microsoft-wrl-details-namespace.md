---
title: Microsoft::WRL::Details 命名空间
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: fce6e620600164e73d3708d98d8a7fa979e8ab42
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027465"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details 命名空间

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>成员

### <a name="classes"></a>类

|名称|描述|
|----------|-----------------|
|[ComPtrRef 类](comptrref-class.md)|表示类型 ComPtr 的对象的引用\<T >。|
|[ComPtrRefBase 类](comptrrefbase-class.md)|表示类的基类[ComPtrRef](comptrref-class.md)类。|
|[DontUseNewUseMake 类](dontusenewusemake-class.md)|阻止使用运算符`new`在`RuntimeClass`。 因此，必须使用[使函数成为](make-function.md)相反。|
|[EventTargetArray 类](eventtargetarray-class.md)|表示事件处理程序的数组。|
|[MakeAllocator 类](makeallocator-class.md)|可激活的类，带或不带弱引用支持，为分配内存。|
|[ModuleBase 类](modulebase-class.md)|表示类的基类[模块](module-class.md)类。|
|[RemoveIUnknown 类](removeiunknown-class.md)|创建类型的它等效于`IUnknown`-基于的类型，但具有非虚拟`QueryInterface`， `AddRef`，和`Release`方法。|
|[WeakReference 类](weakreference-class.md)|表示*弱引用*可以用于 Windows 运行时或经典 com。 弱引用表示可能可访问或可能不可访问的对象。|

### <a name="structures"></a>结构

|名称|描述|
|----------|-----------------|
|[ArgTraits 结构](argtraits-structure.md)|接口和具有指定的数目的参数的匿名成员函数声明指定的委托。|
|[ArgTraitsHelper 结构](argtraitshelper-structure.md)|可帮助定义委托参数的共同的特征。|
|[BoolStruct 结构](boolstruct-structure.md)|定义是否`ComPtr`管理接口的对象生存期。 `BoolStruct` 在内部使用[BoolType()](comptr-class.md#operator-microsoft-wrl-details-booltype)运算符。|
|[CreatorMap 结构](creatormap-structure.md)|包含有关如何初始化、 注册和注销的对象的信息。|
|[DerefHelper 结构](derefhelper-structure.md)|表示一个取消引用的指向`T*`模板参数。|
|[EnableIf 结构](enableif-structure.md)|如果第一个模板参数的计算结果为第二个模板参数指定的类型的数据成员定义`true`。|
|[FactoryCache 结构](factorycache-structure.md)|包含的类工厂和用于标识已注册的 Windows 运行时或 COM 类对象的值的位置。|
|[ImplementsBase 结构](implementsbase-structure.md)|用于验证中的模板参数类型[Implements 结构](implements-structure.md)。|
|[ImplementsHelper 结构](implementshelper-structure.md)|可帮助实现[实现](implements-structure.md)结构。|
|[InterfaceList 结构](interfacelist-structure.md)|用于创建接口的递归列表。|
|[InterfaceListHelper 结构](interfacelisthelper-structure.md)|生成`InterfaceList`通过以递归方式应用指定的模板参数自变量的类型。|
|[InterfaceTraits 结构](interfacetraits-structure.md)|实现的接口的共同特征。|
|[InvokeHelper 结构](invokehelper-structure.md)|提供的实现`Invoke()`方法基于指定的数目和参数的类型。|
|[IsBaseOfStrict 结构](isbaseofstrict-structure.md)|测试一种类型是否是另一种类型的基类。|
|[IsSame 结构](issame-structure.md)|一个指定类型等同于另一个测试指定的类型。|
|[Nil 结构](nil-structure.md)|用于指示未指定可选的模板参数。|
|[RemoveReference 结构](removereference-structure.md)|去除从指定的类模板参数引用或右值引用的特征。|
|[RuntimeClassBase 结构](runtimeclassbase-structure.md)|用于检测`RuntimeClass`中[使](make-function.md)函数。|
|[RuntimeClassBaseT 结构](runtimeclassbaset-structure.md)|提供的帮助器方法`QueryInterface`操作和入门的接口 Id。|
|[VerifyInheritanceHelper 结构](verifyinheritancehelper-structure.md)|测试是否有一个接口派生自另一个接口。|
|[VerifyInterfaceHelper 结构](verifyinterfacehelper-structure.md)|验证模板参数指定的接口满足某些要求。|

### <a name="enumerations"></a>枚举

|名称|描述|
|----------|-----------------|
|[AsyncStatusInternal 枚举](asyncstatusinternal-enumeration.md)|指定的状态的异步操作的内部枚举之间的映射和`Windows::Foundation::AsyncStatus`枚举。|

### <a name="functions"></a>函数

|名称|描述|
|----------|-----------------|
|[ActivationFactoryCallback 函数](activationfactorycallback-function.md)|获取激活工厂指定的激活 id。|
|[Move 函数](move-function.md)|将指定的参数从一个位置移动到另一个。|
|[RaiseException 函数](raiseexception-function.md)|引发调用线程中的异常。|
|[Swap 函数 (WRL)](swap-function-wrl.md)|交换两个指定参数的值。|
|[TerminateMap 函数](terminatemap-function.md)|关闭指定的模块中的类工厂。|

## <a name="requirements"></a>要求

**标头：** async.h、 client.h、 corewrappers.h、 event.h、 ftm.h、 implements.h、 internal.h、 module.h

**命名空间：** Microsoft::WRL::Details

## <a name="see-also"></a>请参阅

[Microsoft::WRL Namespace](microsoft-wrl-namespace.md)<br/>
[Microsoft::WRL::Wrappers 命名空间](microsoft-wrl-wrappers-namespace.md)