---
title: SimpleClassFactory 类
ms.date: 09/7/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
helpviewer_keywords:
- Microsoft::WRL::SimpleClassFactory class
- Microsoft::WRL::SimpleClassFactory::CreateInstance method
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
ms.openlocfilehash: 66794789e51a2635fae646cca49e4fae8385dfe0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211146"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory 类

提供创建基类的基本机制。

## <a name="syntax"></a>语法

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>参数

*基座*<br/>
基类。

## <a name="remarks"></a>备注

基类必须提供默认构造函数。

下面的代码示例演示如何将用于 `SimpleClassFactory` [ActivatableClassWithFactoryEx](activatableclass-macros.md)宏。

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|“属性”|描述|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance 方法](#createinstance)|创建指定接口的实例。|

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

`ClassFactory`

`SimpleClassFactory`

## <a name="requirements"></a>要求

**标头：** 模块。h

**命名空间：** Microsoft::WRL

## <a name="simpleclassfactorycreateinstance-method"></a><a name="createinstance"></a>SimpleClassFactory：： CreateInstance 方法

创建指定接口的实例。

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

#### <a name="parameters"></a>参数

*pUnkOuter*<br/>
必须为 **`nullptr`** ; 否则，返回值为 CLASS_E_NOAGGREGATION。

SimpleClassFactory 不支持聚合。 如果支持聚合，并且所创建的对象是聚合的一部分，则*pUnkOuter*将是指向聚合的控制接口的指针 `IUnknown` 。

*riid*<br/>
要创建的对象的接口 ID。

*ppvObject*<br/>
此操作完成后，指针指向由*riid*参数指定的对象的实例。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

如果 `__WRL_STRICT__` 定义了，则在类模板参数中指定的基类不是从[RuntimeClass](runtimeclass-class.md)派生的或未使用 ClassicCom 或 WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md)枚举值配置的情况下，将发出断言错误。
