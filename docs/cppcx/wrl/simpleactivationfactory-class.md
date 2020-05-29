---
title: SimpleActivationFactory 类
ms.date: 09/07/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
helpviewer_keywords:
- Microsoft::WRL::SimpleActivationFactory class
- Microsoft::WRL::SimpleActivationFactory::ActivateInstance method
- Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::SimpleActivationFactory::GetTrustLevel method
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
ms.openlocfilehash: 39e539c63e91b508f51656114ee8fbd68150991f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370941"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory 类

提供创建 Windows 运行时或经典 COM 基类的基础机制。

## <a name="syntax"></a>语法

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>参数

*基地*<br/>
基类。

## <a name="remarks"></a>备注

基类必须提供默认构造函数。

以下代码示例演示如何将简单激活工厂与[可激活的类与 FactoryEx](activatableclass-macros.md)宏一起使用。

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance 方法](#activateinstance)|创建指定接口的实例。|
|[SimpleActivationFactory::GetRuntimeClassName 方法](#getruntimeclassname)|获取*Base*类模板参数指定的类实例的运行时类名称。|
|[SimpleActivationFactory::GetTrustLevel 方法](#gettrustlevel)|获取*Base*类模板参数指定的类实例的信任级别。|

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

`SimpleActivationFactory`

## <a name="requirements"></a>要求

**标题：** 模块.h

**命名空间：** Microsoft::WRL

## <a name="simpleactivationfactoryactivateinstance-method"></a><a name="activateinstance"></a>简单激活工厂：：激活实例方法

创建指定接口的实例。

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>参数

*ppvObject*<br/>
此操作完成后，将指针指向`Base`类模板参数指定的对象的实例。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

如果`__WRL_STRICT__`已定义，如果类模板参数中指定的基类不是从[RuntimeClass](runtimeclass-class.md)派生，或者未配置 WinRt 或 WinRtClassicComMix[运行时类型](runtimeclasstype-enumeration.md)枚举值，则将发出断言错误。

## <a name="simpleactivationfactorygetruntimeclassname-method"></a><a name="getruntimeclassname"></a>简单激活工厂：：获取运行时类名称方法

获取`Base`类模板参数指定的类实例的运行时类名称。

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>参数

*运行时名称*<br/>
此操作完成后，运行时类名称。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

如果`__WRL_STRICT__`已定义，如果`Base`类模板参数指定的类不是从[RuntimeClass](runtimeclass-class.md)派生，或者未配置 WinRt 或 WinRtClassicComMix[运行时类型](runtimeclasstype-enumeration.md)枚举值，则将发出断言错误。

## <a name="simpleactivationfactorygettrustlevel-method"></a><a name="gettrustlevel"></a>简单激活工厂：：获取信任级别方法

获取`Base`类模板参数指定的类实例的信任级别。

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>参数

*信任吕尔*<br/>
此操作完成后，当前类对象的信任级别。

### <a name="return-value"></a>返回值

始终 S_OK。
