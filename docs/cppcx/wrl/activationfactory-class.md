---
title: ActivationFactory 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::AddRef
- module/Microsoft::WRL::ActivationFactory::GetIids
- module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
- module/Microsoft::WRL::ActivationFactory::QueryInterface
- module/Microsoft::WRL::ActivationFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ActivationFactory class
- Microsoft::WRL::ActivationFactory::ActivationFactory, constructor
- Microsoft::WRL::ActivationFactory::AddRef method
- Microsoft::WRL::ActivationFactory::GetIids method
- Microsoft::WRL::ActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::ActivationFactory::GetTrustLevel method
- Microsoft::WRL::ActivationFactory::QueryInterface method
- Microsoft::WRL::ActivationFactory::Release method
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
ms.openlocfilehash: 0655caeb3f49a18e9c57c78f0008901aaaedda4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368710"
---
# <a name="activationfactory-class"></a>ActivationFactory 类

启用 Windows 运行时将激活的一个或多个类。

## <a name="syntax"></a>语法

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ActivationFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IActivationFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<WinRt | InhibitWeakReference>,
        false
    >;
```

### <a name="parameters"></a>参数

*I0*<br/>
第零个接口。

*I1*<br/>
第一个接口。

*I2*<br/>
第二个接口。

## <a name="remarks"></a>备注

`ActivationFactory`提供了接口的`IActivationFactory`注册方法和基本功能。 `ActivationFactory`还使您能够提供自定义工厂实现。

以下代码片段象征性地说明了如何使用激活工厂。

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../codesnippet/CPP/activationfactory-class_1.cpp)]

以下代码片段演示如何使用[实现](implements-structure.md)结构指定三个以上接口 ID。

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                                       | 说明
---------------------------------------------------------- | ------------------------------------------
[激活工厂：：激活工厂](#activationfactory) | 初始化 `ActivationFactory` 类。

### <a name="public-methods"></a>公共方法

名称                                                           | 说明
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[激活工厂：：添加参考](#addref)                           | 增加当前`ActivationFactory`对象的引用计数。
[激活工厂：：获取 Iid](#getiids)                         | 检索已实现接口 ID 的数组。
[激活工厂：：获取运行时类名称](#getruntimeclassname) | 获取当前`ActivationFactory`实例化对象的运行时类名称。
[激活工厂：获取信任级别](#gettrustlevel)             | 获取当前`ActivationFactory`实例化的对象的信任级别。
[激活工厂：：查询接口](#queryinterface)           | 检索指向指定接口的指针。
[激活工厂：：发布](#release)                         | 取消当前`ActivationFactory`对象的引用计数。

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

## <a name="requirements"></a>要求

**标题：** 模块.h

**命名空间：** Microsoft::WRL

## <a name="activationfactoryactivationfactory"></a><a name="activationfactory"></a>激活工厂：：激活工厂

初始化 `ActivationFactory` 类。

```cpp
ActivationFactory();
```

## <a name="activationfactoryaddref"></a><a name="addref"></a>激活工厂：：添加参考

增加当前`ActivationFactory`对象的引用计数。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。

## <a name="activationfactorygetiids"></a><a name="getiids"></a>激活工厂：：获取 Iid

检索已实现接口 ID 的数组。

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>参数

*iidCount*<br/>
此操作完成后 *，iids*数组中的 Interace ID 数。

*伊德*<br/>
此操作完成后，已实现接口 ID 的数组。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。 E_OUTOFMEMORY 是可能的失败 HRESULT。

## <a name="activationfactorygetruntimeclassname"></a><a name="getruntimeclassname"></a>激活工厂：：获取运行时类名称

获取当前`ActivationFactory`实例化对象的运行时类名称。

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>参数

*运行时名称*<br/>
此操作完成后，包含当前`ActivationFactory`实例化对象的运行时类名称的字符串的句柄。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。

## <a name="activationfactorygettrustlevel"></a><a name="gettrustlevel"></a>激活工厂：获取信任级别

获取当前`ActivationFactory`实例化的对象的信任级别。

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>参数

*信任吕尔*<br/>
此操作完成后，`ActivationFactory`实例化的运行时类的信任级别。

### <a name="return-value"></a>返回值

S_OK如果成功;否则，将发出断言错误，并将*信任 Lvl*设置为`FullTrust`。

## <a name="activationfactoryqueryinterface"></a><a name="queryinterface"></a>激活工厂：：查询接口

检索指向指定接口的指针。

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>参数

*riid*<br/>
接口 ID。

*ppvObject*<br/>
此操作完成后，指向参数*riid*指定的接口的指针。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。

## <a name="activationfactoryrelease"></a><a name="release"></a>激活工厂：：发布

取消当前`ActivationFactory`对象的引用计数。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。
