---
title: ClassFactory 类
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
- module/Microsoft::WRL::ClassFactory::AddRef
- module/Microsoft::WRL::ClassFactory::ClassFactory
- module/Microsoft::WRL::ClassFactory::LockServer
- module/Microsoft::WRL::ClassFactory::QueryInterface
- module/Microsoft::WRL::ClassFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ClassFactory class
- Microsoft::WRL::ClassFactory::AddRef method
- Microsoft::WRL::ClassFactory::ClassFactory, constructor
- Microsoft::WRL::ClassFactory::LockServer method
- Microsoft::WRL::ClassFactory::QueryInterface method
- Microsoft::WRL::ClassFactory::Release method
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
ms.openlocfilehash: bbf20e2269e6d62206e06e748174d7b88898cd68
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87198094"
---
# <a name="classfactory-class"></a>ClassFactory 类

实现 `IClassFactory` 接口的基本功能。

## <a name="syntax"></a>语法

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ClassFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IClassFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<ClassicCom | InhibitWeakReference>,
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

利用 `ClassFactory` 提供用户定义的工厂实现。

下面的编程模式演示如何使用[实现](implements-structure.md)结构在类工厂中指定三个以上的接口。

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

名称                                        | 描述
------------------------------------------- | -----------
[ClassFactory：： ClassFactory](#classfactory) |

### <a name="public-methods"></a>公共方法

“属性”                                            | 描述
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory：： AddRef](#addref)                 | 递增当前对象的引用计数 `ClassFactory` 。
[ClassFactory：： LockServer](#lockserver)         | 递增或递减由当前对象跟踪的基础对象的数量 `ClassFactory` 。
[ClassFactory：： QueryInterface](#queryinterface) | 检索指向参数指定的接口的指针。
[ClassFactory：： Release](#release)               | 递减当前对象的引用计数 `ClassFactory` 。

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

## <a name="requirements"></a>要求

**标头：** 模块。h

**命名空间：** Microsoft::WRL

## <a name="classfactoryaddref"></a><a name="addref"></a>ClassFactory：： AddRef

递增当前对象的引用计数 `ClassFactory` 。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。

## <a name="classfactoryclassfactory"></a><a name="classfactory"></a>ClassFactory：： ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="classfactorylockserver"></a><a name="lockserver"></a>ClassFactory：： LockServer

递增或递减由当前对象跟踪的基础对象的数量 `ClassFactory` 。

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>参数

*fLock*<br/>
**`true`** 递增跟踪的对象数。 **`false`** 减少跟踪的对象数。

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为 E_FAIL。

### <a name="remarks"></a>备注

`ClassFactory`跟踪[模块](module-class.md)类的基础实例中的对象。

## <a name="classfactoryqueryinterface"></a><a name="queryinterface"></a>ClassFactory：： QueryInterface

检索指向参数指定的接口的指针。

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

## <a name="classfactoryrelease"></a><a name="release"></a>ClassFactory：： Release

递减当前对象的引用计数 `ClassFactory` 。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>返回值

如果成功，则为 S_OK；否则为描述失败的 HRESULT。
