---
title: Microsoft::WRL::Details 命名空间
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d71fe149-d804-4c6f-961d-43fe21ef8630
ms.openlocfilehash: 50208242d77d7b54951bcb44608f1a20b5147efc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223468"
---
# <a name="microsoftwrldetails-namespace"></a>Microsoft::WRL::Details 命名空间

支持 WRL 基础结构，不应在代码中直接使用。

## <a name="syntax"></a>语法

```cpp
namespace Microsoft::WRL::Details;
```

## <a name="members"></a>成员

### <a name="classes"></a>类

|“属性”|说明|
|----------|-----------------|
|[ComPtrRef 类](comptrref-class.md)|表示对 ComPtr 类型的对象的引用 \<T> 。|
|[ComPtrRefBase 类](comptrrefbase-class.md)|表示[ComPtrRef](comptrref-class.md)类的基类。|
|[DontUseNewUseMake 类](dontusenewusemake-class.md)|阻止 `new` 在中使用运算符 `RuntimeClass` 。 因此，你必须改为使用[Make 函数](make-function.md)。|
|[EventTargetArray 类](eventtargetarray-class.md)|表示事件处理程序的数组。|
|[MakeAllocator 类](makeallocator-class.md)|为可激活的类分配内存，但不支持弱引用。|
|[ModuleBase 类](modulebase-class.md)|表示[模块](module-class.md)类的基类。|
|[RemoveIUnknown 类](removeiunknown-class.md)|使类型等效于 `IUnknown` 基于的类型，但具有非虚拟 `QueryInterface` 的、 `AddRef` 和 `Release` 方法。|
|[WeakReference 类](weakreference-class.md)|表示可与 Windows 运行时或经典 COM 一起使用的*弱引用*。 弱引用表示可能可访问或可能不可访问的对象。|

### <a name="structures"></a>結構

|名称|说明|
|----------|-----------------|
|[ArgTraits 结构](argtraits-structure.md)|声明指定的委托接口和具有指定数量的参数的匿名成员函数。|
|[ArgTraitsHelper 结构](argtraitshelper-structure.md)|有助于定义委托参数的常见特性。|
|[BoolStruct 结构](boolstruct-structure.md)|定义是否 `ComPtr` 正在管理接口的对象生存期。 `BoolStruct`由[BoolType （）](comptr-class.md#operator-microsoft-wrl-details-booltype)运算符在内部使用。|
|[CreatorMap 结构](creatormap-structure.md)|介绍如何初始化、注册和撤消注册对象。|
|[DerefHelper 结构](derefhelper-structure.md)|表示指向模板参数的取消引用的指针 `T*` 。|
|[EnableIf 结构](enableif-structure.md)|如果第一个模板参数的计算结果为，则定义由第二个模板参数指定的类型的数据成员 **`true`** 。|
|[FactoryCache 结构](factorycache-structure.md)|包含类工厂的位置以及标识已注册的 Windows 运行时或 COM 类对象的值。|
|[ImplementsBase 结构](implementsbase-structure.md)|用于验证[实现结构](implements-structure.md)中的模板参数类型。|
|[ImplementsHelper 结构](implementshelper-structure.md)|帮助实现[实现](implements-structure.md)结构。|
|[InterfaceList 结构](interfacelist-structure.md)|用于创建接口的递归列表。|
|[InterfaceListHelper 结构](interfacelisthelper-structure.md)|`InterfaceList`通过递归应用指定的模板参数参数生成类型。|
|[InterfaceTraits 结构](interfacetraits-structure.md)|实现接口的常见特性。|
|[InvokeHelper 结构](invokehelper-structure.md)|`Invoke()`基于指定的参数数量和类型提供方法的实现。|
|[IsBaseOfStrict 结构](isbaseofstrict-structure.md)|测试一种类型是否是另一种类型的基类。|
|[IsSame 结构](issame-structure.md)|测试指定的类型是否与另一个指定的类型相同。|
|[Nil 结构](nil-structure.md)|用于指示未指定的可选模板参数。|
|[RemoveReference 结构](removereference-structure.md)|从指定的类模板参数中去除引用或右值引用特征。|
|[RuntimeClassBase 结构](runtimeclassbase-structure.md)|用于 `RuntimeClass` 在[Make](make-function.md)函数中检测。|
|[RuntimeClassBaseT 结构](runtimeclassbaset-structure.md)|为 `QueryInterface` 操作和获取接口 id 提供帮助器方法。|
|[VerifyInheritanceHelper 结构](verifyinheritancehelper-structure.md)|测试一个接口是否派生自另一个接口。|
|[VerifyInterfaceHelper 结构](verifyinterfacehelper-structure.md)|验证模板参数指定的接口是否满足某些要求。|

### <a name="enumerations"></a>枚举

|名称|说明|
|----------|-----------------|
|[AsyncStatusInternal 枚举](asyncstatusinternal-enumeration.md)|指定异步操作状态和枚举的内部枚举之间的映射 `Windows::Foundation::AsyncStatus` 。|

### <a name="functions"></a>函数

|名称|说明|
|----------|-----------------|
|[ActivationFactoryCallback 函数](activationfactorycallback-function.md)|获取指定激活 ID 的激活工厂。|
|[移动函数](move-function.md)|将指定的参数从一个位置移动到另一个位置。|
|[RaiseException 函数](raiseexception-function.md)|引发调用线程中的异常。|
|[Swap 函数（WRL）](swap-function-wrl.md)|交换两个指定参数的值。|
|[TerminateMap 函数](terminatemap-function.md)|关闭指定模块中的类工厂。|

## <a name="requirements"></a>要求

**标头：** async .h，corewrappers.h，internal.h，实现 .h，内 .h，模块. h，模块。h

**命名空间：** Microsoft：： WRL：:D etails

## <a name="see-also"></a>另请参阅

[Microsoft：： WRL 命名空间](microsoft-wrl-namespace.md)<br/>
[Microsoft：： WRL：：包装命名空间](microsoft-wrl-wrappers-namespace.md)
