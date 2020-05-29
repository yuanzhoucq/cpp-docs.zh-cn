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
ms.openlocfilehash: 924b9d2c30f11e6f0444d9c647807f1c86dcc411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373549"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory 类

提供创建基类的基本机制。

## <a name="syntax"></a>语法

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>参数

*基地*<br/>
基类。

## <a name="remarks"></a>备注

基类必须提供默认构造函数。

以下代码示例演示如何与`SimpleClassFactory`[可激活类与 FactoryEx](activatableclass-macros.md)宏一起使用。

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|说明|
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

**标题：** 模块.h

**命名空间：** Microsoft::WRL

## <a name="simpleclassfactorycreateinstance-method"></a><a name="createinstance"></a>简单类工厂：：创建实例方法

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
必须是`nullptr`;否则，返回值CLASS_E_NOAGGREGATION。

简单类工厂不支持聚合。 如果支持聚合，并且正在创建的对象是聚合的一部分，*则 pUnkOuter*将是指向聚合控制`IUnknown`接口的指针。

*riid*<br/>
要创建的对象的接口 ID。

*ppvObject*<br/>
此操作完成后，指针指向*riid*参数指定的对象的实例。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

如果`__WRL_STRICT__`已定义，如果类模板参数中指定的基类不是从[运行时类](runtimeclass-class.md)派生，或者未配置 ClassicCom 或 WinRtClassicComMix[运行时类型](runtimeclasstype-enumeration.md)枚举值，则将发出断言错误。
