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
ms.openlocfilehash: 9a4c169944d56b693efa681bf7089636477012ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403071"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory 类

提供创建基类的基本机制。

## <a name="syntax"></a>语法

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>参数

*基本*<br/>
基类。

## <a name="remarks"></a>备注

类的基类必须提供默认构造函数。

下面的代码示例演示如何使用`SimpleClassFactory`与[ActivatableClassWithFactoryEx](activatableclass-macros.md)宏。

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
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

**标头：** module.h

**命名空间：** Microsoft:: wrl

## <a name="createinstance"></a>Simpleclassfactory:: Createinstance 方法

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
必须为`nullptr`; 否则为返回值是 CLASS_E_NOAGGREGATION。

SimpleClassFactory 不支持聚合。 如果受支持聚合，并且正在创建的对象是一个聚合的组成部分*pUnkOuter*是一个指向控制`IUnknown`聚合的接口。

*riid*<br/>
若要创建的对象 ID 的接口。

*ppvObject*<br/>
此操作完成后，指向由指定的对象的实例*riid*参数。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为指示错误的 HRESULT。

### <a name="remarks"></a>备注

如果`__WRL_STRICT__`是定义，断言错误发出如果类模板参数中指定的基类不派生自[RuntimeClass](runtimeclass-class.md)，或者因配置不与 ClassicCom 或 WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md)枚举值。
