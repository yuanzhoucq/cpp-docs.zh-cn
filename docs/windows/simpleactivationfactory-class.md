---
title: SimpleActivationFactory 类 |Microsoft Docs
ms.custom: ''
ms.date: 09/07/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::SimpleActivationFactory class
- Microsoft::WRL::SimpleActivationFactory::ActivateInstance method
- Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::SimpleActivationFactory::GetTrustLevel method
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 07c37dbf1629461141d592eb1987ce071324e22c
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691466"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory 类

提供创建 Windows 运行时或经典 COM 基类的基础机制。

## <a name="syntax"></a>语法

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>参数

*基本*  
基类。

## <a name="remarks"></a>备注

类的基类必须提供默认构造函数。

下面的代码示例演示如何使用与 SimpleActivationFactory [ActivatableClassWithFactoryEx](../windows/activatableclass-macros.md)宏。

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance 方法](#activateinstance)|创建指定接口的实例。|
|[SimpleActivationFactory::GetRuntimeClassName 方法](#getruntimeclassname)|获取指定的类的实例的运行时类名称*Base*类模板参数。|
|[SimpleActivationFactory::GetTrustLevel 方法](#gettrustlevel)|获取指定的类的实例的信任级别*Base*类模板参数。|

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

**标头：** module.h

**命名空间：** Microsoft::WRL

## <a name="activateinstance"></a>Simpleactivationfactory:: Activateinstance 方法

创建指定接口的实例。

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>参数

*ppvObject*  
此操作完成后，指向由指定的对象的实例`Base`类模板参数。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

如果`__WRL_STRICT__`是定义，断言错误发出如果类模板参数中指定的基类不派生自[RuntimeClass](../windows/runtimeclass-class.md)，或者因配置不与 WinRt 或 WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举值。

## <a name="getruntimeclassname"></a>Simpleactivationfactory:: Getruntimeclassname 方法

获取指定的类的实例的运行时类名称`Base`类模板参数。

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>参数

*runtimeName*  
此操作完成后，运行时类名称。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

如果`__WRL_STRICT__`是定义，断言错误如果由指定的类发出`Base`类模板参数不派生自[RuntimeClass](../windows/runtimeclass-class.md)，或者因配置不与 WinRt 或 WinRtClassicComMix [RuntimeClassType](../windows/runtimeclasstype-enumeration.md)枚举值。

## <a name="gettrustlevel"></a>Simpleactivationfactory:: Gettrustlevel 方法

获取指定的类的实例的信任级别`Base`类模板参数。

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>参数

*trustLvl*  
此操作完成后，当前类对象的信任级别。

### <a name="return-value"></a>返回值

始终返回 S_OK。
